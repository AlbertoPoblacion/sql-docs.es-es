---
title: Método getBestRowIdentifier (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getBestRowIdentifier
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c19e9ca6-2a53-4a0c-91ab-80090c3f7229
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9a19bd01a8ebf54eb3e819bd4a82400b8107e382
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954027"
---
# <a name="getbestrowidentifier-method-sqlserverdatabasemetadata"></a>Método getBestRowIdentifier (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descripción del conjunto óptimo de columnas de una tabla que identifique una fila de forma única.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.ResultSet getBestRowIdentifier(java.lang.String catalog,  
                                               java.lang.String schema,  
                                               java.lang.String table,  
                                               int scope,  
                                               boolean nullable)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *catalog*  
  
 Objeto **String** que contiene el nombre del catálogo.  
  
 *schema*  
  
 Objeto **String** que contiene el nombre del esquema.  
  
 *table*  
  
 Objeto **String** que contiene el nombre de la tabla.  
  
 *scope*  
  
 Un valor **int** que indica el ámbito de interés. Los valores pueden incluir lo siguiente:  
  
 bestRowTemporary (0)  
  
 bestRowTransaction (1)  
  
 bestRowSession (2)  
  
 *nullable*  
  
 Es **true** para incluir columnas con valores NULL. De lo contrario, se devuelve el valor **False**.  
  
## <a name="return-value"></a>Valor devuelto  
 Objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Observaciones  
 El método getBestRowIdentifier especifica este método getBestRowIdentifier en la interfaz java.sql.DatabaseMetaData.  
  
 El conjunto de resultados devuelto por el método getBestRowIdentifier contendrá la siguiente información:  
  
|Nombre|Tipo|Descripción|  
|----------|----------|-----------------|  
|SCOPE|short|Ámbito de los resultados devueltos. Puede ser uno de los siguientes valores:<br /><br /> bestRowTemporary (0)<br /><br /> bestRowTransaction (1)<br /><br /> bestRowSession (2)|  
|COLUMN_NAME|String|Nombre de la columna.|  
|DATA_TYPE|short|Tipo de datos SQL de java.sql.Types.|  
|TYPE_NAME|String|El nombre del tipo de datos.|  
|COLUMN_SIZE|int|Precisión de la columna.|  
|BUFFER_LENGTH|int|Longitud del búfer.|  
|DECIMAL_DIGITS|short|Escala de la columna.|  
|PSEUDO_COLUMN|short|Indica si la columna es una pseudocolumna. Puede ser uno de los siguientes valores:<br /><br /> bestRowUnknown (0)<br /><br /> bestRowNotPseudo (1)<br /><br /> bestRowPseudo (2)|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo utilizar el método getBestRowIdentifier para devolver información acerca del mejor identificador de fila para la tabla Person.Contact en la base de datos de ejemplo [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetBestRowIdentifier(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getBestRowIdentifier(null, "Person", "Contact", 0, true);  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }  
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
