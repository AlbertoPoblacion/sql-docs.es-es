---
title: Conectarse a un origen de datos PostgreSQL (Asistente para importación y exportación de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b7a75a72-b267-444f-9eb8-d23eb333fc35
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f895175a3ee4798643c2841399d2ed2ea9a89c27
ms.sourcegitcommit: 5683044d87f16200888eda2c2c4dee38ff87793f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58221999"
---
# <a name="connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard"></a>Conectarse a un origen de datos PostgreSQL (Asistente para importación y exportación de SQL Server)
En este tema se muestra cómo conectarse a un origen de datos **PostgreSQL** desde la página **Elegir un origen de datos** o **Elegir un destino** del asistente para importación y exportación de SQL Server. 

> [!IMPORTANT]
> Los requisitos detallados y los requisitos previos para conectarse a una base de datos PostgreSQL no se indicarán en este artículo de Microsoft. En este artículo se da por supuesto que ya tiene instalado el software de cliente PostgreSQL y que puede conectarse correctamente a la base de datos de destino PostgreSQL. Para obtener más información, consulte la documentación de PostgreSQL o el administrador de base de datos PostgreSQL.

## <a name="get-the-postgresql-odbc-driver"></a>Obtener el controlador ODBC de PostgreSQL

### <a name="install-the-odbc-driver-with-stack-builder"></a>Instalar el controlador ODBC con Stack Builder
Ejecute Stack Builder para agregar el controlador de ODBC de PostgreSQL (psqlODBC) a la instalación de PostgreSQL.

![Instalar ODBC de PostgreSQL con Stack Builder](../../integration-services/import-export-data/media/install-postgresql-odbc-with-stack-builder.png)

### <a name="or-download-the-latest-odbc-driver"></a>O bien, descargar el controlador más reciente de ODBC
También puede descargar el instalador de Windows para la versión más reciente del controlador ODBC de PostgreSQL (psqlODBC) directamente desde este sitio FTP: [https://www.postgresql.org/ftp/odbc/versions/msi/](https://www.postgresql.org/ftp/odbc/versions/msi/). Extraiga los archivos del archivo .zip y ejecute el archivo .msi.

## <a name="connect-to-postgresql-with-the-postgresql-odbc-driver-psqlodbc"></a>Conectarse a PostgreSQL con el controlador ODBC de PostgreSQL (psqlODBC)
Los controladores ODBC no aparecen en la lista desplegable de los orígenes de datos. Para conectarse con un controlador ODBC, empiece seleccionando el **proveedor de datos de .NET Framework para ODBC** como origen de datos en la página **Elegir un origen de datos** o **Elegir un destino**. Este proveedor actúa como un contenedor para el controlador ODBC.

Esta es la pantalla genérica que se ve inmediatamente después de seleccionar el proveedor de datos de .NET Framework para ODBC.

![Conectarse antes a PostgreSQL con ODBC](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-postgresql-odbc-driver"></a>Opciones que hay que especificar (controlador ODBC de PostgreSQL)

> [!NOTE]
> Las opciones de conexión de este proveedor de datos y el controlador ODBC son las mismas independientemente de si PostgreSQL es el origen o el destino. Es decir, las opciones que ve son las mismas en las páginas **Elegir un origen de datos** y **Elegir un destino** del asistente.

Para conectarse a PostgreSQL con el controlador ODBC de PostgreSQL, ensamble una cadena de conexión que incluya las siguientes opciones y sus valores. El formato de una cadena de conexión completa aparece inmediatamente después de la lista de opciones.

> [!TIP]
> Obtenga ayuda para ensamblar una cadena de conexión que funcione correctamente. O bien, en lugar de proporcionar una cadena de conexión, puede proporcionar un DSN (nombre de origen de datos) existente o crear uno nuevo. Para obtener más información acerca de estas opciones, consulte [Conectarse a un origen de datos ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Controlador**  
Es el nombre del controlador ODBC, ya sea un **controlador ODBC de PostgreSQL (UNICODE)** o **Controlador ODBC de PostgreSQL (ANSI)**.

**Server**  
Nombre del servidor de PostgreSQL. 

**Puerto**  
Puerto que se usará para conectarse al servidor de PostgreSQL.

**Base de datos**  
Nombre de la base de datos PostgreSQL.

**Uid** y **Pwd**   
Son los valores **Uid** (id. de usuario) y **Pwd** (contraseña) para conectarse.

### <a name="connection-string-format"></a>Formato de la cadena de conexión
Este es el formato de una cadena de conexión típica. 

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=<server>;Port=<port>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>Escribir la cadena de conexión
Escriba la cadena de conexión en el campo **ConnectionString** o escriba el nombre DSN en el campo **DSN**, que se encuentra en la página **Elegir un origen de datos** o **Elegir un destino**. Después de escribir la cadena de conexión, el asistente la analiza y muestra las propiedades individuales y sus valores en la lista.

En el siguiente ejemplo se emplea esta cadena de conexión.

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=127.0.0.1;Port=5432;Database=postgres;UID=postgres;PWD=********
    ```

Esta es la pantalla que verá después de escribir la cadena de conexión.

![Conectarse a PostgreSQL con ODBC](../../integration-services/import-export-data/media/connect-to-postgresql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Otros proveedores de datos y más información
Para obtener más información sobre cómo conectarse a PostgreSQL con un proveedor de datos que no aparezca aquí, consulte [PostgreSQL connection strings (Cadenas de conexión de PostgreSQL)](https://www.connectionstrings.com/postgresql/). En este sitio de terceros también encontrará más información sobre los proveedores de datos y los parámetros de conexión que se describen en esta página.

## <a name="see-also"></a>Vea también
[Choose a Data Source](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md) (Selección de un origen de datos)  
[Choose a Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md) (Selección de un destino)

