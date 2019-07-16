---
title: Tamaño del conjunto de filas del cursor | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d23fc32e866167a8ae1109d52e5b4699aeffc815
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68092873"
---
# <a name="cursor-rowset-size"></a>Tamaño del conjunto de filas del cursor
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Los cursores ODBC no están limitados a capturar una fila cada vez. Pueden recuperar varias filas en cada llamada a **SQLFetch** o [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Cuando se trabaja con una base de datos cliente/servidor, como [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de Microsoft, resulta más eficaz capturar varias filas a la vez. El número de filas devueltas en una operación de captura se denomina el tamaño del conjunto de filas y se especifica mediante el SQL_ATTR_ROW_ARRAY_SIZE de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Los cursores con un tamaño del conjunto de filas mayor que 1 reciben el nombre de cursores de bloque.  
  
 Hay dos opciones para enlazar las columnas de conjunto de resultados para los cursores de bloque:  
  
-   Enlace de modo de columna  
  
     Cada columna se enlaza a una matriz de variables. Cada matriz tiene el mismo número de elementos que el tamaño del conjunto de filas.  
  
-   Enlace de modo de fila  
  
     Una matriz se genera mediante estructuras que contienen los datos e indicadores para todas las columnas de una fila. La matriz tiene el mismo número de estructuras que el tamaño del conjunto de filas.  
  
 Cuando se usa el enlace de columna o fila, cada llamada a **SQLFetch** o **SQLFetchScroll** rellena las matrices enlazadas con datos desde el conjunto de filas recuperada.  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) también puede usarse para recuperar datos de la columna de un cursor de bloque. Dado que **SQLGetData** funciona una fila a la vez, **SQLSetPos** debe llamarse para establecer una fila específica en el conjunto de filas como la fila actual antes de llamar a **SQLGetData**.  
  
 El [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client proporciona una optimización mediante conjuntos de filas para recuperar un conjunto completo de resultados rápidamente. Para usar esta optimización, establezca los atributos de cursor en sus valores predeterminados (tamaño del conjunto de filas de solo avance y solo lectura = 1) en el momento **SQLExecDirect** o **SQLExecute** se llama. El [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client configura un conjunto de resultados predeterminado. Esto es más eficaz que los cursores de servidor al transferir los resultados al cliente sin desplazarse. Después de ejecutar la instrucción, aumente el tamaño del conjunto de filas y use el enlace de modo de columna o de modo de fila. Esto permite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] use un resultado predeterminado establecido en enviar de forma eficaz las filas de resultados al cliente, mientras que el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client extrae continuamente filas de los búferes de red en el cliente.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de cursor](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
