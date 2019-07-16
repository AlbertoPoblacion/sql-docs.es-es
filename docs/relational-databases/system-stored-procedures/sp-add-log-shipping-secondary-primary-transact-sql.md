---
title: sp_add_log_shipping_secondary_primary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_primary_TSQL
- sp_add_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_primary
ms.assetid: bfbbbee2-c255-4a59-a963-47d6e980a8e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: efbd753b40159afcca81b8922e8ef2842d22e5e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067718"
---
# <a name="spaddlogshippingsecondaryprimary-transact-sql"></a>sp_add_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Configura información principal, agrega vínculos al monitor local y remoto y crea trabajos de copia y restauración en el servidor secundario de la base de datos principal especificada.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_add_log_shipping_secondary_primary  
 [ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[ @backup_source_directory = ] 'backup_source_directory' ,   
[ @backup_destination_directory = ] 'backup_destination_directory'  
[ @copy_job_name = ] 'copy_job_name'  
[ @restore_job_name = ] 'restore_job_name'  
[, [ @file_retention_period = ] 'file_retention_period']  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @copy_job_id = ] 'copy_job_id' OUTPUT ]  
[, [ @restore_job_id = ] 'restore_job_id' OUTPUT ]  
[, [ @secondary_id = ] 'secondary_id' OUTPUT]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @primary_server = ] 'primary_server'` El nombre de la instancia principal de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] en la configuración de trasvase de registros. *primary_server* es **sysname** y no puede ser NULL.  
  
`[ @primary_database = ] 'primary_database'` Es el nombre de la base de datos en el servidor principal. *primary_database* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @backup_source_directory = ] 'backup_source_directory'` El directorio donde se almacenan los archivos de copia de seguridad del registro de transacciones desde el servidor principal. *backup_source_directory* es **nvarchar (500)** y no puede ser NULL.  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'` El directorio en el servidor secundario que se copiarán los archivos de copia de seguridad. *backup_destination_directory* es **nvarchar (500)** y no puede ser NULL.  
  
`[ @copy_job_name = ] 'copy_job_name'` El nombre que se usará para el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trabajo del agente que se va a crear para copiar las copias de seguridad del registro de transacciones en el servidor secundario. *copy_job_name* es **sysname** y no puede ser NULL.  
  
`[ @restore_job_name = ] 'restore_job_name'` Es el nombre de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trabajo del agente en el servidor secundario que restaura las copias de seguridad a la base de datos secundaria. *restore_job_name* es **sysname** y no puede ser NULL.  
  
`[ @file_retention_period = ] 'file_retention_period'` El período de tiempo, en minutos, que se conserva un archivo de copia de seguridad en el servidor secundario en la ruta de acceso especificada por el @backup_destination_directory parámetro antes de eliminarse. *history_retention_period* es **int**, su valor predeterminado es null. Si se especifica ninguno, se usará un valor de 14420.  
  
`[ @monitor_server = ] 'monitor_server'` Es el nombre del servidor de supervisión. *Monitor_server* es **sysname**, no tiene ningún valor predeterminado, y no puede ser NULL.  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'` Modo de seguridad utilizado para conectarse al servidor de supervisión.  
  
 1 = Autenticación de Windows.  
  
 0 = Autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *monitor_server_security_mode* es **bit** y no puede ser NULL.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` Es el nombre de usuario de la cuenta utilizada para tener acceso el servidor de supervisión.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` Es la contraseña de la cuenta utilizada para tener acceso el servidor de supervisión.  
  
`[ @copy_job_id = ] 'copy_job_id' OUTPUT` El identificador asociado con el trabajo de copia en el servidor secundario. *copy_job_id* es **uniqueidentifier** y no puede ser NULL.  
  
`[ @restore_job_id = ] 'restore_job_id' OUTPUT` El identificador asociado con el trabajo de restauración en el servidor secundario. *restore_job_id* es **uniqueidentifier** y no puede ser NULL.  
  
`[ @secondary_id = ] 'secondary_id' OUTPUT` El identificador para el servidor secundario en la configuración de trasvase de registros. *secondary_id* es **uniqueidentifier** y no puede ser NULL.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentarios  
 **sp_add_log_shipping_secondary_primary** se debe ejecutar desde la **maestro** base de datos en el servidor secundario. Este procedimiento almacenado hace lo siguiente:  
  
1.  Genera un Id. secundario para el servidor principal y la base de datos principal especificados.  
  
2.  ocurre lo siguiente:  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    1.  Agrega una entrada para el Id. secundario en **log_shipping_secondary** utilizando los argumentos proporcionados.  
  
    2.  Crea un trabajo de copia para el Id. secundario que está deshabilitado.  
  
    3.  Establece el identificador de trabajo de copia en el **log_shipping_secondary** entrada para el Id. de trabajo del trabajo de copia.  
  
    4.  Crea un trabajo de restauración para el Id. secundario que está deshabilitado.  
  
    5.  Establecer el Id. de trabajo de restauración en el **log_shipping_secondary** entrada para el Id. de trabajo del trabajo de restauración.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede ejecutar este procedimiento.  
  
## <a name="examples"></a>Ejemplos  
 En este ejemplo se muestra cómo utilizar el **sp_add_log_shipping_secondary_primary** procedimiento almacenado para configurar la información de la base de datos principal [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] en el servidor secundario.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_primary   
@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks'   
,@backup_source_directory = N'\\tribeca\LogShipping'   
,@backup_destination_directory = N''   
,@copy_job_name = N''   
,@restore_job_name = N''   
,@file_retention_period = 1440   
,@monitor_server = N'ROCKAWAY'   
,@monitor_server_security_mode = 1   
,@copy_job_id = @LS_Secondary__CopyJobId OUTPUT   
,@restore_job_id = @LS_Secondary__RestoreJobId OUTPUT   
,@secondary_id = @LS_Secondary__SecondaryId OUTPUT ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Acerca del trasvase de registros &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
