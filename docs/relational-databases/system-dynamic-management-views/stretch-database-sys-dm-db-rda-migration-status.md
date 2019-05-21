---
title: sys.dm_db_rda_migration_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 257d83e522b398cce8358c1e30f4966dd951739e
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945452"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - sys.dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contiene una fila por cada lote de los datos migrados desde cada tabla habilitada para Stretch en la instancia local de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los lotes se identifican mediante su hora de inicio y la hora de finalización.  
  
 **Sys.dm_db_rda_migration_status** tiene como ámbito el contexto de base de datos actual. Asegúrese de que se encuentra en el contexto de base de datos de las tablas de habilitar Stretch para el que desea ver el estado de la migración.  
  
 En [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], la salida de **sys.dm_db_rda_migration_status** está limitada a 200 filas.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|El identificador de la tabla desde el que se migraron las filas.|  
|**database_id**|**int**|El identificador de la base de datos desde el que se migraron las filas.|  
|**migrated_rows**|**bigint**|El número de filas migradas en este lote.|  
|**start_time_utc**|**datetime**|La hora UTC en que se inició el lote.|  
|**end_time_utc**|**datetime**|La hora UTC en que finalizó el lote.|  
|**error_number**|**int**|Si se produce un error en el lote, el número de error del error producido; en caso contrario, es null.|  
|**error_severity**|**int**|Si se produce un error en el lote, la gravedad del error producido; en caso contrario, es null.|  
|**error_state**|**int**|Si se produce un error en el lote, el estado del error producido; en caso contrario, es null.<br /><br /> El **error_state** indica la condición o la ubicación donde se produjo el error.|  
  
## <a name="see-also"></a>Vea también  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
