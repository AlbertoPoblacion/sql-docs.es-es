---
title: sysmail_delete_mailitems_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_mailitems_sp_TSQL
- sysmail_delete_mailitems_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_mailitems_sp
ms.assetid: f87c9f4a-bda1-4bce-84b2-a055a3229ecd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23ecda5fd8d91f20133eb2295d38dc9d9ace66f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069100"
---
# <a name="sysmaildeletemailitemssp-transact-sql"></a>sysmail_delete_mailitems_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina de forma permanente los mensajes de correo electrónico de las tablas internas del Correo electrónico de base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sysmail_delete_mailitems_sp  [ [ @sent_before = ] 'sent_before' ]  
    [ , [ @sent_status = ] 'sent_status' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @sent_before = ] 'sent_before'` Elimina mensajes de correo electrónico hasta la fecha y hora especificadas por el *sent_before* argumento. *sent_before* es **datetime** con NULL como valor predeterminado. NULL indica todas las fechas.  
  
`[ @sent_status = ] 'sent_status'` Elimina mensajes de correo electrónico del tipo especificado por *sent_status*. *sent_status* es **varchar (8)** no tiene ningún valor predeterminado. Las entradas válidas son **envía**, **sin enviar**, **reintentando**, y **no se pudo**. NULL indica todos los estados.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 Mensajes de correo electrónico de base de datos y sus datos adjuntos se almacenan en el **msdb** base de datos. Los mensajes se deben eliminar periódicamente para evitar **msdb** crezca mayor de lo esperado y para cumplir con el programa de retención de documentos de las organizaciones. Use la **sysmail_delete_mailitems_sp** procedimiento almacenado para eliminar permanentemente los mensajes de correo electrónico de las tablas del correo electrónico de base de datos. Un argumento opcional permite eliminar solo los mensajes de correo electrónico antiguos indicando la fecha y la hora. Se eliminarán los mensajes de correo electrónico anteriores al valor de ese argumento. Otro argumento opcional permite eliminar solo los correos electrónicos de un tipo determinado, especificado como el **sent_status** argumento. Debe proporcionar un argumento para **@sent_before** o **@sent_status** . Para eliminar todos los mensajes, utilice  **@sent_before = getdate()** .  
  
 Si se eliminan mensajes de correo electrónico, se eliminarán también los archivos adjuntos relacionados con los mismos. Eliminación de correo electrónico no elimina las entradas correspondientes en **sysmail_event_log**. Use [sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md) para eliminar elementos del registro.  
  
## <a name="permissions"></a>Permisos  
 De forma predeterminada, este procedimiento almacenado se concede para la ejecución a los miembros de desactivar el **sysadmin** rol fijo de servidor y **DatabaseMailUserRole**. Los miembros de la **sysadmin** rol fijo de servidor puede ejecutar este procedimiento para eliminar los correos electrónicos enviados por todos los usuarios. Los miembros de **DatabaseMailUserRole** solo se puede eliminar los correos electrónicos enviados por ese usuario.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-deleting-all-e-mails"></a>A. Eliminar todos los mensajes de correo electrónico  
 En el ejemplo siguiente se eliminan todos los mensajes de correo electrónico del sistema del Correo electrónico de base de datos.  
  
```  
DECLARE @GETDATE datetime  
SET @GETDATE = GETDATE();  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @GETDATE;  
GO  
```  
  
### <a name="b-deleting-the-oldest-e-mails"></a>b. Eliminar los mensajes de correo electrónico más antiguos  
 En el ejemplo siguiente se eliminan los mensajes de correo electrónico del registro del Correo electrónico de base de datos anteriores a la fecha `October 9, 2005`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-e-mails-of-a-certain-type"></a>C. Eliminar todos los mensajes de correo electrónico de un tipo determinado  
 En el ejemplo siguiente se eliminan todos los mensajes de correo electrónico con errores del registro del Correo electrónico de base de datos.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_status = 'failed' ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_event_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_mailattachments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)   
 [Crear un trabajo del Agente SQL Server para archivar mensajes y registros de eventos del Correo electrónico de base de datos](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
