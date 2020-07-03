---
title: Sys. Traces (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- traces
- sys.traces_TSQL
- sys.traces
- traces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.traces catalog view
ms.assetid: 4a03be22-b7da-4e2a-97ff-94bed890a620
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3f8edc61622c2748208a62d2bdaeb66650a78840
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897701"
---
# <a name="systraces-transact-sql"></a>sys.traces (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La vista de catálogo **Sys. Traces** contiene los seguimientos actuales en ejecución en el sistema. Esta vista está pensada como un reemplazo de la función **fn_trace_getinfo** .  
  
 Para obtener una lista completa de los eventos de seguimiento admitidos, vea [SQL Server referencia](../../relational-databases/event-classes/sql-server-event-class-reference.md)de la clase de eventos.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use vistas de catálogo de eventos extendidos en su lugar.  
  
|Nombre de la columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Id. de seguimiento.|  
|**status**|**int**|Estado de la seguimiento:<br /><br /> 0 = detenida<br /><br /> 1 = en ejecución|  
|**path**|**nvarchar(260)**|Ruta de acceso al archivo de seguimiento. Este valor es NULL se trata de una seguimiento de conjunto de filas.|  
|**max_size**|**bigint**|Tamaño máximo permitido del archivo de seguimiento, en megabytes (MB). Este valor es NULL se trata de una seguimiento de conjunto de filas.|  
|**stop_time**|**datetime**|Hora a la que se detiene la seguimiento en ejecución.|  
|**max_files**|**int**|Número máximo de archivos de sustitución incremental. Este valor es NULL si no se establece el número máximo.|  
|**is_rowset**|**bit**|1 = Seguimiento de conjunto de filas.|  
|**is_rollover**|**bit**|1 = La opción de sustitución incremental está habilitada.|  
|**is_shutdown**|**bit**|1 = La opción de cierre está habilitada.|  
|**is_default**|**bit**|1 = Seguimiento predeterminado.|  
|**buffer_count**|**int**|Número de búferes en memoria utilizados por la seguimiento.|  
|**buffer_size**|**int**|Tamaño de cada búfer (KB).|  
|**file_position**|**bigint**|Última posición del archivo de seguimiento. Este valor es NULL se trata de una seguimiento de conjunto de filas.|  
|**reader_spid**|**int**|Identificador de sesión del lector de seguimiento del conjunto de filas. Este valor es NULL cuando se trata de un seguimiento de archivo.|  
|**start_time**|**datetime**|Hora de inicio de la seguimiento.|  
|**last_event_time**|**datetime**|Hora en que se desencadenó el último evento.|  
|**event_count**|**bigint**|Número total de eventos que se han producido.|  
|**dropped_event_count**|**int**|Número total de eventos que se han quitado.|  
  
## <a name="permissions"></a>Permisos  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Consulte también  
 [Vistas de catálogo de objetos &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Sys. trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [Sys. trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [Sys. trace_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [Sys. trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [Sys. trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
