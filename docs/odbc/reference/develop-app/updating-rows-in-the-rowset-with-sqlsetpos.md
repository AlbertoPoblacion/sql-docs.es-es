---
title: Actualización de filas en el conjunto de filas con SQLSetPos ? Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4851d4ba741379fc188b2b88c895a378ef3bb80d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298975"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Actualizar las filas del conjunto de filas con SQLSetPos
La operación de actualización de **SQLSetPos** hace que el origen de datos actualice una o varias filas seleccionadas de una tabla, utilizando datos en los búferes de aplicación para cada columna enlazada (a menos que el valor del búfer de longitud/indicador sea SQL_COLUMN_IGNORE). Las columnas que no están enlazadas no se actualizarán.  
  
 Para actualizar filas con **SQLSetPos**, la aplicación hace lo siguiente:  
  
1.  Coloca los nuevos valores de datos en los búferes del conjunto de filas. Para obtener información sobre cómo enviar datos largos con **SQLSetPos**, vea [Long Data y SQLSetPos y SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Establece el valor en el búfer de longitud/indicador de cada columna según sea necesario. Esta es la longitud de bytes de los datos o SQL_NTS de las columnas enlazadas a búferes de cadena, la longitud de bytes de los datos de las columnas enlazadas a búferes binarios y SQL_NULL_DATA para que las columnas se establezcan en NULL.  
  
3.  Establece el valor en el búfer de longitud/indicador de las columnas que no se deben actualizar a SQL_COLUMN_IGNORE. Aunque la aplicación puede omitir este paso y reenviar los datos existentes, esto es ineficaz y corre el riesgo de enviar valores al origen de datos que se truncaron cuando se leyeron.  
  
4.  Llama a **SQLSetPos** con *Operation* establecido en SQL_UPDATE y *RowNumber* establecido en el número de la fila que se debe actualizar. Si *RowNumber* es 0, se actualizan todas las filas del conjunto de filas.  
  
 Después de **SQLSetPos** devuelve, la fila actual se establece en la fila actualizada.  
  
 Al actualizar todas las filas del conjunto de filas (*RowNumber* es igual a 0), una aplicación puede deshabilitar la actualización de determinadas filas estableciendo los elementos correspondientes de la matriz de operaciones de fila (señalado por el atributo de instrucción SQL_ATTR_ROW_OPERATION_PTR) en SQL_ROW_IGNORE. La matriz de operaciones de fila corresponde en tamaño y número de elementos a la matriz de estado de fila (señalada por el atributo de instrucción SQL_ATTR_ROW_STATUS_PTR). Para actualizar solo las filas del conjunto de resultados que se capturaron correctamente y no se han eliminado del conjunto de filas, la aplicación utiliza la matriz de estado de fila de la función que captura el conjunto de filas como matriz de operaciones de fila en **SQLSetPos**.  
  
 Para cada fila que se envía al origen de datos como una actualización, los búferes de aplicación deben tener datos de fila válidos. Si los búferes de aplicación se llenaron mediante la obtención y si se ha mantenido una matriz de estado de fila, sus valores en cada una de estas posiciones de fila no deben ser SQL_ROW_DELETED, SQL_ROW_ERROR o SQL_ROW_NOROW.  
  
 Por ejemplo, el código siguiente permite a un usuario desplazarse por la tabla Customers y actualizar, eliminar o agregar nuevas filas. Coloca los nuevos datos en los búferes del conjunto de filas antes de llamar a **SQLSetPos** para actualizar o agregar nuevas filas. Se asigna una fila adicional al final de los búferes del conjunto de filas para contener nuevas filas; esto impide que los datos existentes se sobrescriban cuando los datos de una nueva fila se colocan en los búferes.  
  
```  
#define UPDATE_ROW   100  
#define DELETE_ROW   101  
#define ADD_ROW      102  
  
SQLUINTEGER    CustIDArray[11];  
SQLCHAR        NameArray[11][51], AddressArray[11][51],   
               PhoneArray[11][11];  
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11],   
               AddressLenOrIndArray[11],  
               PhoneLenOrIndArray[11];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
            AddressLenOrIndArray);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);  
  
// Fetch and display the first 10 rows.  
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,  
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
  
// Call GetAction to get an action and a row number from the user.  
while (GetAction(&Action, &RowNum)) {  
   switch (Action) {  
  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray,  
                     NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray,  
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case UPDATE_ROW:  
         // Place the new data in the rowset buffers and update the   
         // specified row.  
         GetNewData(&CustIDArray[RowNum - 1], &CustIDIndArray[RowNum - 1],  
                  NameArray[RowNum - 1], &NameLenOrIndArray[RowNum - 1],  
                  AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                  PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case DELETE_ROW:  
         // Delete the specified row.  
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case ADD_ROW:  
         // Place the new data in the rowset buffers at index 10.   
         // This is an extra element for new rows so rowset data is   
         // not overwritten. Insert the new row. Row 11 corresponds   
         // to index 10.  
         GetNewData(&CustIDArray[10], &CustIDIndArray[10],  
                     NameArray[10], &NameLenOrIndArray[10],  
                     AddressArray[10], &AddressLenOrIndArray[10],  
                     PhoneArray[10], &PhoneLenOrIndArray[10]);  
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
