---
title: sp_update_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5428ae9130646db662c6c960f777c6a7dfe25000
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084891"
---
# <a name="spupdatejob-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia los atributos de un trabajo.  
  

  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @job_id = ] job_id` El número de identificación del trabajo que se puede actualizar. *job_id*es **uniqueidentifier**.  
  
`[ @job_name = ] 'job_name'` El nombre del trabajo. *job_name* es **nvarchar (128)** .  
  
> **NOTA:** Cualquier *job_id* o *job_name* debe especificarse, pero no se pueden especificar ambos.  
  
`[ @new_name = ] 'new_name'` El nuevo nombre para el trabajo. *new_name* es **nvarchar (128)** .  
  
`[ @enabled = ] enabled` Especifica si el trabajo está habilitado (**1**) o no habilitada (**0**). *habilitado* es **tinyint**.  
  
`[ @description = ] 'description'` La descripción del trabajo. *descripción* es **nvarchar (512)** .  
  
`[ @start_step_id = ] step_id` El número de identificación del primer paso para ejecutar el trabajo. *step_id* es **int**.  
  
`[ @category_name = ] 'category'` La categoría del trabajo. *categoría* es **nvarchar (128)** .  
  
`[ @owner_login_name = ] 'login'` El nombre del inicio de sesión que pertenece el trabajo. *inicio de sesión* es **nvarchar (128)** sólo los miembros de la **sysadmin** rol fijo de servidor puede cambiar la propiedad de un trabajo.  
  
`[ @notify_level_eventlog = ] eventlog_level` Especifica cuándo se debe incluir una entrada en el registro de aplicación de Microsoft Windows para este trabajo. *eventlog_level*es **int**, y puede tener uno de estos valores.  
  
|Valor|Descripción (acción)|  
|-----------|----------------------------|  
|**0**|Nunca|  
|**1**|En caso de éxito|  
|**2**|En caso de error|  
|**3**|Siempre|  
  
`[ @notify_level_email = ] email_level` Especifica cuándo se debe enviar un correo electrónico tras finalizar este trabajo. *email_level*es **int**. *email_level*utiliza los mismos valores que *eventlog_level*.  
  
`[ @notify_level_netsend = ] netsend_level` Especifica cuándo se debe enviar un mensaje de red tras finalizar este trabajo. *netsend_level*es **int**. *netsend_level*utiliza los mismos valores que *eventlog_level*.  
  
`[ @notify_level_page = ] page_level` Especifica cuándo se debe enviar una página tras finalizar este trabajo. *page_level* es **int**. *page_level*utiliza los mismos valores que *eventlog_level*.  
  
`[ @notify_email_operator_name = ] 'operator_name'` El nombre del operador al que se envía el correo electrónico cuando *email_level* se alcanza. *nombre de correo electrónico* es **nvarchar (128)** .  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` El nombre del operador al que se envía el mensaje de red. *netsend_operator* es **nvarchar (128)** .  
  
`[ @notify_page_operator_name = ] 'page_operator'` El nombre del operador al que se envía una página. *page_operator* es **nvarchar (128)** .  
  
`[ @delete_level = ] delete_level` Especifica cuándo se debe eliminar el trabajo. *delete_value*es **int**. *delete_level*utiliza los mismos valores que *eventlog_level*.  
  
`[ @automatic_post = ] automatic_post` Reservado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_update_job** se debe ejecutar desde la **msdb** base de datos.  
  
 **sp_update_job** solo cambia las opciones de parámetro que se proporcionan los valores. Si se omite un parámetro, se conserva la configuración actual.  
  
## <a name="permissions"></a>Permisos  
 De forma predeterminada, los miembros del rol fijo de servidor **sysadmin** pueden ejecutar este procedimiento almacenado. Al resto de usuarios se les debe conceder uno de los siguientes roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la base de datos **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Para detalles sobre los permisos de estos roles, consulte [Roles fijos de base de datos del Agente SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Solo los miembros del **sysadmin** puede usar este procedimiento almacenado para editar los atributos de los trabajos que pertenecen a otros usuarios.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se cambia el nombre, la descripción y el estado de habilitación del trabajo `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
