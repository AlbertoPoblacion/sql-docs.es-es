---
title: Alta disponibilidad para los contenedores de SQL Server
description: Este artículo presentan alta disponibilidad para los contenedores de SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: da4c702e8ec5e8c1d645af616df53edd287eae5a
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833924"
---
# <a name="high-availability-for-sql-server-containers"></a>Alta disponibilidad para los contenedores de SQL Server

Crear y administrar las instancias de SQL Server de forma nativa en Kubernetes.

Implementar SQL Server para contenedores de docker administrados por [Kubernetes](https://kubernetes.io/). En Kubernetes, un contenedor con una instancia de SQL Server puede recuperarse automáticamente en caso de que se produce un error en un nodo de clúster. Para lograr una disponibilidad más robusta, configure SQL Server AlwaysOn en el grupo de disponibilidad con instancias de SQL Server en contenedores en un clúster de Kubernetes. Este artículo comparan las dos soluciones.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Comparar versiones de SQL Server en Kubernetes

SQL Server 2017 proporciona una imagen de Docker que puede implementar en Kubernetes. Puede configurar la imagen con una notificación de volumen persistente (PVC) de Kubernetes. Kubernetes supervisa el proceso de SQL Server en el contenedor. Si se producirá un error en el proceso, pod, contenedor o nodo, Kubernetes arranca otra instancia automáticamente y se vuelve a conectar al almacenamiento.

SQL Server 2019 (versión preliminar) presenta una arquitectura más sólida con Kubernetes StatefulSet. Kubernetes orquesta las instancias de SQL Server como imágenes de contenedor que participan en un SQL Server grupo de disponibilidad AlwaysOn. Este patrón proporciona supervisión de estado mejorada, una recuperación más rápida, descarga de copia de seguridad y escalado horizontal de lectura.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Contenedor con la instancia de SQL Server en Kubernetes

Kubernetes 1.6 y versiones posteriores es compatible con [ *clases de almacenamiento*](https://kubernetes.io/docs/concepts/storage/storage-classes/), [ *notificaciones de volumen persistente*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)y el [  *Tipo de volumen de disco de Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

En esta configuración, Kubernetes desempeña la función de orquestador del contenedor. 

![Diagrama del clúster de Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

En el diagrama anterior, `mssql-server` es una instancia de SQL Server (contenedor) en un [ *pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Un [conjunto de réplicas](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) garantiza que el pod se recupera automáticamente después de un error de nodo. Las aplicaciones se conectan al servicio. En este caso, el servicio representa un equilibrador de carga que hospeda una dirección IP que permanece igual después de un error de la `mssql-server`.

Kubernetes orquesta los recursos del clúster. Cuando se produce un error en un nodo de hospedaje de un contenedor de la instancia de SQL Server, se arranca un nuevo contenedor con una instancia de SQL Server y lo asocia al mismo almacenamiento persistente.

SQL Server 2017 y versiones posteriores admite contenedores en Kubernetes.

Para crear un contenedor en Kubernetes, consulte [implementar un contenedor de SQL Server en Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Un grupo de disponibilidad SQL Server Always On en los contenedores de SQL Server en Kubernetes

SQL Server 2019 admite grupos de disponibilidad en los contenedores de un Kubernetes. Para los grupos de disponibilidad, implemente el servidor SQL Server [Kubernetes operador](https://coreos.com/blog/introducing-operators.html) al clúster de Kubernetes. El operador ayuda a paquete, implementar y administrar instancias de SQL Server y el grupo de disponibilidad en un clúster.

![Grupo de disponibilidad en el contenedor de Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

En la imagen anterior, un clúster de cuatro nodos kubernetes aloja un grupo de disponibilidad con tres réplicas. La solución incluye los siguientes componentes:

* Un Kubernetes [ *implementación*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). La implementación incluye el operador y un mapa de la configuración. La implementación describe la imagen de contenedor, software y las instrucciones necesarias para implementar instancias de SQL Server para el grupo de disponibilidad.

* Tres nodos, cada hospeda un [ *StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). El StatefulSet contiene un pod. Cada pod contiene:
  * Un contenedor de SQL Server ejecuta una instancia de SQL Server.
  * Un supervisor `mcr.microsoft.com/mssql/ha` para administrar el grupo de disponibilidad.

* Dos [ *ConfigMaps* ](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) relacionadas con el grupo de disponibilidad. El ConfigMaps proporcionan información acerca de:
  * La implementación del operador.
  * Grupo de disponibilidad.

 * Volúmenes persistentes de cada instancia de SQL Server proporcionan el almacenamiento para los archivos de registro y datos.

Además, el clúster almacena [ *secretos* ](https://kubernetes.io/docs/concepts/configuration/secret/) para las contraseñas, certificados, claves y otra información confidencial.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Comparar la alta disponibilidad de SQL Server en contenedores con y sin el grupo de disponibilidad

En la tabla siguiente compara la funcionalidad de alta disponibilidad de SQL Server en contenedores en Kubernetes con y sin un grupo de disponibilidad:

| |Con un grupo de disponibilidad | Instancia independiente del contenedor<br/> No hay ningún grupo de disponibilidad
|:------|:------|:------
|Recuperarse automáticamente de error de nodo | Sí | Sí
|Recuperarse automáticamente de error de pod | Sí | Sí
|Rápida conmutación por error |Sí |
|Recuperarse automáticamente de error de la instancia de SQL Server | Sí | 
|Recuperarse automáticamente de error de comprobación de mantenimiento de base de datos | Sí | 
|Proporcionar las réplicas de solo lectura | Sí |
|Copia de seguridad de réplica secundaria | Sí | 
|Se ejecuta como un StatefulSet | Sí | 

Una diferencia clave es que el tiempo de recuperación (o conmutación por error) es más rápido con un grupo de disponibilidad que con una sola instancia de SQL Server en un contenedor. Esta mejora es porque el grupo de disponibilidad de SQL Server mantiene réplicas secundarias en otros nodos del clúster. En la conmutación por error, una réplica secundaria está seleccionada y promueve a principal. Las aplicaciones conectadas para el servicio se le redirigirá a la nueva réplica principal.

Sin el grupo de disponibilidad cuando Kubernetes detecta una conmutación por error, debe crear el contenedor, conéctelo al almacenamiento y, a continuación, se vuelven a conectar las aplicaciones conectadas al servicio. El tiempo de conmutación por error exacto depende de que era la conmutación por error, y cómo se detectó. 

Por lo general, el tiempo de conmutación por error para un grupo de disponibilidad se mide en segundos, mientras que el tiempo de conmutación por error para una instancia única recuperar un contenedor puede ser de hasta 10 minutos.

## <a name="next-steps"></a>Pasos siguientes

Para implementar contenedores en Azure Kubernetes Service (AKS) de SQL Server, vea estos ejemplos:

* [Implementar SQL Server en el contenedor de Docker](sql-server-linux-configure-docker.md)
* [Implementar un contenedor de SQL Server en Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Grupos de disponibilidad de Always On para los contenedores de SQL Server](sql-server-ag-kubernetes.md)

