---
title: Sys.linked_logins (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ca2137294edf7a24c0ad5b167c5e1037a86cab1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila por asignación de inicio de sesión de servidor vinculado para su uso por parte de las RPC y las consultas distribuidas desde el servidor local al servidor vinculado correspondiente.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Id. del servidor en **sys.servers**.|  
|**local_principal_id**|**int**|Entidad de seguridad de servidor a la que se aplica la asignación.<br /><br /> 0 = comodín o public.|  
|**uses_self_credential**|**bit**|Si es 1, la asignación indica que la sesión debe utilizar sus propias credenciales; por el contrario, 0 indica que la sesión utiliza el nombre y la contraseña proporcionados.|  
|**remote_name**|**sysname**|Nombre de usuario remoto que se va a utilizar al conectar. La contraseña también se almacena, pero no se expone en las interfaces de la vista de catálogo.|  
|**modify_date**|**datetime**|Fecha en que se cambió el inicio de sesión vinculado por última vez.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vistas de catálogo de los servidores vinculados &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
