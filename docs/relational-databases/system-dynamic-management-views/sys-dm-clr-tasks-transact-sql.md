---
title: sys.dm_clr_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b1386f34ad1ae82229729e9db696c95176c43aa9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742081"
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve una fila de todas las tareas CLR (Common Language Runtime) que se están ejecutando actualmente. Un lote de [!INCLUDE[tsql](../../includes/tsql-md.md)] que contiene una referencia a una rutina CLR crea una tarea independiente para la ejecución de todo el código administrado en ese lote. Muchas instrucciones del lote que requieren la ejecución del código administrado utilizan la misma tarea CLR. La tarea CLR es responsable del mantenimiento de objetos y el estado relativo a la ejecución de código administrado y también de las transacciones entre la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y CLR.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Dirección de la tarea CLR.|  
|**sos_task_address**|**varbinary(8)**|Dirección de la tarea del lote [!INCLUDE[tsql](../../includes/tsql-md.md)] subyacente.|  
|**appdomain_address**|**varbinary(8)**|Dirección del dominio de la aplicación en la que se ejecuta esta tarea.|  
|**state**|**nvarchar(128)**|Estado actual de la tarea.|  
|**abort_state**|**nvarchar(128)**|Estado en el que está actualmente la cancelación (si la tarea se ha cancelado). Hay varios estados implicados en la anulación de tareas.|  
|**Tipo**|**nvarchar(128)**|Tipo de tarea.|  
|**affinity_count**|**int**|Afinidad de la tarea.|  
|**forced_yield_count**|**int**|Número de veces que se forzó a la tarea a producir.|  
  
## <a name="permissions"></a>Permisos  

En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requiere el `VIEW DATABASE STATE` permiso en la base de datos.   
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vistas de administración dinámica relacionadas con el Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

