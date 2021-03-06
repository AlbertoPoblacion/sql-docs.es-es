---
title: "getSchemas (método) (String, String) | Documentos de Microsoft"
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
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1309f95e5ccdb95c6cfe2f60fe88bf6b26794fdf
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getschemas-method-string-string"></a>Método getSchemas (String, String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera los nombres de esquema que están disponibles en la base de datos actual a través del nombre del catálogo y de esquema especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *catálogo*  
  
 El nombre de un catálogo en la base de datos. Si es una cadena vacía "", el resultado incluye los esquemas sin un catálogo. Si es **null**, el nombre del catálogo no se utiliza para la búsqueda.  
  
 *schemaPattern*  
  
 El nombre de un esquema. Si es **null**, el nombre del esquema no se utiliza para la búsqueda.  
  
## <a name="return-value"></a>Valor devuelto  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getSchemas es especificado por el método getSchemas en la interfaz java.sql.DatabaseMetaData.  
  
 El conjunto de resultados devuelto por el método getSchemas contiene la información siguiente:  
  
|Nombre|Tipo|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|Nombre del esquema.|  
|TABLE_CATALOG|**String**|Nombre del catálogo para el esquema.|  
  
 Los resultados se ordenan por TABLE_CATALOG y, a continuación, según TABLE_SCHEM. En cada fila TABLE_SCHEM es la primera columna y TABLE_CATALOG la segunda.  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
