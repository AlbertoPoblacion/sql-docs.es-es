---
title: dbo.sysproxies (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a1e16809177b6bec502493d03527343fecf6923
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Define atributos de una cuenta de proxy del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta tabla se almacena en la **msdb** base de datos.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Id. de la cuenta de proxy.|  
|**Nombre**|**sysname**|Nombre de la cuenta de proxy.|  
|**credential_id**|**int**|Id. de la credencial que utiliza la cuenta de proxy.|  
|**enabled**|**tinyint**|Estado de la cuenta de proxy:<br /><br /> **0** = deshabilitado. **1** = habilitado.|  
|**description**|**nvarchar(512)**|Descripción proporcionada por el usuario cuando se creó la cuenta de proxy.|  
|**user_sid**|**varbinary(85)**|Microsoft Windows *security_identifier* del usuario o grupo asociado con la credencial de proxy.|  
|**credential_date_created**|**datetime**|Es la fecha y hora en que se creó la credencial.|  
  
## <a name="remarks"></a>Comentarios  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede tener acceso a la **sysproxies** tabla.  
  
## <a name="see-also"></a>Vea también  
 [dbo.sysproxylogin &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
