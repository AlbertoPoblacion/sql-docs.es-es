---
title: Sys.dm_db_session_space_usage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_session_space_usage_TSQL
- dm_db_session_space_usage
- sys.dm_db_session_space_usage
- sys.dm_db_session_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_session_space_usage dynamic management view
ms.assetid: a67a6045-8e14-460a-9fe3-912b846c08c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6cdb4a6077a91b36407c1faee050ad5b1ee38cbc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096259"
---
# <a name="sysdmdbsessionspaceusage-transact-sql"></a>sys.dm_db_session_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve el número de páginas asignadas y desasignadas por cada sesión en la base de datos.  
  
> [!NOTE]  
>  Esta vista sólo es aplicable a la [base de datos tempdb](../../relational-databases/databases/tempdb-database.md).  
  
> [!NOTE]  
>  Al llamarlo desde [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_db_session_space_usage**.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|Id. de sesión.<br /><br /> **session_id** se asigna a **session_id** en [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).|  
|**database_id**|**smallint**|Id. de la base de datos.|  
|**user_objects_alloc_page_count**|**bigint**|Número de páginas reservadas o asignadas por esta sesión para objetos de usuario.|  
|**user_objects_dealloc_page_count**|**bigint**|Número de páginas desasignadas y que ya no están reservadas por esta sesión para objetos de usuario.|  
|**internal_objects_alloc_page_count**|**bigint**|Número de páginas reservadas o asignadas por esta sesión para objetos internos.|  
|**internal_objects_dealloc_page_count**|**bigint**|Número de páginas desasignadas y que ya no están reservadas por esta sesión para objetos internos.|  
|**user_objects_deferred_dealloc_page_count**|**bigint**|Número de páginas que se han marcado para desasignación aplazada.<br /><br /> **Nota:** Introducido en service packs para [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] y [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].|  
|**pdw_node_id**|**int**|**Se aplica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> El identificador para el nodo en esta distribución.|  
  
## <a name="permissions"></a>Permisos  

En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requiere el permiso `VIEW DATABASE STATE` en la base de datos.   

## <a name="remarks"></a>Comentarios  
 Páginas IAM no incluidas en ninguno de los recuentos de asignación y desasignación comunicados por esta vista.  
  
 Los recuentos de páginas se inicializan a cero (0) en el inicio de una sesión. Los recuentos realizan el seguimiento del número total de páginas que se han asignado o desasignado para tareas que ya se han completado en la sesión. Los recuentos se actualizan solo cuando una tarea finaliza; no reflejan las tareas en ejecución.  
  
 Una sesión puede tener varias solicitudes activas simultáneamente. Una solicitud puede iniciar varios subprocesos, tareas, si está en una consulta paralela.  
  
 Para obtener más información acerca de las sesiones, solicitudes y tareas, consulte [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md), [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)y [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).  
  
## <a name="user-objects"></a>Objetos de usuario  
 Los objetos siguientes se incluyen en los contadores de páginas de objetos de usuario:  
  
-   Índices y tablas definidos por el usuario  
  
-   Índices y tablas del sistema  
  
-   Índices y tablas temporales globales  
  
-   Índices y tablas temporales locales  
  
-   Variables de tabla  
  
-   Tablas devueltas en las funciones con valores de tabla.  
  
## <a name="internal-objects"></a>Objetos internos  
 Objetos internos están sólo en **tempdb**. Los objetos siguientes se incluyen en los contadores de páginas de objetos internos:  
  
-   Tablas de trabajo para operaciones de cola o cursor y almacenamiento de objetos grandes (LOB) temporales  
  
-   Archivos de trabajo para operaciones como la combinación hash  
  
-   Ordenaciones  
  
## <a name="physical-joins"></a>Combinaciones físicas  
 ![Combinaciones físicas de sys.dm_db_session_space_usage](../../relational-databases/system-dynamic-management-views/media/join-dm-db-session-space-usage-1.gif "combinaciones físicas de sys.dm_db_session_space_usage")  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relación  
  
|De|En|Relación|  
|----------|--------|------------------|  
|dm_db_session_space_usage.session_id|dm_exec_sessions.session_id|Uno a uno|  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vistas de administración dinámica relacionadas con la base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  



