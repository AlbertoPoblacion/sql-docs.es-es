---
title: sys.dm_resource_governor_resource_pool_affinity (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 83c425a7346e58b4332ee4c8e78b4fe607b9ca6a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmresourcegovernorresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Realiza el seguimiento de la afinidad del grupo de recursos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "icono de vínculo de tema") [convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Nombre de Colmn|Tipo de datos|Description|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|Identificador del grupo de recursos. No admite valores NULL.|  
|Processor_group|**smallint**|Identificador del grupo de procesadores lógicos de Windows. No admite valores NULL.|  
|Scheduler_mask|**bigint**|Máscara binaria que representa los programadores asociados a este grupo. No admite valores NULL.|  
  
## <a name="remarks"></a>Comentarios  
 Los grupos creados con la afinidad AUTO no aparecerán en esta vista porque no tienen ninguna afinidad. Para obtener más información, consulte el [CREATE RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-resource-pool-transact-sql.md) y [ALTER RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-resource-pool-transact-sql.md) instrucciones.  
  
## <a name="see-also"></a>Vea también  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
