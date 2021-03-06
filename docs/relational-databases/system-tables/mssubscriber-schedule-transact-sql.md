---
title: MSsubscriber_schedule (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 983ea7374e26cfae1c3313f1e4eaec9bd287ff22
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriberschedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSsubscriber_schedule** tabla contiene la combinación de forma predeterminada y las programaciones de sincronización transaccional de cada par de publicador y suscriptor. Esta tabla se almacena en la base de datos de distribución.  
  
> [!NOTE]  
>  Esta tabla del sistema ha quedado desusada y se mantiene para admitir las versiones anteriores de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**publicador**|**sysname**|El nombre del publicador.|  
|**suscriptor**|**sysname**|Nombre del suscriptor.|  
|**agent_type**|**smallint**|El tipo de agente:<br /><br /> 0 = Agente de distribución.<br /><br /> 1 = Agente de mezcla.|  
|**frequency_type**|**int**|Frecuencia con que se programa el Agente de distribución:<br /><br /> **1** = una vez.<br /><br /> **2** = a petición.<br /><br /> **4** = diariamente.<br /><br /> **8** = semanalmente.<br /><br /> **16** = mensualmente.<br /><br /> **32** = mensualmente relativa.<br /><br /> **64** = inicio automático.<br /><br /> **128** = periódica.|  
|**frequency_interval**|**int**|El valor que debe aplicarse a la frecuencia establecida **frequency_type**.|  
|**frequency_relative_interval**|**int**|Fecha del Agente de distribución:<br /><br /> **1** = primero.<br /><br /> **2** = segundo.<br /><br /> **4** = tercero.<br /><br /> **8** = cuarto.<br /><br /> **16** = último.|  
|**frequency_recurrence_factor**|**int**|El factor de periodicidad utilizado por **frequency_type**.|  
|**frequency_subday**|**int**|Frecuencia de repetición de la programación durante el periodo definido:<br /><br /> **1** = una vez.<br /><br /> **2** = segundo.<br /><br /> **4** = minuto.<br /><br /> **8** = hora.|  
|**frequency_subday_interval**|**int**|El intervalo de **frequency_subday**.|  
|**active_start_time_of_day**|**int**|Hora del día en que el Agente de distribución se programa por primera vez, con formato HHMMSS.|  
|**active_end_time_of_day**|**int**|Hora del día en que el Agente de distribución deja de estar programado, con formato HHMMSS.|  
|**active_start_date**|**int**|Fecha en que se programa por primera vez el Agente de distribución, con formato AAAAMMDD.|  
|**active_end_date**|**int**|Fecha en que se deja de programar el Agente de distribución, con formato AAAAMMDD.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
