---
title: Establecer una conexión | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establising a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establising a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70f459f60616e7edd77078a7e9653ab9dff097e9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248346"
---
# <a name="establishing-a-connection"></a>Establecer una conexión
Después de asignar identificadores de entorno y de conexión y establecer los atributos de conexión, la aplicación está lista para conectarse al origen de datos o al controlador. Hay tres funciones diferentes, que la aplicación puede usar para hacer esto: **SQLConnect** (nivel de conformidad con la interfaz de núcleo), **SQLDriverConnect** (Core), y **SQLBrowseConnect** (nivel 1). Cada uno de los tres está diseñado para usarse en un escenario diferente. Antes de conectarse, la aplicación puede determinar cuál de estas funciones es compatible con la **ConnectFunctions** palabra clave devuelto por **SQLDrivers**.  
  
> [!NOTE]  
>  Algunos controladores de limitan el número de conexiones activas que admiten. Una aplicación llama a **SQLGetInfo** con la opción SQL_MAX_DRIVER_CONNECTIONS para determinar cuántas conexiones activas que admite un controlador determinado.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Origen de datos predeterminado](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Conexión con SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Cadenas de conexión](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Conexión con SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Conectar con SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
