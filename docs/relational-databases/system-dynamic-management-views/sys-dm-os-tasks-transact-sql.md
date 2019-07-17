---
title: sys.dm_os_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e71af56ba845cc2b011196fadce6d7c1a3684b15
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265648"
---
# <a name="sysdmostasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve una fila por cada tarea activa en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Al llamarlo desde [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_os_tasks**.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Dirección de memoria del objeto.|  
|**task_state**|**nvarchar(60)**|Estado de la tarea. Puede ser uno de los siguientes:<br /><br /> PENDIENTE: Esperando un subproceso de trabajo.<br /><br /> PUEDE EJECUTAR: Runnable, pero se espera recibir un cuanto.<br /><br /> EJECUTANDO: Ejecutándose actualmente en el programador.<br /><br /> SUSPENDIDO: Tiene un trabajador, pero está esperando un evento.<br /><br /> HECHO: Puede completar.<br /><br /> SPINLOOP: Atrapado en un subproceso.|  
|**context_switches_count**|**int**|Número de cambios de contexto del programador que esta tarea ha completado.|  
|**pending_io_count**|**int**|Número de entradas y salidas físicas realizadas por esta tarea.|  
|**pending_io_byte_count**|**bigint**|Recuento total de bytes de las entradas y salidas realizadas por esta tarea.|  
|**pending_io_byte_average**|**int**|Recuento promedio de bytes de las entradas y salidas realizadas por esta tarea.|  
|**scheduler_id**|**int**|Id. del programador primario. Es un identificador de la información del programador para esta tarea. Para obtener más información, consulte [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|Id. de la sesión que está asociada a la tarea.|  
|**exec_context_id**|**int**|Id. del contexto de ejecución que está asociado a la tarea.|  
|**request_id**|**int**|Id. de la solicitud de la tarea. Para obtener más información, consulte [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Dirección de memoria del trabajador que ejecuta la tarea.<br /><br /> NULL = La tarea espera un trabajador que pueda ejecutarla o la tarea acaba de finalizar la ejecución.<br /><br /> Para obtener más información, consulte [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Dirección de memoria del host.<br /><br /> 0 = No se ha usado el hospedaje para crear la tarea. Esto ayuda a identificar el host que se ha utilizado para crear esta tarea.<br /><br /> Para obtener más información, consulte [sys.dm_os_hosts &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Dirección de memoria de la tarea que es el elemento primario del objeto.|  
|**pdw_node_id**|**int**|**Se aplica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> El identificador para el nodo en esta distribución.|  
  
## <a name="permissions"></a>Permisos

En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] los niveles Premium, requieren el `VIEW DATABASE STATE` permiso en la base de datos. En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveles estándar y básico, requiere el **administrador del servidor** o un **Administrador de Azure Active Directory** cuenta.   

## <a name="examples"></a>Ejemplos  
  
### <a name="a-monitoring-parallel-requests"></a>A. Supervisar solicitudes paralelas  
 Para las solicitudes que se ejecutan en paralelo, verá varias filas para la misma combinación de (\<**session_id**>, \< **request_id**>). Use la siguiente consulta para buscar el [configurar la max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) para todas las solicitudes activas.  
  
> [!NOTE]  
>  Un **request_id** es único dentro de una sesión.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>b. Asociar identificadores de sesión con subprocesos de Windows  
 Puede utilizar la siguiente consulta para asociar un valor de identificador de sesión a un identificador de subproceso de Windows. A continuación, puede supervisar el rendimiento del subproceso en el Monitor de rendimiento de Windows. La siguiente consulta no devuelve información para sesiones en espera.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
  [Vistas de administración dinámica relacionadas con el sistema operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


