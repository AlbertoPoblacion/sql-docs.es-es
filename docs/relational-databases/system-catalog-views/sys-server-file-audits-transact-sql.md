---
title: Sys.server_file_audits (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 04/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_file_audits_TSQL
- sys.server_file_audits_TSQL
- sys.server_file_audits
- server_file_audits
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_file_audits catalog view
ms.assetid: 553288a0-be57-4d79-ae53-b7cbd065e127
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42a00870788129a007511766ea8b2a87ef73740d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverfileaudits-transact-sql"></a>sys.server_file_audits (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene información adicional sobre el tipo de auditoría de archivos en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una instancia del servidor de auditoría. Para obtener más información, vea [SQL Server Audit &#40;motor de base de datos&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|audit_id|**int**|Identificador de la auditoría.|  
|name|**sysname**|Nombre de la auditoría.|  
|audit_guid|**uniqueidentifier**|GUID de la auditoría.|  
|create_date|**datetime**|Fecha UTC en la que se creó la auditoría de archivos.|  
|modify_date|**DateTime**|Fecha UTC en la que se modificó por última vez la auditoría de archivos.|  
|principal_id|**int**|Identificador del propietario de la auditoría tal y como se registró en el servidor.|  
|Tipo|**Char(2)**|Tipo de auditoría:<br /><br /> 0 = Registro de eventos de seguridad de NT<br /><br /> 1 = Registro de eventos de aplicación de NT<br /><br /> 2 = Archivo del sistema de archivos|  
|type_desc|**nvarchar (60)**|Descripción del tipo de auditoría.|  
|on_failure|**tinyint**|Condición en caso de error:<br /><br /> 0 = Continuar<br /><br /> 1 = Cerrar la instancia del servidor<br /><br /> 2 = Error en la operación|  
|on_failure_desc|**nvarchar (60)**|En caso de error escribir una entrada de acción:<br /><br /> CONTINUE<br /><br /> SHUTDOWN SERVER INSTANCE<br /><br /> FAIL OPERATION|  
|is_state_enabled|**tinyint**|0 = Deshabilitado<br /><br /> 1 = Habilitado|  
|queue_delay|**int**|Tiempo máximo sugerido, en milisegundos, que debe transcurrir antes de realizar la escritura en disco. Si es igual a 0, la auditoría garantizará la escritura antes de que continúe el evento.|  
|predicate|**nvarchar(8000)**|Expresión de predicado aplicada al evento.|  
|max_file_size|**bigint**|Tamaño máximo de la auditoría, expresado en megabytes:<br /><br /> 0 = Ilimitado o no aplicable al tipo de auditoría seleccionada.|  
|max_rollover_files|**int**|Número máximo de archivos que se van a utilizar con la opción de sustitución incremental.|  
|max_files|**int**|Número máximo de archivos que se van a utilizar sin la opción de sustitución incremental.|  
|reserved_disk_space|**int**|Cantidad de espacio en disco que se debe reservar para cada archivo.|  
|log_file_path|**nvarchar (260)**|Ruta de acceso a la auditoría. Para auditorías de archivos, la ruta de acceso del archivo; para auditorías de registro de la aplicación, la ruta de acceso del registro de la aplicación.|  
|log_file_name|**nvarchar (260)**|Nombre base para el archivo de registro proporcionado en la instrucción DDL CREATE AUDIT. Se agrega un número incremental al archivo base_log_name como un sufijo para crear el nombre del archivo de registro.|  
  
## <a name="permissions"></a>Permissions  
 Entidades de seguridad con la **ALTER ANY SERVER AUDIT** o **VIEW ANY DEFINITION** permiso tiene acceso a esta vista de catálogo. Además, la entidad de seguridad no se debe denegar **VIEW ANY DEFINITION** permiso.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [CREATE SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREAR especificación de auditoría de servidor &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREAR especificación de auditoría de base de datos &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [QUITE la especificación de auditoría de base de datos &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys.server_file_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [Sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys.database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [Sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Sys.dm_audit_class_type_map &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Crear una auditoría de servidor y una especificación de auditoría de servidor](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
