---
title: sp_notify_operator (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74558320df59414a756e1655bb073e9bf0d7d73c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107980"
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Envía un mensaje de correo electrónico a un operador mediante el Correo electrónico de base de datos.  
  
 
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @profile_name = ] 'profilename'` El nombre del perfil de correo electrónico de base de datos se utiliza para enviar el mensaje. *ProfileName* es **nvarchar (128)** . Si *profilename* no se especifica, se usa el perfil de correo electrónico de base de datos de forma predeterminada.  
  
`[ @id = ] id` El identificador del operador enviar el mensaje. *Id. de* es **int**, su valor predeterminado es null. Uno de *id* o *nombre* debe especificarse.  
  
`[ @name = ] 'name'` El nombre del operador para enviar el mensaje. *nombre* es **nvarchar (128)** , su valor predeterminado es null. Uno de *id* o *nombre* debe especificarse.  
  
> **NOTA:** Debe definirse una dirección de correo electrónico del operador antes de poder recibir mensajes.  
  
`[ @subject = ] 'subject'` El asunto del mensaje de correo electrónico. *asunto* es **nvarchar (256)** no tiene ningún valor predeterminado.  
  
`[ @body = ] 'message'` El cuerpo del mensaje de correo electrónico. *mensaje* es **nvarchar (max)** no tiene ningún valor predeterminado.  
  
`[ @file_attachments = ] 'attachment'` El nombre de un archivo para adjuntarlo al mensaje de correo electrónico. *datos adjuntos* es **nvarchar (512)** , no tiene ningún valor predeterminado.  
  
`[ @mail_database = ] 'mail_host_database'` Especifica el nombre de la base de datos de host de correo electrónico. *mail_host_database* es **nvarchar (128)** . Si no hay ningún *mail_host_database* se especifica, el **msdb** base de datos se usa de forma predeterminada.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 Envía el mensaje especificado a la dirección de correo electrónico del operador especificado. Si el operador no tiene configurada una dirección de correo electrónico, generará un error.  
  
 El Correo electrónico de base de datos y la base de datos host de correo deben configurarse antes de que se pueda enviar una notificación al operador.  
  
## <a name="permissions"></a>Permisos  
 De forma predeterminada, los miembros del rol fijo de servidor **sysadmin** pueden ejecutar este procedimiento almacenado. Al resto de usuarios se les debe conceder uno de los siguientes roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la base de datos **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Para detalles sobre los permisos de estos roles, consulte [Roles fijos de base de datos del Agente SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra cómo enviar una notificación de correo electrónico al operador `François Ajenstat` mediante el perfil de base de datos de correo electrónico de `AdventureWorks Administrator`. El asunto del mensaje de correo electrónico es `Test Notification`. El mensaje de correo electrónico indica que se trata de una notificación de prueba por correo electrónico.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del Agente SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
