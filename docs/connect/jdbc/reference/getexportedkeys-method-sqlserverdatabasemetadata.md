---
title: "Método getExportedKeys (SQLServerDatabaseMetaData) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getExportedKeys
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 78a2ace3784458d21546379f7073091832af1496
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>Método getExportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descripción de las columnas de clave externa que hacen referencia a las columnas de clave principal de la tabla determinadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *CAT*  
  
 A **cadena** que contiene el nombre del catálogo.  
  
 *esquema*  
  
 A **cadena** que contiene el nombre del esquema.  
  
 *table*  
  
 A **cadena** que contiene el nombre de tabla.  
  
## <a name="return-value"></a>Valor devuelto  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getExportedKeys especificado por el método getExportedKeys en la interfaz java.sql.DatabaseMetaData.  
  
 El conjunto de resultados devuelto por el método getExportedKeys contendrá la siguiente información:  
  
|Nombre|Tipo|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|Nombre del catálogo que contiene la tabla de la clave principal.|  
|PKTABLE_SCHEM|**String**|Nombre del esquema de la tabla de la clave principal.|  
|PKTABLE_NAME|**String**|Nombre de la tabla de la clave principal.|  
|PKCOLUMN_NAME|**String**|Nombre de la columna de la clave principal.|  
|FKTABLE_CAT|**String**|Nombre del catálogo que contiene la tabla de la clave externa.|  
|FKTABLE_SCHEM|**String**|Nombre del esquema de la tabla de la clave externa.|  
|FKTABLE_NAME|**String**|Nombre de la tabla de la clave externa.|  
|FKCOLUMN_NAME|**String**|Nombre de la columna de la clave externa.|  
|KEY_SEQ|**corto**|Número de secuencia de la columna en una clave principal en varias columnas.|  
|UPDATE_RULE|**corto**|Acción aplicada a la clave externa cuando la operación de SQL sea una actualización. Puede ser uno de los siguientes valores:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**corto**|Acción aplicada a la clave externa cuando la operación de SQL sea una eliminación. Puede ser uno de los siguientes valores:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|El nombre de la clave externa.|  
|PK_NAME|**String**|Nombre de la clave principal.|  
|DEFERRABILITY|**corto**|Indica si la evaluación de la restricción de la clave externa se puede diferir hasta que se efectúe una confirmación. Puede ser uno de los siguientes valores:<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Para obtener más información acerca de los datos devueltos por el método getExportedKeys, vea "sp_fkeys (Transact-SQL)" en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] libros en pantalla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el método getExportedKeys para devolver información sobre todas las claves externas que hacen referencia a las claves principales de la tabla Person.Contact en la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] base de datos de ejemplo.  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
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
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
