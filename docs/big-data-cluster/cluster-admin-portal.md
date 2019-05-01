---
title: Portal de administración de clústeres
titleSuffix: SQL Server big data clusters
description: Obtenga información sobre cómo usar el portal de administración de clúster para supervisar clústeres de macrodatos de 2019 de SQL Server (versión preliminar).
author: yualan
ms.author: alayu
ms.reviewer: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 3e0f3c939f4d20e65262453e23ac127b02c6d212
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63472138"
---
# <a name="how-to-use-the-cluster-administration-portal-to-monitor-a-sql-server-big-data-cluster"></a>Cómo usar el portal de administración de clúster para supervisar un clúster de macrodatos de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Si desea supervisar o solucionar problemas de su clúster de macrodatos de 2019 de SQL Server (versión preliminar), use el portal de administración de clúster.

El portal de administración de clúster le permite:
- Ver rápidamente el número de pods ejecutando y los problemas
- Supervisar el estado de implementación
- Ver extremos de servicio de disponibilidad
- Controlador de vista y la instancia principal de SQL Server
- Explorar en profundidad la información sobre pods, incluido el acceso a registros de Kibana y paneles de Grafana

## <a name="access-the-cluster-administration-portal"></a>Obtener acceso al portal de administración de clúster

Siga el [inicio rápido para implementar el clúster de macrodatos](quickstart-big-data-cluster-deploy.md) hasta llegar a la **portal de administración de clúster** sección. Una vez que el clúster de macrodatos que se está ejecutando con mssqlctl, siga estas instrucciones:

Una vez que se está ejecutando el pod del controlador, puede usar el portal de administración de clúster para supervisar la implementación. Se puede acceder al portal mediante el número de puerto y dirección IP externo para la `mgmtproxy-svc-external` (por ejemplo: **https://\<ip-address\>: 30777/portal**). Las credenciales de acceso al portal de administración es los valores de `CONTROLLER_USERNAME` y `CONTROLLER_PASSWORD` variables de entorno proporcionadas anteriormente.

> [!NOTE]
> Para CTP 2.5, hay una advertencia de seguridad al obtener acceso a la página web, dado que usa certificados SSL generados automáticamente.

## <a name="overview"></a>Información general

![Información general](./media/cluster-admin-portal/portal-overview.png)

Cuando se escribe por primera vez el portal, puede ver rápidamente el número de pods que se ejecuta en:
- Controlador
- Instancia de master
- Grupo de proceso
- Grupo de almacenamiento
- Grupo de datos

Si hay algún problema, puede abrir un vínculo a problemas conocidos. Puede usar el panel de navegación izquierdo para ir al grupo específico, si hay un problema.

## <a name="deployment"></a>Implementación

![implementación](./media/cluster-admin-portal/portal-deployment.png)

Para supervisar la implementación, haga clic en la pestaña de la implementación de la izquierda. Puede ver una vista de árbol de la implementación, y si hay algún problema en la implementación.

## <a name="service-endpoints"></a>Puntos de conexión de servicio

![extremos](./media/cluster-admin-portal/portal-endpoints.png)

Puede ver los puntos de conexión de servicio disponibles, haga clic en la pestaña puntos de conexión en el panel de navegación izquierdo.

Esto incluye vínculos a punto de conexión de Spark, panel de Grafana, y los registros de Kibana.

## <a name="controller"></a>Controlador

![Controlador](./media/cluster-admin-portal/portal-controller.png)

El controlador muestra todos los Pods están relacionados con el controlador. Puede aprender más acerca del controlador [aquí.](concept-controller.md)

Para obtener más información adicional sobre cada pod, puede hacer clic en **métricas** columna para ver los paneles de Grafana.

Para obtener información acerca de los registros para los pods con problemas, puede hacer clic en el **registros** columna.

## <a name="master-instance"></a>Instancia de master

![extremos](./media/cluster-admin-portal/portal-master.png)

La instancia maestra se muestran todos los Pods están relacionadas con la instancia principal de SQL Server. Puede aprender más acerca de la instancia principal de SQL Server [aquí.](concept-master-instance.md)

Para obtener más información adicional sobre cada pod, puede hacer clic en **métricas** columna para ver los paneles de Grafana.

Para obtener información acerca de los registros para los pods con problemas, puede hacer clic en el **registros** columna.

## <a name="pool-and-pod-pages"></a>Grupo de servidores y las páginas de Pod

![Grupo de servidores](./media/cluster-admin-portal/portal-data-pool.png)

En cada página del grupo (proceso, almacenamiento y datos), puede explorar en profundidad cada una de las páginas de pod haciendo clic en **predeterminado**

![pod](./media/cluster-admin-portal/portal-data-default-pool.png)

Esto muestra una ruta de navegación en la parte superior de la ruta de acceso en profundidad.

Para obtener más información adicional sobre cada pod, puede hacer clic en **métricas** columna para ver los paneles de Grafana.

Para obtener información acerca de los registros para los pods con problemas, puede hacer clic en el **registros** columna.

Para obtener más información sobre cada grupo:
- [grupo de proceso](concept-compute-pool.md)
- [grupo de almacenamiento](concept-storage-pool.md)
- [grupo de datos](concept-data-pool.md)

## <a name="about-page"></a>Acerca de la página

![acerca de](./media/cluster-admin-portal/portal-about.png)

Aquí puede ver información sobre el clúster, como los números de versión diferentes, contenedores y un vínculo a la documentación.

## <a name="next-steps"></a>Pasos siguientes

Además el portal de administración de clúster, también puede ejecutar varios comandos útiles de Kubernetes para explorar el estado y el estado del clúster. Para obtener más información, consulte [comandos Kubectl para la supervisión y solución de problemas de clústeres de SQL Server macrodatos](cluster-troubleshooting-commands.md).

Para más información acerca de los clústeres de macrodatos de 2019 de SQL Server, consulte [¿cuáles son los clústeres de SQL Server 2019 macrodatos?](big-data-cluster-overview.md).
