---
title: "Método Unwrap (SQLServerXADataSource) | Documentos de Microsoft"
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
ms.assetid: d97c99b3-2224-4abb-8b32-40aff49fe759
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a59d9a1a7bf80f96bc509a6793703de9caa884d6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="unwrap-method-sqlserverxadatasource"></a>Método unwrap (SQLServerXADataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Devuelve un objeto que implementa la interfaz especificada para permitir el acceso a la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-métodos específicos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *iface*  
  
 Una clase de tipo **T** define una interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto que implementa la interfaz especificada.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 El [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) método se define mediante la interfaz java.sql.Wrapper, que se introdujo en las especificaciones de JDBC 4.0.  
  
 Las aplicaciones necesiten tener acceso a las extensiones para la API de JDBC que son específicas de la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. El método unwrap admite la acción de desencapsular para las clases públicas que extiende este objeto, si las clases tienen extensiones de proveedor.  
  
 El [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md) clase extiende la [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) (clase), que se extiende desde el [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) clase. Cuando se llama a este método, el objeto desencapsula las siguientes clases: [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), y [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
 Para obtener más información, consulte [contenedores e Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Miembros de SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Clase SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
