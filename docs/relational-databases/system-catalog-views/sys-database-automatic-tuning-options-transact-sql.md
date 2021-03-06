---
title: sys.database_automatic_tuning_options (Transact-SQL) | Microsoft Docs
description: "Obtenga información acerca de cómo ver las opciones de optimización automática en una base de datos de SQL"
ms.custom: 
ms.date: 07/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
caps.latest.revision: 
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4208b9e294273444c24ac9e3a05e60b43d4274c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>sys.database\_automatic\_tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Devuelve las opciones de optimización automática de esta base de datos.  

|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**Nombre**|**nvarchar(128)**|El nombre de la opción de optimización automática. Hacer referencia a [ALTER AUTOMATIC_TUNING del conjunto de base de datos &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) opciones disponibles.|  
|**desired_state**|**smallint**|Indica el modo de operación para la opción de optimización automática, establece explícitamente por el usuario.<br />0 = OFF<br />1 = ON |  
|**desired_state_desc**|**nvarchar(60)**|Descripción textual del modo de operación de ajuste automático de la opción.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Indica el modo de operación de ajuste automático de la opción.<br />0 = OFF<br />1 = ON |  
|**actual_state_desc**|**nvarchar(60)**|Descripción textual del modo de operación real de opción de optimización automática.<br />OFF<br />ON|  
|**reason**|**smallint**|Indica por qué estados reales y deseados son diferentes.<br />2 = DESHABILITADO<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Descripción textual de la razón por qué estados reales y deseados son diferentes.<br />DESHABILITADO = opción está deshabilitada por sistema<br />QUERY_STORE_OFF = almacén de consultas está desactivado<br />QUERY_STORE_READ_ONLY = almacén de consultas está en modo de solo lectura<br />NOT_SUPPORTED = disponible solo en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>Permissions  
 Requiere la `VIEW DATABASE STATE` permiso.  
  
## <a name="see-also"></a>Vea también  
 [El ajuste automático](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER AUTOMATIC_TUNING del conjunto de base de datos &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
