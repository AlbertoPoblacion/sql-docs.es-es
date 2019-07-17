---
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: dead5962987f7fb132f21bb4e3517f7cc9249601
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127648"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene información detallada, más allá de la información de adicional [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), acerca de la copia de seguridad en curso y finalizada y en las operaciones de restauración [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y acerca de en curso y completar la copia de seguridad, restauración y las operaciones de carga en [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. La información se conserva entre reinicios del sistema.  
  
|Nombre de la columna|Tipo de datos|Descripción|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificador único para una copia de seguridad específica o una restauración que se ejecute.<br /><br /> run_id y pdw_node_id forman la clave para esta vista.||  
|pdw_node_id|**int**|Identificador único de un nodo de dispositivo para el que este registro contiene información.<br /><br /> run_id y pdw_node_id forman la clave para esta vista.|Consulte node_id en [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|El estado actual de la ejecución.|'CANCELAR', 'COMPLETADO', 'ERROR', 'QUEUED', 'EJECUTANDO'|  
|start_time|**datetime**|Hora en que se inició la operación en este nodo concreto.||  
|end_time|**datetime**|Hora a la que finalizó la operación en este nodo concreto, si existe.||  
|total_elapsed_time|**int**|Tiempo total de que la operación se ha estado ejecutando en este nodo concreto.|Si total_elapsed_time supera el valor máximo de un entero (24,8 días en milisegundos), provocará el error de materialización debido al desbordamiento.<br /><br /> El valor máximo en milisegundos equivale a 24,8 días.|  
|Progreso|**int**|Progreso de la operación que se expresa como un porcentaje.|de 0 a 100|  
  
## <a name="see-also"></a>Vea también  
 [SQL Data Warehouse y vistas de catálogo del almacén de datos en paralelo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
