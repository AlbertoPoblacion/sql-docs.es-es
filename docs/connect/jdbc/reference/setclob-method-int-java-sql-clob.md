---
title: "Método setClob (int, java.sql.Clob) | Documentos de Microsoft"
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
apiname: SQLServerPreparedStatement.setClob
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 68d49f2c-fd8d-4abb-bfdc-e7b0fbd9a9da
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 89056fc3a5c61211b7a3c542d31e68161a2fcc80
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setclob-method-int-javasqlclob"></a>Método setClob (int, java.sql.Clob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el parámetro designado para el objeto Clob determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.sql.Clob clobValue)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *parameterIndex*  
  
 Un **int** que indica el número de parámetro.  
  
 *clobValue*  
  
 Un objeto Clob.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método setClob especificado por el método setClob en la interfaz java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-methods.md)   
 [Clase SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
