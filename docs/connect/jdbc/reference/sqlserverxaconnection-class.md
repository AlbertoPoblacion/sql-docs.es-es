---
title: Clase SQLServerXAConnection | Documentos de Microsoft
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
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6c016a665405a50ce133de5e45ef77ddf0981d0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverxaconnection-class"></a>Clase SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa las conexiones JDBC que pueden participar en transacciones distribuidas (XA).  
  
 **Paquete:** com.microsoft.sqlserver.jdbc  
  
 **Extiende:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implementa:** javax.sql.XAConnection  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto SQLServerXAConnection puede dar de alta en una transacción distribuida por medio de un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objeto. Un administrador de transacciones, normalmente forma parte de un servidor de nivel intermedio, administra un objeto SQLServerXAConnection a través del objeto SQLServerXAResource.  
  
> [!NOTE]  
>  Los programadores de la aplicación, por lo general, no utilizan directamente esta interfaz. Normalmente lo utiliza un administrador de transacciones que trabaja en el servidor del nivel intermedio.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Referencia de API del controlador JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
