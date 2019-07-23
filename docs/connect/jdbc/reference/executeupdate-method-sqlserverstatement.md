---
title: Método executeUpdate (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10ae662a-ce3c-4b24-875c-5c2df319d93b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c13b439c687ea59e895bea8db162a0d64e887e5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954593"
---
# <a name="executeupdate-method-sqlserverstatement"></a>Método executeUpdate (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ejecuta la instrucción SQL determinada, que puede ser una instrucción INSERT, UPDATE o DELETE; o una instrucción SQL que no devuelve nada, como una instrucción DDL de SQL. A partir del controlador JDBC 3.0 de [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], executeUpdate devolverá el número correcto de filas actualizado en una operación MERGE.  
  
## <a name="overload-list"></a>Lista de sobrecargas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[executeUpdate (java.lang.String)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-sqlserverstatement.md)|Ejecuta la instrucción SQL determinada, que puede ser una instrucción INSERT, UPDATE, DELETE o MERGE; o una instrucción SQL que no devuelve nada, como una instrucción DDL de SQL.|  
|[executeUpdate (java.lang.String, int)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-int.md)|Ejecuta la instrucción SQL especificada y señala el [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con la marca indicada sobre si las claves generadas automáticamente por este objeto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) deben estar disponibles para su recuperación.|  
|[executeUpdate (java.lang.String, int&#91;&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string.md)|Ejecuta la instrucción SQL determinada e indica al controlador JDBC que las claves que se han generado automáticamente y están presentes en la matriz determinada deben estar disponibles para su recuperación.|  
|[executeUpdate (java.lang.String, java.lang.String&#91;&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-java-lang-string.md)|Ejecuta la instrucción SQL determinada e indica al controlador JDBC que las claves que se han generado automáticamente y están presentes en la matriz determinada deben estar disponibles para su recuperación.|  
  
## <a name="see-also"></a>Consulte también  
 [Miembros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Clase SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
