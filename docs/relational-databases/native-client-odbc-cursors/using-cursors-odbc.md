---
title: Uso de cursores (ODBC) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d6572c8681dff0d8d8d2147c7f077ca9b7634d4
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2018
---
# <a name="using-cursors-odbc"></a>Uso de cursores (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC admite un modelo de cursor que permite:  
  
-   Varios tipos de cursores.  
  
-   Desplazamiento y colocación en un cursor.  
  
-   Varias opciones de simultaneidad.  
  
-   Actualizaciones posicionadas.  
  
 Las aplicaciones ODBC raramente declaran y abren cursores o utilizan cualquier instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] relacionada con cursores. ODBC abre automáticamente un cursor para cada conjunto de resultados que devuelve una instrucción SQL. Las características de los cursores se controlan mediante los atributos de instrucción establecidos con [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) antes de la instrucción SQL se ejecuta la instrucción. Las funciones de la API de ODBC para procesar conjuntos de resultados admiten toda la funcionalidad del cursor, entre la que se incluye la captura, el desplazamiento y las actualizaciones posicionadas.  
  
 A continuación se ofrece una comparación de cómo los scripts de [!INCLUDE[tsql](../../includes/tsql-md.md)] y las aplicaciones ODBC trabajan con cursores.  
  
|Acción|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|Definir el comportamiento del cursor|Se especifica a través de parámetros DECLARE CURSOR|Establecer atributos de cursor mediante [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)|  
|Abrir un cursor|DECLARE CURSOR OPEN *cursor_name*|**SQLExecDirect** o **SQLExecute**|  
|Capturar filas|FETCH|**SQLFetch** o [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)|  
|Actualización posicionada|Cláusula WHERE CURRENT OF en UPDATE o DELETE|**SQLSetPos**|  
|Cerrar un cursor|CERRAR *cursor_name* DEALLOCATE|[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)|  
  
 Los cursores de servidor implementados en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admiten la funcionalidad del modelo de cursores de ODBC. El controlador [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utiliza cursores de servidor para admitir la funcionalidad de cursor de la API de ODBC.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Cómo se implementan los cursores](../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
-   [Tipos de cursor](../../relational-databases/native-client-odbc-cursors/cursor-types.md)  
  
-   [Comportamientos de cursor](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
-   [Propiedades de cursor](../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
-   [Detalles de la programación de cursor &#40; ODBC &#41;](../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
-   [Desplazamiento y captura de filas](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
-   [Posición actualizaciones &#40; ODBC &#41;](../../relational-databases/native-client-odbc-cursors/positioned-updates-odbc.md)  
  
## <a name="see-also"></a>Vea también  
 [Cliente nativo de SQL Server &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [Cursores](../../relational-databases/cursors.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
