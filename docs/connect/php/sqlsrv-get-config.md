---
title: sqlsrv_get_config | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef4f53e4ee4ae1c9022ea8bfab0ba7a66c147c08
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922753"
---
# <a name="sqlsrv_get_config"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Devuelve el valor actual de la configuración especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>Parámetros  
*$setting*: la configuración para la que se devuelve el valor. Para obtener una lista de valores configurables, consulte [sqlsrv_configure](../../connect/php/sqlsrv-configure.md).  
  
## <a name="return-value"></a>Valor devuelto  
El valor de la configuración especificado mediante el parámetro *$setting* . Si se especifica una configuración no válida, se devuelve **False** y se agrega un error a la colección de errores.  
  
## <a name="remarks"></a>Observaciones  
Si **False** config **sqlsrv_get_config**, debe llamar a [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) para determinar si se produjo un error o si **False** es el valor de la configuración especificada mediante el parámetro *$setting* .  
  
## <a name="see-also"></a>Consulte también  
[Referencia de API del controlador SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
