---
title: sp_add_maintenance_plan_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_maintenance_plan_job_TSQL
- sp_add_maintenance_plan_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_maintenance_plan_job
ms.assetid: 7205855c-964f-4f55-bf75-39a55f6fe7bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba27f90c8d2fc4c7e174333080815d56f90e48c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091917"
---
# <a name="spaddmaintenanceplanjob-transact-sql"></a>sp_add_maintenance_plan_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Asocia un trabajo existente a un plan de mantenimiento.  
  
> [!NOTE]  
>  Este procedimiento almacenado se utiliza con planes de mantenimiento de bases de datos. Esta característica se ha reemplazado por planes de mantenimiento que no utilizan este procedimiento almacenado. Utilice este procedimiento para conservar planes de mantenimiento de bases de datos en instalaciones actualizadas de una versión anterior de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_add_maintenance_plan_job [ @plan_id = ] 'plan_id' , [ @job_id = ] 'job_id'  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @plan_id = ] 'plan_id'` Especifica el identificador del plan de mantenimiento. *plan_id* es **uniqueidentifier**, y debe ser un identificador válido.  
  
`[ @job_id = ] 'job_id'` Especifica el identificador del trabajo que se asociará con el plan de mantenimiento. *job_id* es **uniqueidentifier**, y debe ser un identificador válido. Para crear un trabajo o trabajos, ejecute **sp_add_job**, o utilice SQL Server Management Studio.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_add_maintenance_plan_job** se debe ejecutar desde la **msdb** base de datos.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede ejecutar **sp_add_maintenance_plan_job**.  
  
## <a name="examples"></a>Ejemplos  
 Este ejemplo agrega el trabajo "B8FCECB1-E22C-11D2-AA64-00C04F688EAE" al plan de mantenimiento creado con **sp_add_maintenance_plan_job**.  
  
```  
EXECUTE   sp_add_maintenance_plan_job N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'B8FCECB1-E22C-11D2-AA64-00C04F688EAE';  
```  
  
## <a name="see-also"></a>Vea también  
 [Planes de mantenimiento](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Procedimientos almacenados de planes de mantenimiento de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
