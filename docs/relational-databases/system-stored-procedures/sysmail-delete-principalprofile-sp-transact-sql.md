---
title: sysmail_delete_principalprofile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86f9566ce86423939aff22fc37331c5c9db89904
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909208"
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quita el permiso de un usuario o un rol de base de datos para usar un perfil público o privado de Correo electrónico de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @principal_id = ] principal_id` Es el identificador de usuario de base de datos o del rol en el **msdb** base de datos de la asociación que se va a eliminar. *principal_id* es **int**, su valor predeterminado es null. Para convertir un perfil público en un perfil privado, proporcione el identificador de entidad de seguridad **0** o el nombre principal de **'public'** . Cualquier *principal_id* o *principal_name* debe especificarse.  
  
`[ @principal_name = ] 'principal_name'` Es el nombre de usuario de base de datos o del rol en el **msdb** base de datos de la asociación que se va a eliminar. *principal_name* es **sysname**, su valor predeterminado es null. Para convertir un perfil público en un perfil privado, proporcione el identificador de entidad de seguridad **0** o el nombre principal de **'public'** . Cualquier *principal_id* o *principal_name* debe especificarse.  
  
`[ @profile_id = ] profile_id` Es el identificador del perfil para la asociación que se va a eliminar. *profile_id* es **int**, su valor predeterminado es null. Cualquier *profile_id* o *profile_name* debe especificarse.  
  
`[ @profile_name = ] 'profile_name'` Es el nombre del perfil de la asociación que se va a eliminar. *nombre_perfil* es **sysname**, su valor predeterminado es null. Cualquier *profile_id* o *profile_name* debe especificarse.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 Para convertir un perfil público en un perfil privado, proporcionar **'public'** para el nombre de entidad de seguridad o **0** para el identificador de entidad de seguridad.  
  
 Tenga cuidado al quitar permisos para el perfil privado predeterminado de un usuario o el perfil público predeterminado. Cuando no esté disponible, ningún perfil predeterminado **sp_send_dbmail** requiere que el nombre de un perfil como argumento. Por lo tanto, al quitar un perfil predeterminado puede provocar llamadas a **sp_send_dbmail** un error. Para obtener más información, consulte [sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 El procedimiento almacenado **sysmail_delete_principalprofile_sp** está en el **msdb** de base de datos y que pertenece el **dbo** esquema. El procedimiento debe ejecutarse con un nombre de tres partes si la base de datos actual no es **msdb**.  
  
## <a name="permissions"></a>Permisos  
 Permisos de ejecución de este procedimiento de forma predeterminada a los miembros de la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente muestra cuando se elimina la asociación entre el perfil **AdventureWorks Administrator** y el inicio de sesión **ApplicationUser** en el **msdb** base de datos.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Vea también  
 [Correo electrónico de base de datos](../../relational-databases/database-mail/database-mail.md)   
 [Objetos de configuración de correo electrónico de base de datos](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procedimientos almacenados de correo electrónico de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
