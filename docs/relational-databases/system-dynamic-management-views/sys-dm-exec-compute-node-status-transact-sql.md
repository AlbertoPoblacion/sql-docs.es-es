---
title: Sys. dm_exec_compute_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 11883f7744aad3f8d483e808922a7170c8fe5391
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532760"
---
# <a name="sysdm_exec_compute_node_status-transact-sql"></a>sys.dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contiene información adicional sobre el rendimiento y el estado de todos los nodos de polybase. Muestra una fila por nodo.  
  
|Column Name|Tipo de datos|Descripción|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|`int`|Identificador numérico único asociado al nodo.|Único en todo el clúster de escalado horizontal, independientemente del tipo.|  
|process_id|`int`|||  
|process_name|`nvarchar(255)`|Nombre lógico del nodo.|Cualquier cadena de longitud adecuada.|  
|allocated_memory|`bigint`|Memoria total asignada en este nodo.||  
|available_memory|`bigint`|Memoria total disponible en este nodo.||  
|process_cpu_usage|`bigint`|Uso total de la CPU del proceso, en pasos.||  
|total_cpu_usage|`bigint`|Uso total de CPU, en pasos.||  
|thread_count|`bigint`|Número total de subprocesos en uso en este nodo.||  
|handle_count|`bigint`|Número total de identificadores en uso en este nodo.||  
|total_elapsed_time|`bigint`|Tiempo total transcurrido desde el inicio o el reinicio del sistema.|Tiempo total transcurrido desde el inicio o el reinicio del sistema. Si total_elapsed_time supera el valor máximo de un entero (24,8 días en milisegundos), se producirá un error de materialización debido al desbordamiento. El valor máximo en milisegundos es equivalente a 24,8 días.|  
|is_available|`bit`|Marca que indica si este nodo está disponible.||  
|sent_time|`datetime`|Última vez que envió un paquete de red||  
|received_time|`datetime`|Última vez que este nodo envió un paquete de red.||  
|error_id|`nvarchar(36)`|Identificador único del último error que se produjo en este nodo.||
|compute_pool_id|`int`|Identificador único para el grupo.|

## <a name="see-also"></a>Vea también  
 [Solución de problemas de polybase con vistas de administración dinámica](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vistas &#40;de administración dinámica relacionadas con bases de datos TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
