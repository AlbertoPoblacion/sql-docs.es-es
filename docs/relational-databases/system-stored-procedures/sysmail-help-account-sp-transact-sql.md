---
title: sysmail_help_account_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b5f416d1f2989cd9392ecac0279e792477cca8d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909183"
---
# <a name="sysmailhelpaccountsp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Muestra información (excepto contraseñas) sobre las cuentas del Correo electrónico de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @account_id = ] account_id` El identificador de la cuenta que se muestra información de cuenta. *account_id* es **int**, su valor predeterminado es null.  
  
`[ @account_name = ] 'account_name'` El nombre de la cuenta que se muestra información. *account_name* es **sysname**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Devuelve un conjunto de resultados que contiene las columnas que se indican a continuación.  
  
||||  
|-|-|-|  
|Nombre de columna|Tipo de datos|Descripción|  
|**account_id**|**int**|Id. de la cuenta.|  
|**name**|**sysname**|El nombre de la cuenta.|  
|**description**|**nvarchar(256)**|Descripción de la cuenta.|  
|**email_address**|**nvarchar(128)**|Dirección de correo electrónico desde la que se envían los mensajes.|  
|**display_name**|**nvarchar(128)**|El nombre para mostrar de la cuenta.|  
|**replyto_address**|**nvarchar(128)**|La dirección donde se envían las respuestas a mensajes desde esta cuenta.|  
|**servertype**|**sysname**|Tipo de servidor de correo electrónico para la cuenta.|  
|**servername**|**sysname**|Nombre del servidor de correo electrónico para la cuenta.|  
|**port**|**int**|Número de puerto que utiliza el servidor de correo electrónico.|  
|**username**|**nvarchar(128)**|Nombre de usuario que se utiliza para iniciar sesión en el servidor de correo electrónico si éste utiliza autenticación. Cuando **username** es NULL, correo electrónico de base de datos no utiliza la autenticación para esta cuenta.|  
|**use_default_credentials**|**bit**|Especifica si se debe enviar el correo al servidor SMTP con las credenciales de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** es de tipo bit, no tiene ningún valor predeterminado. Si el valor de este parámetro es 1, el Correo electrónico de base de datos utiliza las credenciales del servicio [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Cuando este parámetro es 0, el correo electrónico de base de datos utiliza el **@username** y **@password** para la autenticación en el servidor SMTP. Si **@username** y **@password** son NULL, el correo electrónico de base de datos utiliza la autenticación anónima. Consulte al administrador de SMTP antes de especificar este parámetro.|  
|**enable_ssl**|**bit**|Especifica si el Correo electrónico de base de datos cifra la comunicación mediante Capa de sockets seguros (SSL). Utilice esta opción si se requiere SSL en el servidor SMTP. **enable_ssl** es de tipo bit, no tiene ningún valor predeterminado. El valor 1 indica que el Correo electrónico de base de datos cifra la comunicación mediante SSL. El valor 0 indica que el Correo electrónico de base de datos envía el correo sin cifrado SSL.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando no hay ninguna *account_id* o *account_name* se proporciona, **sysmail_help_account** muestra información en todas las cuentas de correo electrónico de base de datos en la instancia de Microsoft SQL Server.  
  
 El procedimiento almacenado **sysmail_help_account_sp** está en el **msdb** de base de datos y que pertenece el **dbo** esquema. El procedimiento debe ejecutarse con un nombre de tres partes si la base de datos actual no es **msdb**.  
  
## <a name="permissions"></a>Permisos  
 Permisos de ejecución de este procedimiento de forma predeterminada a los miembros de la **sysadmin** rol fijo de servidor.  
  
## <a name="examples"></a>Ejemplos  
 **A. Mostrar información para todas las cuentas**  
  
 En el siguiente ejemplo se muestra la información de cuenta para todas las cuentas de la instancia.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 El siguiente es un conjunto de resultados de ejemplo con la longitud de línea editada:  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B. Mostrar información para una cuenta específica**  
  
 En el siguiente ejemplo se muestra la información de cuenta para la cuenta llamada `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 El siguiente es un conjunto de resultados de ejemplo con la longitud de línea editada:  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>Vea también  
 [Correo electrónico de base de datos](../../relational-databases/database-mail/database-mail.md)   
 [Crear una cuenta de correo electrónico de base de datos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Procedimientos almacenados de correo electrónico de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
