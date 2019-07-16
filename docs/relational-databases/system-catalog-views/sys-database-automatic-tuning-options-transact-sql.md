---
title: Sys.database_automatic_tuning_options (Transact-SQL) | Microsoft Docs
description: Obtenga información sobre cómo ver las opciones de ajuste automático en una base de datos de SQL
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 437dbbc4ea7deb32a9723febb443cc67941fdc5e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67940218"
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>Sys.Database\_automática\_tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Devuelve las opciones de ajuste automático para esta base de datos.  

|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|El nombre de la opción de ajuste automático. Consulte [ALTER DATABASE establece AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) para las opciones disponibles.|  
|**desired_state**|**smallint**|Indica el modo de operación deseada para la opción de ajuste automático, establezca explícitamente por el usuario.<br />0 = OFF<br />1 = ON|  
|**desired_state_desc**|**nvarchar(60)**|Descripción textual del modo de operación deseada de la opción de ajuste automático.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Indica el modo de operación de la opción de ajuste automático.<br />0 = OFF<br />1 = ON|  
|**actual_state_desc**|**nvarchar(60)**|Descripción textual del modo de operación real de la opción de ajuste automático.<br />OFF<br />ON|  
|**reason**|**smallint**|Indica por qué estados reales y deseados son diferentes.<br />2 = DESHABILITADO<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Descripción textual de la razón de por qué estados reales y deseados son diferentes.<br />DESHABILITADO = opción está deshabilitada de forma del sistema<br />QUERY_STORE_OFF = consulta Store se ha desactivado<br />QUERY_STORE_READ_ONLY = consulta Store está en modo de solo lectura<br />NOT_SUPPORTED = disponible solo en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>Vea también  
 [El ajuste automático](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
