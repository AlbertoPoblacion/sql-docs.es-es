---
title: syspolicy_policy_execution_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 155c88f9e23a706fe7124893a8dd0c5ac5f03173
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62671796"
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Muestra el momento en que se ejecutaron las directivas, el resultado de cada ejecución y detalles sobre errores, si se produjo alguno. En la tabla siguiente se describen las columnas de la vista de syspolicy_policy_execution_history.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Identificador de este registro. Cada registro indica una directiva y el momento en que se inició.|  
|policy_id|**int**|Identificador de la directiva.|  
|start_date|**datetime**|Fecha y hora en que intentó ejecutarse esta directiva.|  
|end_date|**datetime**|Momento en que terminó de ejecutarse esta directiva.|  
|resultado|**bit**|Corrección o error de la directiva. 0 = error, 1 = correcto.|  
|exception_message|**nvarchar(max)**|Mensaje generado por la excepción, si se produjo alguna.|  
|excepción|**nvarchar(max)**|Descripción de la excepción, si se produjo alguna.|  
  
## <a name="remarks"></a>Comentarios  
 El [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) vista contiene los detalles relacionados sobre los objetivos de la directiva y las expresiones de condición probadas.  
  
## <a name="permissions"></a>Permisos  
 Requiere la pertenencia al rol PolicyAdministratorRole en la base de datos msdb.  
  
## <a name="see-also"></a>Vea también  
 [Administrar servidores mediante administración basada en directivas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vistas de administración basada en directivas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
