---
title: "isPoolable (método) (SQLServerStatement) | Documentos de Microsoft"
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
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7861ef89f072371bf3747e20b7128755ac1520f1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="ispoolable-method-sqlserverstatement"></a>isPoolable (método) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Devuelve un valor que indica si una instrucción se puede agregar al grupo de instrucciones proporcionado por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si la instrucción se puede agregar al grupo de instrucción proporcionado por el usuario; **false** en caso contrario.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) cambia el comportamiento de la capacidad de un objeto.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Clase SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
