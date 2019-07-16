---
title: sys.dm_db_xtp_index_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6e6370f4cbfcbc38478e562c3b74ff24ffde962f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026835"
---
# <a name="sysdmdbxtpindexstats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Contiene las estadísticas recopiladas desde el último reinicio de la base de datos.  
  
 Para obtener más información, consulte [OLTP en memoria &#40;optimización en memoria&#41; ](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md) y [directrices para utilizar índices en tablas optimizadas para memoria](https://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b).  

  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|Id. del objeto al que pertenece este índice.|  
|xtp_object_id|**bigint**|Id. interno correspondiente a la versión actual del objeto.<br /><br /> Nota: Se aplica a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|index_id|**bigint**|Id. del índice. El index_id es exclusivo solo dentro del objeto.|  
|scans_started|**bigint**|Número de recorridos de índice OLTP en memoria realizados. Cada selección, inserción, actualización o eliminación requiere un recorrido de índice.|  
|scans_retried|**bigint**|Número de recorridos de índice que tuvieron que reintentarse.|  
|rows_returned|**bigint**|Número de filas devueltas acumulado desde que se creó la tabla o desde el inicio de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_touched|**bigint**|Número acumulado de filas a las que se tuvo acceso desde que se creó la tabla o desde el inicio de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_expiring|**bigint**|Exclusivamente para uso interno.|  
|rows_expired|**bigint**|Exclusivamente para uso interno.|  
|rows_expired_removed|**bigint**|Exclusivamente para uso interno.|  
|phantom_scans_started|**bigint**|Exclusivamente para uso interno.|  
|phatom_scans_retries|**bigint**|Exclusivamente para uso interno.|  
|phantom_rows_touched|**bigint**|Exclusivamente para uso interno.|  
|phantom_expiring_rows_encountered|**bigint**|Exclusivamente para uso interno.|  
|phantom_expired_rows_encountered|**bigint**|Exclusivamente para uso interno.|  
|phantom_expired_removed_rows_encountered|**bigint**|Exclusivamente para uso interno.|  
|phantom_expired_rows_removed|**bigint**|Exclusivamente para uso interno.|  
|object_address|**varbinary(8)**|Exclusivamente para uso interno.|  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso VIEW DATABASE STATE en la base de datos actual.  
  
## <a name="see-also"></a>Vea también  
 [Vistas de administración dinámica de tabla optimizado para memoria &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
