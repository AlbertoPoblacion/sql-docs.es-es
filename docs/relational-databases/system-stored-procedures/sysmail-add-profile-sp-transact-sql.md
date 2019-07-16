---
title: sysmail_add_profile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f70661db4dbd34475a5708b8ae9ca3691c94e689
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017802"
---
# <a name="sysmailaddprofilesp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuevo perfil de Correo electrónico de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @profile_name = ] 'profile\_name'` El nombre del nuevo perfil. *nombre_perfil* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @description = ] 'description'` La descripción opcional para el nuevo perfil. *descripción* es **nvarchar (256)** , no tiene ningún valor predeterminado.  
  
`[ @profile_id = ] _new\_profile\_idOUTPUT` Devuelve el identificador del nuevo perfil. *new_profile_id* es **int**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 Un perfil de Correo electrónico de base de datos contiene cualquier número de cuentas de Correo electrónico de base de datos. Los procedimientos almacenados de Correo electrónico de base de datos pueden hacer referencia a un perfil por el nombre o por el Id. del perfil generado por este procedimiento. Para obtener más información acerca de cómo agregar una cuenta a un perfil, vea [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md).  
  
 El nombre del perfil y la descripción se pueden cambiar con el procedimiento almacenado **sysmail_update_profile_sp**, mientras que el identificador del perfil permanece constante durante la vida del perfil.  
  
 El nombre del perfil debe ser único para el [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] de Microsoft o el procedimiento almacenado devuelve un error.  
  
 El procedimiento almacenado **sysmail_add_profile_sp** está en el **msdb** de base de datos y que pertenece el **dbo** esquema. El procedimiento debe ejecutarse con un nombre de tres partes si la base de datos actual no es **msdb**.  
  
## <a name="permissions"></a>Permisos  
 Permisos de ejecución de este procedimiento de forma predeterminada a los miembros de la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 **A. Crear un nuevo perfil**  
  
 En el ejemplo siguiente se crea un nuevo perfil de Correo electrónico de base de datos denominado `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **B. Crear un nuevo perfil y guardar el Id. de perfil en una variable**  
  
 En el ejemplo siguiente se crea un nuevo perfil de Correo electrónico de base de datos denominado `AdventureWorks Administrator`. En el ejemplo se almacena el Id. del perfil en la variable `@profileId` y se devuelve un conjunto de resultados que contiene el Id. del nuevo perfil.  
  
```  
DECLARE @profileId INT ;  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.',  
       @profile_id = @profileId OUTPUT ;  
  
SELECT @profileId ;  
```  
  
## <a name="see-also"></a>Vea también  
 [Correo electrónico de base de datos](../../relational-databases/database-mail/database-mail.md)   
 [Crear una cuenta de correo electrónico de base de datos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Objetos de configuración de correo electrónico de base de datos](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procedimientos almacenados de correo electrónico de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
