---
title: MSmerge_contents (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4be6cffcc7e4f13b88d8037b53d438d604b9650
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089943"
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSmerge_contents** tabla contiene una fila por cada fila modificada en la base de datos actual desde que se publicó. El proceso de mezcla utiliza esta tabla para determinar las filas que han cambiado. Esta tabla se almacena en las bases de datos de publicación y de suscripciones.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|El alias de la tabla publicada.|  
|**rowguid**|**uniqueidentifier**|Identificador de la fila especificada.|  
|**generation**|**bigint**|La generación de la fila identificada por el **tablenick** y **rowguid**.|  
|**partchangegen**|**bigint**|Generación asociada al último cambio en los datos que podría haber determinado si la fila pertenece a una publicación filtrada.|  
|**lineage**|**Varbinary(501)**|Alias del suscriptor y pares de números de versión para mantener un historial de los cambios en esta fila.|  
|**colvl**|**varbinary(7489)**|Información de versión de columna.|  
|**marcador**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifica la fila primaria de nivel superior en **MSmerge_contents** (por **rowguid**) para cada fila secundaria correspondiente en un registro lógico.|  
|**logical_record_lineage**|**Varbinary(501)**|Alias del suscriptor y pares de números de versión utilizados para mantener un historial de los cambios en la fila primaria de nivel superior en un registro lógico. Este valor es NULL para todas las filas secundarias en un registro lógico.|  
|**logical_relation_change_gen**|**bigint**|Valor de generación asociado con el último cambio que ocasionó la realineación del registro lógico en la que se insertó o se quitó una fila existente de un registro lógico.|  
  
## <a name="see-also"></a>Vea también  
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
