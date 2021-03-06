---
title: "Método setCatalog (SQLServerConnection) | Documentos de Microsoft"
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
apiname: SQLServerConnection.setCatalog
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44420fcaa6ecc0ab97dcb44344688b0cf92c9645
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setcatalog-method-sqlserverconnection"></a>Método setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el nombre de catálogo determinado para seleccionar un subespacio de este [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) base de datos del objeto en el que se va a trabajar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *catálogo*  
  
 A **cadena** que contiene el nombre del catálogo.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método setCatalog especificado por el método setCatalog en la interfaz java.sql.Connection.  
  
 El *catálogo* argumento es la secuencia de escape el [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automáticamente. Con este método establece la propiedad de catálogo para el objeto de conexión. No se establece implícitamente de cualquier otra manera.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Clase SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
