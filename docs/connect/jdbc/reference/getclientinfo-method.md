---
title: Método getClientInfo () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a6b68caa4abff00f113176791d06c6361c5da1e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953114"
---
# <a name="getclientinfo-method-"></a>Método getClientInfo ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una lista que contiene el nombre y valor vigentes de cada propiedad de información del cliente que admita el controlador JDBC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto Properties que contiene el nombre y el valor actual de cada una de las propiedades de información de cliente que admite el controlador.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notas  
 Este método getClientInfo se especifica mediante el método getClientInfo en la interfaz java. SQL. Connection.  
  
 El [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] no admite propiedades de información de cliente. Como resultado, este método devuelve un objeto de propiedades vacío.  
  
 De igual forma, las aplicaciones pueden utilizar el método [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) de la clase [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) para recuperar una lista de las propiedades de información de cliente que admita el controlador. El método [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) devuelve un conjunto de resultados vacío.  
  
## <a name="see-also"></a>Consulte también  
 [Método getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Miembros SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Clase SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
