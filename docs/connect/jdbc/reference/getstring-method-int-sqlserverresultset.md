---
title: "Método getString (int) (SQLServerResultSet) | Documentos de Microsoft"
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
apiname: SQLServerResultSet.getString (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: bfa493c4-fe07-449b-b4d0-384e1a1fce48
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 677c6642a2eb9ab969b507c056c5c64a0aac95e4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getstring-method-int-sqlserverresultset"></a>Método getString (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el valor del índice de columna designado en la fila actual de este [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto como un **cadena** en el lenguaje de programación Java.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.String getString(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnIndex*  
  
 Un **int** que indica el índice de columna.  
  
## <a name="return-value"></a>Valor devuelto  
 A **cadena** valor.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getString especificado por el método getString de la interfaz java.sql.ResultSet.  
  
 Todas las columnas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] puede devolverse como una cadena. Esto significa que un **cadena** pueden ser la representación de todos los tipos basados en número y carácter y una representación de cadena hexadecimal de columnas binarias como binary, varbinary, varbinary (max), imagen, timestamp y uniqueidentifier, Devuelve.  
  
 Tipos de dependientes de la ubicación como money, smallmoney, datetime, smalldatetime, float, real, decimal y numeric devolverán el formato canónico toString() para el valor subyacente del tipo.  
  
 Tipos definidos por el usuario se devuelven como hexadecimal **cadena** valores.  
  
## <a name="see-also"></a>Vea también  
 [Método getString &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
