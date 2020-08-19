---
description: Conectarse a un origen de datos de Excel (Asistente para importación y exportación de SQL Server)
title: Conectarse a un origen de datos de Excel (Asistente para importación y exportación de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39ff753dec9f3f918fbd21dea3b04306feba307a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425307"
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Conectarse a un origen de datos de Excel (Asistente para importación y exportación de SQL Server)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


En este artículo se muestra cómo conectarse a un origen de datos de **Microsoft Excel** desde la página **Elegir un origen de datos** o **Elegir un destino** del Asistente para importación y exportación de SQL Server.

En la siguiente captura de pantalla se muestra una conexión de ejemplo a un libro de Microsoft Excel.

![Conexión de Excel](../../integration-services/import-export-data/media/excel-connection.png) 

Es posible que tenga que descargar e instalar archivos adicionales para conectarse a archivos de Excel. Para obtener más información, vea [Obtener los archivos que necesita para conectarse a Excel](../load-data-to-from-excel-with-ssis.md#files-you-need).

> [!IMPORTANT]
> Para obtener información detallada sobre cómo conectarse a archivos de Excel y sobre las limitaciones y problemas conocidos a la hora de cargar datos de o a archivos de Excel, vea [Cargar datos de o a Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

## <a name="options-to-specify"></a>Opciones que hay que especificar

> [!NOTE]
> Las opciones de conexión de este proveedor de datos son las mismas independientemente de si Excel es el origen o el destino. Es decir, las opciones que ve son las mismas en las páginas **Elegir un origen de datos** y **Elegir un destino** del asistente.

**Ruta de acceso del archivo Excel**  
 Especificar la ruta de acceso y el nombre del archivo de Excel. Por ejemplo:
-   Para un archivo en el equipo local, **C:\\MyData.xlsx**.
-   Para un archivo en un recurso compartido de red, **\\\\Sales\\Database\\Northwind.xlsx**.

O bien, haga clic en **Examinar**.  
  
 **Browse**  
 Busque la hoja de cálculo desde el cuadro de diálogo **Abrir**.  

> [!NOTE]
> El asistente no puede abrir un archivo de Excel protegido mediante contraseña.

 **Versión de Excel**  
Seleccione la versión de Excel que usa el libro de origen o de destino.

**La primera fila tiene nombres de columna**  
Indique si la primera fila de los datos contiene nombres de columna.
-   Si los datos no contienen nombres de columna, pero se habilita esta opción, el asistente trata la primera fila de los datos de origen como los nombres de columna.
-   Si los datos contienen nombres de columna, pero se deshabilita esta opción, el asistente trata la fila de nombres de columna como la primera fila de datos.

Si especifica que los datos no tienen nombres de columna, el asistente usa F1, F2, etc., como encabezados de columna.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>No veo Excel en la lista de orígenes de datos
Si no ve Excel en la lista de orígenes de datos, ¿comprobó que está ejecutando el asistente de 64 bits? Los proveedores para Excel y Access son normalmente de 32 bits y no son visibles en el asistente de 64 bits. Ejecute al asistente de 32 bits en su lugar.

> [!NOTE]
> Para usar la versión de 64 bits del asistente para importación y exportación de SQL Server, tendrá que instalar SQL Server. SQL Server Data Tools (SSDT) y SQL Server Management Studio (SSMS) son aplicaciones de 32 bits y solo instalan archivos de 32 bits, incluida la versión de 32 bits del asistente.

## <a name="see-also"></a>Consulte también
[Cargar datos de o a Excel con SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
[Choose a Data Source](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md) (Selección de un origen de datos)  
[Choose a Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md) (Selección de un destino)

