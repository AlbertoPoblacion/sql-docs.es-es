---
title: "getPooledConnection (método) (java.lang.String, java.lang.String) | Documentos de Microsoft"
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
apiname: SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a28924aab79628830fe2f51e6b8642f12be2bfd
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getpooledconnection-method-javalangstring-javalangstring"></a>Método getPooledConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Intenta establecer una conexión a bases de datos física que se pueda utilizar como una conexión agrupada basada en el nombre de usuario y contraseña especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public javax.sql.PooledConnection getPooledConnection(java.lang.String user,  
                                                      java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *usuario*  
  
 A **cadena** que contiene el nombre de usuario.  
  
 *passwword*  
  
 A **cadena** que contiene la contraseña.  
  
## <a name="return-value"></a>Valor devuelto  
 A [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) objeto.  
  
## <a name="exceptions"></a>Excepciones  
 java.sql.SQLException  
  
## <a name="remarks"></a>Comentarios  
 Este método getPooledConnection especificado por el método getPooledConnection en la interfaz javax.sql.ConnectionPoolDataSource.  
  
## <a name="see-also"></a>Vea también  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [Métodos SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Miembros de SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Clase SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
