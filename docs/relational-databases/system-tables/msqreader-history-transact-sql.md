---
title: MSqreader_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSqreader_history
- MSqreader_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f21873e8db662bc77bd1acbb5d48c6af49aba404
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032527"
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSqreader_history** tabla contiene filas de historial para los agentes de lector de cola asociados al distribuidor local. Esta tabla se almacena en la base de datos de distribución.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|El identificador del Agente de lectura de cola.|  
|**publication_id**|**int**|Id. de la publicación.|  
|**runstatus**|**int**|Estado de ejecución del agente:<br /><br /> **1** = inicio.<br /><br /> **2** = se realice correctamente.<br /><br /> **3** = en curso.<br /><br /> **4** = inactivo.<br /><br /> **5** = reintento.<br /><br /> **6** = error.|  
|**start_time**|**datetime**|Fecha y hora en que empezó la sesión del agente.|  
|**time**|**datetime**|Fecha y hora del último mensaje registrado.|  
|**duration**|**int**|Tiempo transcurrido de la actividad de sesión registrada, en segundos.|  
|**Comentarios**|**nvarchar(255)**|Texto descriptivo.|  
|**transaction_id**|**nvarchar(40)**|Id. de transacción almacenado en el mensaje, si procede.|  
|**transaction_status**|**int**|El estado de la transacción.|  
|**transactions_processed**|**int**|Número acumulado de transacciones procesadas en la sesión.|  
|**commands_processed**|**int**|Número acumulado de comandos procesados en la sesión.|  
|**delivery_rate**|**float(53)**|Número promedio de comandos entregados por segundo.|  
|**transaction_rate**|**float(53)**|Tasa de transacciones procesadas.|  
|**suscriptor**|**sysname**|Nombre del suscriptor.|  
|**subscriberdb**|**sysname**|El nombre de la base de datos de suscripción.|  
|**error_id**|**int**|Si no cero, el número representa un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mensaje de error.|  
|**timestamp**|**timestamp**|Columna de marca de tiempo y hora de la tabla.|  
  
## <a name="see-also"></a>Vea también  
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
