---
title: "Next (método) (SQLServerResultSet) | Documentos de Microsoft"
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
apiname: SQLServerResultSet.next
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 162902318cbc078ce214568b18e752fdd99559b1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="next-method-sqlserverresultset"></a>Next (método) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Mueve el cursor una fila hacia abajo desde su posición actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si la nueva fila actual es válida. **false** si no hay más filas que procesar.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método siguiente se especifica el método siguiente en la interfaz java.sql.ResultSet.  
  
 Un cursor del conjunto de resultados se coloca inicialmente antes de la primera fila. La primera llamada al método siguiente convierte la primera fila de la fila actual, la segunda llamada convierte a la segunda fila de la fila actual y así sucesivamente.  
  
 Si un flujo de entrada está abierto para la fila actual, una llamada al método siguiente cerrará de forma implícita. Una cadena de advertencia para la [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto se borra cuando se lee una fila nueva.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
