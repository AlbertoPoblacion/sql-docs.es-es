---
title: "Método executeQuery (SQLServerStatement) | Documentos de Microsoft"
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
apiname: SQLServerStatement.executeQuery
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 599cf463-e19f-4baa-bacb-513cad7c6cd8
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 364285e454cefece9c656a50951747c674581b42
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="executequery-method-sqlserverstatement"></a>Método executeQuery (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ejecuta la instrucción SQL especificada y devuelve una sola [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *SQL*  
  
 A **cadena** que contiene una instrucción SQL.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto SQLServerResultSet.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método executeQuery es especificado por el método executeQuery en la interfaz java.sql.Statement.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) se produce si la instrucción SQL especificada genera algo distinto de una sola [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
 Si ejecuta un procedimiento almacenado da como resultado un recuento de actualizaciones que es mayor que uno, o que genera más de un conjunto de resultados, use la [ejecutar](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) método para ejecutar el procedimiento almacenado.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Clase SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
