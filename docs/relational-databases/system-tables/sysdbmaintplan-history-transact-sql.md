---
title: sysdbmaintplan_history (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 382ea93bb97f8746b8adefb54ab1abb73fa00fc4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdbmaintplanhistory-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esta tabla se almacena en la **msdb** base de datos.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Secuencia del historial llevada a cabo según los planes de mantenimiento de bases de datos.|  
|**plan_id**|**uniqueidentifier**|Id. del plan de mantenimiento de bases de datos.|  
|**plan_name**|**sysname**|Nombre del plan de mantenimiento de bases de datos.|  
|**database_name**|**sysname**|Nombre de la base de datos asociada al plan de mantenimiento de bases de datos.|  
|**server_name**|**sysname**|Nombre del sistema.|  
|**actividad**|**nvarchar(128)**|Actividad llevada a cabo por el plan de mantenimiento de bases de datos (por ejemplo, el registro de transacciones de copia de seguridad).|  
|**succeeded**|**bit**|**0** = correcto **1** = error|  
|**end_time**|**datetime**|Hora en que finalizó la acción.|  
|**duration**|**int**|Tiempo necesario para finalizar la acción del plan de mantenimiento de bases de datos.|  
|**start_time**|**datetime**|Hora en que comenzó la acción.|  
|**error_number**|**int**|Número de error generado.|  
|**message**|**nvarchar(512)**|Mensaje generado por **sqlmaint**.|  
  
  
