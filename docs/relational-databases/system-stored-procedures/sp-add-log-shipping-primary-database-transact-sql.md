---
title: sp_add_log_shipping_primary_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_primary_database
- sp_add_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_primary_database
ms.assetid: 69531611-113f-46b5-81a6-7bf496d0353c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5af11c14c7b0bf3b8e32d503c4b77e59623ce9ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140448"
---
# <a name="spaddlogshippingprimarydatabase-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Configura la base de datos principal de una configuración de trasvase de registros, incluido el trabajo de copia de seguridad, el registro de monitor local y el registro de monitor remoto.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_add_log_shipping_primary_database [ @database = ] 'database',   
[ @backup_directory = ] 'backup_directory',   
[ @backup_share = ] 'backup_share',   
[ @backup_job_name = ] 'backup_job_name',   
[, [ @backup_retention_period = ] backup_retention_period]  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] backup_threshold ]   
[, [ @threshold_alert = ] threshold_alert ]   
[, [ @threshold_alert_enabled = ] threshold_alert_enabled ]   
[, [ @history_retention_period = ] history_retention_period ]  
[, [ @backup_job_id = ] backup_job_id OUTPUT ]  
[, [ @primary_id = ] primary_id OUTPUT]  
[, [ @backup_compression = ] backup_compression_option ]  
  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @database = ] 'database'` Es el nombre de la base de datos principal de trasvase de registros. *base de datos* es **sysname**, no tiene ningún valor predeterminado, y no puede ser NULL.  
  
`[ @backup_directory = ] 'backup_directory'` Es la ruta de acceso a la carpeta de copia de seguridad en el servidor principal. *directorio_de_copia_de_seguridad* es **nvarchar (500)** , no tiene ningún valor predeterminado, y no puede ser NULL.  
  
`[ @backup_share = ] 'backup_share'` Es la ruta de acceso de red en el directorio de copia de seguridad en el servidor principal. *backup_share* es **nvarchar (500)** , no tiene ningún valor predeterminado, y no puede ser NULL.  
  
`[ @backup_job_name = ] 'backup_job_name'` Es el nombre del trabajo del Agente SQL Server en el servidor principal que guarda la copia de seguridad en la carpeta de copia de seguridad. *backup_job_name* es **sysname** y no puede ser NULL.  
  
`[ @backup_retention_period = ] backup_retention_period` Es el período de tiempo, en minutos, que se retiene el archivo de copia de seguridad de registro en el directorio de copia de seguridad en el servidor principal. *backup_retention_period* es **int**, no tiene ningún valor predeterminado, y no puede ser NULL.  
  
`[ @monitor_server = ] 'monitor_server'` Es el nombre del servidor de supervisión. *Monitor_server* es **sysname**, no tiene ningún valor predeterminado, y no puede ser NULL.  
  
`[ @monitor_server_security_mode = ] monitor_server_security_mode` Modo de seguridad utilizado para conectarse al servidor de supervisión.  
  
 1 = Autenticación de Windows.  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticación. *monitor_server_security_mode* es **bit** y no puede ser NULL.  
  
`[ @monitor_server_login = ] 'monitor_server_login'` Es el nombre de usuario de la cuenta utilizada para tener acceso el servidor de supervisión.  
  
`[ @monitor_server_password = ] 'monitor_server_password'` Es la contraseña de la cuenta utilizada para tener acceso el servidor de supervisión.  
  
`[ @backup_threshold = ] backup_threshold` Es el período de tiempo, en minutos, tras la última copia de seguridad antes de un *threshold_alert* se genera el error. *backup_threshold* es **int**, su valor predeterminado es de 60 minutos.  
  
`[ @threshold_alert = ] threshold_alert` Es la alerta que se genera cuando se supera el umbral de copia de seguridad. *threshold_alert* es **int**, su valor predeterminado es 14,420.  
  
`[ @threshold_alert_enabled = ] threshold_alert_enabled` Especifica si va a una alerta se genera cuando *backup_threshold* se supera. El valor cero (0), valor predeterminado, significa que la alerta está deshabilitada y no se generará. *threshold_alert_enabled* es **bits**.  
  
`[ @history_retention_period = ] history_retention_period` Es el período de tiempo en minutos en el que se retendrá el historial. *history_retention_period* es **int**, su valor predeterminado es null. Si se especifica ninguno, se usará un valor de 14420.  
  
`[ @backup_job_id = ] backup_job_id OUTPUT` El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Id. de trabajo de agente asociado con el trabajo de copia de seguridad en el servidor principal. *backup_job_id* es **uniqueidentifier** y no puede ser NULL.  
  
`[ @primary_id = ] primary_id OUTPUT` El identificador de la base de datos principal para la configuración de trasvase de registros. *primary_id* es **uniqueidentifier** y no puede ser NULL.  
  
`[ @backup_compression = ] backup_compression_option` Especifica si se usa una configuración de trasvase de registros [compresión de copia de seguridad](../../relational-databases/backup-restore/backup-compression-sql-server.md). Este parámetro solo se admite en [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (o una versión posterior).  
  
 0 = Deshabilitada. No se comprimen nunca las copias de seguridad de registros.  
  
 1 = Habilitada. Se comprimen siempre las copias de seguridad de registros.  
  
 2 = use el valor de la [ver o establecer la opción de configuración del servidor de compresión de copia de seguridad predeterminada](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md). Este es el valor predeterminado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentarios  
 **sp_add_log_shipping_primary_database** se debe ejecutar desde la **maestro** base de datos en el servidor principal. Este procedimiento almacenado realiza las siguientes funciones:  
  
1.  Genera un Id. principal y agrega una entrada para la base de datos principal en la tabla **log_shipping_primary_databases** utilizando los argumentos proporcionados.  
  
2.  Crea un trabajo de copia de seguridad para la base de datos principal que está deshabilitada.  
  
3.  Establece el identificador de trabajo de copia de seguridad el **log_shipping_primary_databases** entrada para el Id. de trabajo del trabajo de copia de seguridad.  
  
4.  Agrega un registro de supervisión local en la tabla **log_shipping_monitor_primary** en el servidor principal con los argumentos proporcionados.  
  
5.  Si el servidor de supervisión es diferente del servidor principal, agrega un registro de monitor en **log_shipping_monitor_primary** en el monitor de servidor con los argumentos proporcionados.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede ejecutar este procedimiento.  
  
## <a name="examples"></a>Ejemplos  
 En este ejemplo se agrega la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] como la base de datos principal en una configuración de trasvase de registros.  
  
```  
DECLARE @LS_BackupJobId AS uniqueidentifier ;  
DECLARE @LS_PrimaryId AS uniqueidentifier ;  
  
EXEC master.dbo.sp_add_log_shipping_primary_database   
@database = N'AdventureWorks'   
,@backup_directory = N'c:\lsbackup'   
,@backup_share = N'\\tribeca\lsbackup'   
,@backup_job_name = N'LSBackup_AdventureWorks'   
,@backup_retention_period = 1440  
,@monitor_server = N'rockaway'   
,@monitor_server_security_mode = 1   
,@backup_threshold = 60   
,@threshold_alert = 0   
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440   
,@backup_job_id = @LS_BackupJobId OUTPUT   
,@primary_id = @LS_PrimaryId OUTPUT   
,@overwrite = 1   
,@backup_compression = 0;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Acerca del trasvase de registros &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
