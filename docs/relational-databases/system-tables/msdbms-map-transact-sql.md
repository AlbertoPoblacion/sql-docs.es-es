---
title: MSdbms_map (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad9106bb9cde64953643e86bf81e72684858bd65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817121"
---
# <a name="msdbmsmap-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSdbms_map** tabla contiene información de tipo de datos de origen, así como un vínculo a información de tipo de datos de destino predeterminada para los pares DBMS de origen y destino. Esta tabla se almacena en el **msdb** de base de datos y se usa para publicaciones heterogéneas.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|Identifica de manera única una asignación de tipo de datos.|  
|**src_dbms_id**|**int**|Identifica el DBMS de origen especificando su **dbms_id** en el [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) tabla.|  
|**dest_dbms_id**|**int**|Identifica el DBMS de destino mediante la especificación de su **dbms_id** en el [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md) tabla.|  
|**src_datatype_id**|**int**|Identifica el **datatype_id** desde el [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md) tabla para el tipo de datos de origen.|  
|**src_len_min**|**bigint**|La longitud mínima del tipo de datos en el DBMS de origen, en la que un valor NULL indica que no se utiliza una longitud.|  
|**src_len_max**|**bigint**|La longitud máxima del tipo de datos en el DBMS de origen, en la que un valor NULL indica que no se utiliza una longitud.|  
|**src_prec_min**|**bigint**|La precisión mínima del tipo de datos en el DBMS de origen, en la que un valor NULL indica que no se utiliza una precisión.|  
|**src_prec_max**|**bigint**|La precisión máxima del tipo de datos en el DBMS de origen, en la que un valor NULL indica que no se utiliza una precisión.|  
|**src_scale_min**|**int**|La escala mínima del tipo de datos en el DBMS de origen, en la que un valor NULL indica que no se utiliza una escala.|  
|**src_scale_max**|**int**|La escala máxima del tipo de datos en el DBMS de origen, en la que un valor NULL indica que no se utiliza una escala.|  
|**src_nullable**|**bit**|Indica si la columna de destino en la asignación admite valores NULL, donde un valor NULL significa que no se requiere esta definición.|  
|**default_datatype_mapping_id**|**int**|Identifica la asignación de tipo de datos predeterminada especificando su **map_id** en tabla [MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md).|  
  
## <a name="see-also"></a>Vea también  
 [Replicación de bases de datos heterogéneas](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Especificar asignaciones de tipo de datos para un publicador de Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
