---
title: sys.dm_exec_distributed_requests (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 539bf6f6e4df5860977fdd0703a9bc11a5923d31
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contiene información sobre todas las solicitudes actualmente o que recientemente activas en las consultas de PolyBase. Muestra una fila por cada solicitud o consulta.  
  
 En función de la sesión y solicitar Id., un usuario puede recuperar, a continuación, las solicitudes distribuidas reales generadas para su ejecución: a través de sys.dm_exec_distributed_requests. Por ejemplo, una consulta que implicaría SQL normal y tablas externas de SQL se puede descomponer en varias instrucciones/solicitudes ejecutadas a través de los distintos nodos de proceso. Para realizar un seguimiento de los pasos distribuidos en todos los nodos de proceso, se introduce un identificador de ejecución 'global' que se puede usar para realizar el seguimiento de todas las operaciones en los nodos de ejecución asociadas a una solicitud determinada y el operador, respectivamente.  
  
|Nombre de la columna|Tipo de datos|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Clave para esta vista. Identificador numérico único asociado a la solicitud.|Único en todas las solicitudes en el sistema.|  
|execution_id|**nvarchar(32**|Identificador numérico único asociado a la sesión en el que se ejecute esta consulta.||  
|status|**nvarchar(32**|Estado actual de la solicitud.|'Pending', 'Authorizing', 'AcquireSystemResources', 'Initializing', 'Plan', 'Parsing', 'AquireResources', 'Running', 'Cancelling', 'Complete', 'Failed', 'Cancelled'.|  
|error_id|**nvarchar(36)**|Identificador único del error asociado a la solicitud, si lo hay.|Se establece en NULL si se ha producido ningún error.|  
|start_time|**datetime**|Hora en que se inició la ejecución de la solicitud.|0 para las solicitudes en cola; de lo contrario, válido datetime menor o igual a la hora actual.|  
|end_time|**datetime**|Hora en que completó el motor de compilación de la solicitud.|NULL para las solicitudes en cola o activas; en caso contrario, un valor datetime válido menor o igual a la hora actual.|  
|total_elapsed_time|**int**|Tiempo transcurrido en ejecución desde que se inició la solicitud, en milisegundos.|Entre 0 y la diferencia entre start_time y end_time. Si total_elapsed_time supera el valor máximo de un entero, continuará total_elapsed_time sea el valor máximo. Esta condición generará la advertencia "se superó el valor máximo." El valor máximo en milisegundos equivale a días 24,8.|  
  
## <a name="see-also"></a>Vea también  
 [PolyBase, solución de problemas con las vistas de administración dinámica](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Base de datos relacionadas con vistas de administración dinámica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
