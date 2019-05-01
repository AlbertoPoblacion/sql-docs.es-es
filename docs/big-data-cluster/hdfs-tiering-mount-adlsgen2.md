---
title: Montaje de ADLS Gen2 para los niveles de HDFS
titleSuffix: How to mount ADLS Gen2
description: Este artículo explica cómo configurar HDFS niveles para montar un sistema de archivos externo de Azure Data Lake Storage en HDFS en un clúster de macrodatos de 2019 de SQL Server (versión preliminar).
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 04/18/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9d9e01e31f0f9e68c5b41b92da773dca8aab54c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63317134"
---
# <a name="how-to-mount-adls-gen2-for-hdfs-tiering-in-a-big-data-cluster"></a>Cómo Gen2 de ADLS de montaje para los niveles en un clúster de macrodatos HDFS

Las secciones siguientes proporcionan un ejemplo de cómo configurar la organización en niveles con un origen de datos de Azure Data Lake Storage Gen2 HDFS.

## <a name="prerequisites"></a>Requisitos previos

- [Clúster de macrodatos implementada](deployment-guidance.md)
- [Herramientas de datos de gran tamaño](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a id="load"></a> Cargar datos en Azure Data Lake Storage

La siguiente sección describe cómo configurar Azure Data Lake almacenamiento Gen2 para probar los niveles de HDFS. Si ya tiene datos almacenados en Azure Data Lake Storage, puede omitir esta sección para usar sus propios datos.

1. [Crear una cuenta de almacenamiento con las funcionalidades de Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. [Crear un contenedor de blobs](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-portal) en esta cuenta de almacenamiento para los datos externos.

1. Cargue un archivo CSV o Parquet en el contenedor. Se trata de los datos HDFS externos que se montará en HDFS en el clúster de macrodatos.

## <a name="credentials-for-mounting"></a>Credenciales para el montaje

## <a name="use-oauth-credentials-to-mount"></a>Use las credenciales de OAuth para montar

Para poder usar las credenciales de OAuth para montar, deberá seguir los pasos siguientes:

1. Vaya a la [portal de Azure](https://portal.azure.com)
1. Vaya a "services" en el panel de navegación izquierdo y de reloj en "Azure Active Directory"
1. Con "Registros de aplicaciones" en el menú, cree una "aplicación Web y siga el asistente. **Recuerde el nombre que se creen aquí**. Deberá agregar este nombre a la cuenta ADLS como un usuario autorizado.
1. Una vez creada la aplicación web, vaya a "claves" en "configuración" de la aplicación.
1. Seleccione que una duración de la clave y haga clic en guardan. **Guarde la clave generada.**
1.  Vuelva a la página de registros de aplicaciones y haga clic en el botón "Puntos de conexión" en la parte superior. **Anote la dirección URL de "Extremo de Token"**
1. Ahora debería tener lo siguiente que anotó para OAuth:

    - El "identificador de aplicación" de la aplicación Web que creó anteriormente en el paso 3
    - La clave que acaba de generar en el paso 5
    - El extremo de token del paso 6

### <a name="adding-the-service-principal-to-your-adls-account"></a>Agregar a la entidad de servicio a su cuenta de ADLS

1. Ir al portal nuevo y abra su cuenta de ADLS y seleccione el control de acceso (IAM) en el menú izquierdo.
1. Seleccione "Agregar una asignación de roles" y busque el nombre que creó en el paso 3 anterior (tenga en cuenta que no se muestra en la lista, pero se encontrarán si busca el nombre completo).
1. Ahora agregue el rol "Colaborador de datos de la Blob Storage (versión preliminar)".

Espere entre 5 y 10 minutos antes de usar las credenciales para el montaje

### <a name="create-credential-file"></a>Crear archivo de credenciales

Abra un símbolo en un equipo cliente que puede tener acceso al clúster de macrodatos.

Cree un archivo local denominado **filename.creds** que contiene sus credenciales de cuenta de Azure Data Lake Storage Gen2 con el formato siguiente:

   ```text
    fs.azure.account.auth.type=OAuth
    fs.azure.account.oauth.provider.type=org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider
    fs.azure.account.oauth2.client.endpoint=[token endpoint from step6 above]
    fs.azure.account.oauth2.client.id=[<Application ID> from step3 above]
    fs.azure.account.oauth2.client.secret=[<key> from step5 above]
   ```

## <a name="use-access-keys-to-mount"></a>Use las teclas de acceso para montar

También puede montar mediante claves de acceso que se pueden obtener con su cuenta ADLS en el portal de Azure.

 > [!TIP]
   > Para obtener más información sobre cómo buscar la clave de acceso (`<storage-account-access-key>`) para la cuenta de almacenamiento, consulte [ver y copiar las claves de acceso](https://docs.microsoft.com/azure/storage/common/storage-account-manage?#view-and-copy-access-keys).

### <a name="create-credential-file"></a>Crear archivo de credenciales

1. Abra un símbolo en un equipo cliente que puede tener acceso al clúster de macrodatos.

1. Cree un archivo local denominado **filename.creds** que contiene sus credenciales de cuenta de Azure Data Lake Storage Gen2 con el formato siguiente:

   ```text
   fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net
   fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>
   ```

## <a id="mount"></a> Montar el almacenamiento HDFS remoto

Ahora que ha preparado un archivo de credenciales con las claves de acceso o uso de OAuth, puede iniciar el montaje. Los pasos siguientes montar el almacenamiento HDFS remoto en Azure Data Lake en el almacenamiento HDFS local de su clúster de macrodatos.

1. Use **kubectl** para buscar la dirección IP para el punto de conexión **mgmtproxy-svc-external** servicio en el clúster de macrodatos. Busque el **External-IP**.

   ```bash
   kubectl get svc mgmtproxy-svc-external -n <your-cluster-name>
   ```

1. Inicie sesión con **mssqlctl** utilizando la dirección IP externa del punto de conexión de proxy de administración con el nombre de usuario del clúster y la contraseña:

   ```bash
   mssqlctl login -e https://<IP-of-mgmtproxy-svc-external>:30777/ -u <username> -p <password>
   ```

1. Montar el almacenamiento HDFS remoto en Azure mediante **crear montaje del almacenamiento mssqlctl**. Reemplace los valores de marcador de posición antes de ejecutar el comando siguiente:

   ```bash
   mssqlctl storage mount create --remote-uri abfs://<blob-container-name>@<storage-account-name>.dfs.core.windows.net/ --mount-path /mounts/<mount-name> --credential-file <path-to-adls-credentials>/file.creds
   ```

   > [!NOTE]
   > El montaje crear comando es asincrónica. En este momento, no hay ningún mensaje que indica si el montaje se realizó correctamente. Consulte la [estado](#status) sección para comprobar el estado de sus montajes.

Si ha montado correctamente, podrá consultar los datos HDFS y ejecutar trabajos de Spark en él. Aparecerá en el HDFS del clúster de macrodatos en la ubicación especificada por `--mount-path`.

## <a id="status"></a> Obtener el estado de montajes

Para mostrar el estado de todos los montajes en el clúster de macrodatos, utilice el siguiente comando:

```bash
mssqlctl storage mount status
```

Para mostrar el estado de un montaje en una ruta específica en HDFS, use el siguiente comando:

```bash
mssqlctl storage mount status --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Eliminar el montaje

Para eliminar el montaje, use el **mssqlctl almacenamiento montaje delete** comando y especifique la ruta de acceso de montaje en HDFS:

```bash
mssqlctl storage mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de los clústeres de macrodatos de 2019 de SQL Server, vea [¿cuáles son los clústeres de SQL Server 2019 macrodatos?](big-data-cluster-overview.md).