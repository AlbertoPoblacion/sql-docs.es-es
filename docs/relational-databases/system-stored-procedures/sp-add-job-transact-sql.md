---
title: sp_add_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
author: stevestein
ms.author: sstein
ms.openlocfilehash: 34cd282331a2f7bd8c0146d954b0ff76b7f42109
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941748"
---
# <a name="spaddjob-transact-sql"></a>sp_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Agrega un nuevo trabajo ejecutado por el servicio SQLServerAgent.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_add_job [ @job_name = ] 'job_name'  
     [ , [ @enabled = ] enabled ]   
     [ , [ @description = ] 'description' ]   
     [ , [ @start_step_id = ] step_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @category_id = ] category_id ]   
     [ , [ @owner_login_name = ] 'login' ]   
     [ , [ @notify_level_eventlog = ] eventlog_level ]   
     [ , [ @notify_level_email = ] email_level ]   
     [ , [ @notify_level_netsend = ] netsend_level ]   
     [ , [ @notify_level_page = ] page_level ]   
     [ , [ @notify_email_operator_name = ] 'email_name' ]   
          [ , [ @notify_netsend_operator_name = ] 'netsend_name' ]   
     [ , [ @notify_page_operator_name = ] 'page_name' ]   
     [ , [ @delete_level = ] delete_level ]   
     [ , [ @job_id = ] job_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Argumentos  
`[ @job_name = ] 'job_name'` El nombre del trabajo. El nombre debe ser único y no puede contener el porcentaje ( **%** ) caracteres. *job_name*es **nvarchar (128)** , no tiene ningún valor predeterminado.  
  
`[ @enabled = ] enabled` Indica el estado del trabajo agregado. *habilitado*es **tinyint**, su valor predeterminado es 1 (habilitado). Si **0**, el trabajo no está habilitado y no se ejecuta según la programación; sin embargo, se puede ejecutar manualmente.  
  
`[ @description = ] 'description'` La descripción del trabajo. *descripción* es **nvarchar (512)** , su valor predeterminado es null. Si *descripción* es se omite, se utiliza "No hay descripción disponible".  
  
`[ @start_step_id = ] step_id` El número de identificación del primer paso para ejecutar el trabajo. *step_id*es **int**, su valor predeterminado es 1.  
  
`[ @category_name = ] 'category'` La categoría del trabajo. *categoría*es **sysname**, su valor predeterminado es null.  
  
`[ @category_id = ] category_id` Un mecanismo independiente del idioma para especificar una categoría de trabajo. *category_id*es **int**, su valor predeterminado es null.  
  
`[ @owner_login_name = ] 'login'` El nombre del inicio de sesión que pertenece el trabajo. *inicio de sesión*es **sysname**, su valor predeterminado es null, que se interpreta como el nombre de inicio de sesión actual. Solo los miembros de la **sysadmin** rol fijo de servidor puede establecer o cambiar el valor de **@owner_login_name** . Si los usuarios que no son miembros de la **sysadmin** rol establecer o cambiar el valor de **@owner_login_name** , se produce un error en la ejecución de este procedimiento almacenado y devuelve un error.  
  
`[ @notify_level_eventlog = ] eventlog_level` Un valor que indica cuándo se debe incluir una entrada en el registro de aplicación de Microsoft Windows para este trabajo. *eventlog_level*es **int**, y puede tener uno de estos valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**0**|Nunca|  
|**1**|En caso de éxito|  
|**2** (predeterminado)|En caso de error|  
|**3**|Siempre|  
  
`[ @notify_level_email = ] email_level` Un valor que indica cuándo se debe enviar un correo electrónico tras finalizar este trabajo. *email_level*es **int**, su valor predeterminado es **0**, lo que no significa que nunca. *email_level*utiliza los mismos valores que *eventlog_level*.  
  
`[ @notify_level_netsend = ] netsend_level` Un valor que indica cuándo se debe enviar un mensaje de red tras finalizar este trabajo. *netsend_level*es **int**, su valor predeterminado es **0**, lo que no significa que nunca. *netsend_level* utiliza los mismos valores que *eventlog_level*.  
  
`[ @notify_level_page = ] page_level` Un valor que indica cuándo se debe enviar una página tras finalizar este trabajo. *page_level*es **int**, su valor predeterminado es **0**, lo que no significa que nunca. *page_level*utiliza los mismos valores que *eventlog_level*.  
  
`[ @notify_email_operator_name = ] 'email_name'` El nombre de correo electrónico de la persona para enviar correo electrónico cuando *email_level* se alcanza. *nombre de correo electrónico* es **sysname**, su valor predeterminado es null.  
  
`[ @notify_netsend_operator_name = ] 'netsend_name'` El nombre del operador al que se envía el mensaje de red al finalizar este trabajo. *netsend_name*es **sysname**, su valor predeterminado es null.  
  
`[ @notify_page_operator_name = ] 'page_name'` El nombre de la persona a la página tras finalizar este trabajo. *page_name*es **sysname**, su valor predeterminado es null.  
  
`[ @delete_level = ] delete_level` Un valor que indica cuándo se debe eliminar el trabajo. *delete_value*es **int**, su valor predeterminado es 0, lo que significa que nunca. *delete_level*utiliza los mismos valores que *eventlog_level*.  
  
> [!NOTE]  
>  Cuando *delete_level* es **3**, el trabajo se ejecuta solo una vez, independientemente de las programaciones definidas para el trabajo. Además, si un trabajo se elimina a sí mismo, también se elimina todo el historial de trabajos.  
  
`[ @job_id = ] _job_idOUTPUT` El número de identificación del trabajo asignado al trabajo si se creó correctamente. *job_id*es una variable de salida de tipo **uniqueidentifier**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentarios  
 **@originating_server** existe en **sp_add_job** pero no aparece en argumentos. **@originating_server** está reservado para uso interno.  
  
 Después de **sp_add_job** se ha ejecutado para agregar un trabajo, **sp_add_jobstep** puede usarse para agregar los pasos que realizan las actividades para el trabajo. **sp_add_jobschedule** se puede usar para crear la programación que el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servicio del agente se utiliza para ejecutar el trabajo. Use **sp_add_jobserver** para establecer el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia donde se ejecuta el trabajo, y **sp_delete_jobserver** para quitar el trabajo desde el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia.  
  
 Si el trabajo se ejecutará en uno o más servidores de destino en un entorno multiservidor, utilice **sp_apply_job_to_targets** para establecer los servidores de destino o grupos de servidores para el trabajo de destino. Para quitar trabajos de los servidores de destino o grupos de servidores de destino, utilice **sp_remove_job_from_targets**.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ofrece un método gráfico sencillo para administrar trabajos y es el método recomendado para crear y administrar la infraestructura de trabajo.  
  
## <a name="permissions"></a>Permisos  
 Para ejecutar este procedimiento almacenado, los usuarios deben ser un miembro de la **sysadmin** rol fijo de servidor, o debe concedérseles uno de los siguientes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente funciones fijas de base de datos, que residen en el **msdb** base de datos:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Para obtener información sobre los permisos específicos que están asociados con cada una de ellas se ha corregido, roles de base de datos, vea [Roles de base de datos fijos de SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede establecer o cambiar el valor de **@owner_login_name** . Si los usuarios que no son miembros de la **sysadmin** rol establecer o cambiar el valor de **@owner_login_name** , se produce un error en la ejecución de este procedimiento almacenado y devuelve un error.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-adding-a-job"></a>A. Agregar un trabajo  
 En este ejemplo se agrega un nuevo trabajo denominado `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-adding-a-job-with-pager-e-mail-and-net-send-information"></a>b. Agregar un trabajo con la información de buscapersonas, correo electrónico y net send  
 En este ejemplo se crea un trabajo denominado `Ad hoc Sales Data Backup` que notifica a `François Ajenstat` (por medio de un mensaje emergente de red, buscapersonas o correo electrónico) si se produce algún error, y se elimina el trabajo si éste se realiza correctamente.  
  
> [!NOTE]  
>  En este ejemplo se da por supuesto que ya existen un operador denominado `François Ajenstat` y un inicio de sesión denominado `françoisa`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'Ad hoc Sales Data Backup',   
    @enabled = 1,  
    @description = N'Ad hoc backup of sales data',  
    @owner_login_name = N'françoisa',  
    @notify_level_eventlog = 2,  
    @notify_level_email = 2,  
    @notify_level_netsend = 2,  
    @notify_level_page = 2,  
    @notify_email_operator_name = N'François Ajenstat',  
    @notify_netsend_operator_name = N'François Ajenstat',   
    @notify_page_operator_name = N'François Ajenstat',  
    @delete_level = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
