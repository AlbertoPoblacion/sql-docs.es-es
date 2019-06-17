---
title: sys.dm_os_memory_brokers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_brokers
- dm_os_memory_brokers_TSQL
- sys.dm_os_memory_brokers_TSQL
- dm_os_memory_brokers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_brokers dynamic management view
ms.assetid: 48dd6ad9-0d36-4370-8a12-4921d0df4b86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3e8545fe1d612991eb79a7e75e896089b525a996
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047136"
---
# <a name="sysdmosmemorybrokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Las asignaciones internas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizan el administrador de memoria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Seguimiento de la diferencia entre los contadores de memoria de proceso de **sys.dm_os_process_memory** y los contadores internos pueden indicar el uso de memoria de los componentes externos en el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] espacio de memoria.  
  
 Los agentes de memoria distribuyen equitativamente las asignaciones de memoria entre varios componentes dentro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en función del uso actual y previsto. Los agentes de memoria no realizan las asignaciones. Solo realizan el seguimiento de las asignaciones para calcular la distribución.  
  
 La tabla siguiente proporciona información sobre los agentes de memoria.  
  
> [!NOTE]  
>  Al llamarlo desde [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_os_memory_brokers**.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|Id. del grupo de recursos de servidor si está asociado a un grupo del regulador de recursos.|  
|**memory_broker_type**|**nvarchar(60)**|Tipo de agente de memoria. Actualmente hay tres tipos de agentes de memoria en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], que aparece a continuación con sus descripciones.<br /><br /> **MEMORYBROKER_FOR_CACHE** : Memoria asignada para su uso por los objetos en caché (caché de grupo de búferes no).<br /><br /> **MEMORYBROKER_FOR_STEAL** : Memoria descartada del grupo de búferes. Esta memoria no está disponible para ser reutilizada por otros componentes hasta que el propietario actual la libere.<br /><br /> **MEMORYBROKER_FOR_RESERVE** : Memoria reservada para uso futuro en las solicitudes en ejecución.|  
|**allocations_kb**|**bigint**|La cantidad de memoria, en kilobytes (KB) asignada a este tipo de agente.|  
|**allocations_kb_per_sec**|**bigint**|La tasa de asignaciones de memoria en kilobytes (KB) por segundo. Este valor puede ser negativo para las cancelaciones de asignación de memoria.|  
|**predicted_allocations_kb**|**bigint**|La cantidad prevista de memoria asignada por el agente. Depende del modelo de uso de la memoria.|  
|**target_allocations_kb**|**bigint**|La cantidad recomendada de memoria asignada, en kilobytes (KB), depende de la configuración actual y del modelo de uso de la memoria. El agente debería aumentar o disminuir hasta este número.|  
|**future_allocations_kb**|**bigint**|El número previsto de asignaciones, en kilobytes (KB), que se realizarán en los segundos siguientes.|  
|**overall_limit_kb**|**bigint**|Cantidad máxima de memoria, en kilobytes (KB), que puede asignar el agente.|  
|**last_notification**|**nvarchar(60)**|Recomendación del uso de memoria, que depende de la configuración actual y del modelo de uso. Los valores válidos son los siguientes:<br /><br /> grow<br /><br /> shrink<br /><br /> stable|  
|**pdw_node_id**|**int**|**Se aplica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> El identificador para el nodo en esta distribución.|  
  
## <a name="permissions"></a>Permisos  

En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requiere el `VIEW DATABASE STATE` permiso en la base de datos.   
  
## <a name="see-also"></a>Vea también  

  [Vistas de administración dinámica relacionadas con el sistema operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


