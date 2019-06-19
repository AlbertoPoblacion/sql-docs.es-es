---
title: sys.dm_cryptographic_provider_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f8f497019dea80bbe79903c60531f506d7950371
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62741991"
---
# <a name="sysdmcryptographicproviderproperties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información sobre los proveedores de servicios criptográficos registrados.  
  
 
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|Número de identificación del proveedor de servicios criptográficos.|  
|guid|**uniqueidentifier**|Proveedor único GUID.|  
|provider_version|**nvarchar(256)**|Versión del proveedor en el formato '*aa.bb.cccc.dd*'.|  
|sqlcrypt_version|**nvarchar(256)**|Versión principal de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] API criptográfica con el formato '*aa.bb.cccc.dd*'.|  
|friendly_name|**nvarchar(2048)**|El proveedor proporcionó el nombre.|  
|authentication_type|**nvarchar(256)**|WINDOWS, BASIC u OTHER.|  
|symmetric_key_support|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|symmetric_key_export|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|symmetric_key_import|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|symmetric_key_persistance|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|asymmetric_key_support|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|asymmetric_key_export|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|symmetric_key_import|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
|symmetric_key_persistance|**tinyint**|0 (no admitido)<br /><br /> 1 (admitido)|  
  
## <a name="remarks"></a>Comentarios  
 La vista sys.dm_cryptographic_provider_properties está visible para la función public.  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Administración extensible de claves &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Funciones y vistas de administración dinámica relacionadas con la seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
