---
title: Método getClientInfo (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b9fd6139a7fc36033c33fa4fc5301f5f7d0a4f14
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66763933"
---
# <a name="getclientinfo-method-javalangstring"></a>Método getClientInfo (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el valor de una propiedad de información del cliente especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Nombre*  
  
 Un valor String que contiene el nombre de la propiedad de información de cliente que se va a recuperar.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor String que contiene el valor de la propiedad de información de cliente.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notas  
 Este método getClientInfo especificado por el método getClientInfo de la interfaz java.sql.Connection.  
  
 El [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] no admite propiedades de información de cliente. Como resultado, este método devuelve **null**.  
  
 De igual forma, las aplicaciones pueden utilizar el método [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) de la clase [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) para recuperar una lista de las propiedades de información de cliente que admita el controlador. El método [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) devuelve un conjunto de resultados vacío.  
  
## <a name="see-also"></a>Consulte también  
 [Método getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Miembros SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Clase SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
