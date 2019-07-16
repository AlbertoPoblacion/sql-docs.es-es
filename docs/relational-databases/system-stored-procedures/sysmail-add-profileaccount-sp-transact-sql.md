---
title: sysmail_add_profileaccount_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profileaccount_sp
- sysmail_add_profileaccount_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profileaccount_sp
ms.assetid: 7cbf430f-1997-45ea-9707-0086184de744
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11ada827add27ae2186fdcc565b3dd2f99f76452
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017764"
---
# <a name="sysmailaddprofileaccountsp-transact-sql"></a>sysmail_add_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Agrega una cuenta del Correo electrónico de base de datos al perfil del Correo electrónico de base de datos. Ejecutar **sysmail_add_profileaccount_sp** después de crear una cuenta de base de datos con [sysmail_add_account_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md), y se crea un perfil de la base de datos con [sysmail_add_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sysmail_add_profileaccount_sp { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
    [ , [ @sequence_number = ] sequence_number ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @profile_id = ] profile_id` El identificador de perfil que se agrega la cuenta. *profile_id* es **int**, su valor predeterminado es null. Ya sea el *profile_id* o *profile_name* debe especificarse.  
  
`[ @profile_name = ] 'profile_name'` El nombre del perfil que se agrega la cuenta. *nombre_perfil* es **sysname**, su valor predeterminado es null. Ya sea el *profile_id* o *profile_name* debe especificarse.  
  
`[ @account_id = ] account_id` El identificador de cuenta para agregar al perfil. *account_id* es **int**, su valor predeterminado es null. Ya sea el *account_id* o *account_name* debe especificarse.  
  
`[ @account_name = ] 'account_name'` El nombre de la cuenta para agregar al perfil. *account_name* es **sysname**, su valor predeterminado es null. Ya sea el *account_id* o *account_name* debe especificarse.  
  
`[ @sequence_number = ] sequence_number` El número de secuencia de la cuenta en el perfil. *sequence_number* es **int**, no tiene ningún valor predeterminado. El número de secuencia determina el orden en que las cuentas se utilizan en el perfil.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 El perfil y la cuenta ya deben existir. En caso contrario, el procedimiento almacenado devuelve un error.  
  
 Tenga en cuenta que este procedimiento almacenado no cambia el número de secuencia de una cuenta asociada al perfil especificado. Para obtener más información acerca de cómo actualizar el número de secuencia de una cuenta, consulte [sysmail_update_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md).  
  
 El número de secuencia determina el orden en que el Correo electrónico de base de datos utiliza las cuentas en el perfil. En el caso de un mensaje de correo electrónico nuevo, el Correo electrónico de base de datos se inicia con la cuenta con el número de secuencia más bajo. Si la cuenta genera un error, el Correo electrónico de base de datos utiliza la cuenta con el siguiente número de secuencia superior y así sucesivamente hasta que el Correo electrónico de base de datos envía el mensaje correctamente o la cuenta con el número de secuencia superior genera un error. Si la cuenta con el número de secuencia superior genera un error, el Correo electrónico de base de datos pausa los intentos de envío del correo electrónico durante la cantidad de tiempo configurada en el parámetro *AccountRetryDelay* de **sysmail_configure_sp**y, después, inicia el proceso de nuevo intento de envío del correo electrónico comenzando por el número de secuencia más bajo. Use el parámetro *AccountRetryAttempts* de **sysmail_configure_sp**para configurar el número de veces que el proceso de correo electrónico externo intenta enviar el mensaje de correo electrónico con cada cuenta del perfil especificado.  
  
 Si existe más de una cuenta con el mismo número de secuencia, correo electrónico de base de datos solo usará una de esas cuentas para un mensaje de correo electrónico determinado. En este caso, el Correo electrónico de base de datos no confirma qué cuenta se va a usar para el número de secuencia o que se vaya a usar la misma cuenta de un mensaje a otro.  
  
 El procedimiento almacenado **sysmail_add_profileaccount_sp** está en el **msdb** de base de datos y que pertenece el **dbo** esquema. El procedimiento debe ejecutarse con un nombre de tres partes si la base de datos actual no es **msdb**.  
  
## <a name="permissions"></a>Permisos  
 Permisos de ejecución de este procedimiento de forma predeterminada a los miembros de la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se asocia el perfil `AdventureWorks Administrator` a la cuenta `Audit Account`. La cuenta de auditoría tiene el número de secuencia 1.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account',  
    @sequence_number = 1 ;  
```  
  
## <a name="see-also"></a>Vea también  
 [Correo electrónico de base de datos](../../relational-databases/database-mail/database-mail.md)   
 [Crear una cuenta de correo electrónico de base de datos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Objetos de configuración de correo electrónico de base de datos](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procedimientos almacenados de correo electrónico de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
