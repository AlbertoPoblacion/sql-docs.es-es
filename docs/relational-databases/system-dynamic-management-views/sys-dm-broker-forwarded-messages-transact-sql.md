---
title: sys.dm_broker_forwarded_messages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_forwarded_messages
- dm_broker_forwarded_messages
- sys.dm_broker_forwarded_messages_TSQL
- dm_broker_forwarded_messages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_forwarded_messages dynamic management view
ms.assetid: 5576376d-6364-417a-8475-aa770e060845
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4ce05635464cc9b02e419c4f0a5b162a14042d51
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62759897"
---
# <a name="sysdmbrokerforwardedmessages-transact-sql"></a>sys.dm_broker_forwarded_messages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila por cada mensaje de Service Broker que una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene en proceso de reenvío.  
  

|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**conversation_id**|**uniqueidentifier**|Id. de la conversación a la que pertenece este mensaje. QUE ACEPTA VALORES NULL.|  
|**is_initiator**|**bit**|Indica si este mensaje es del iniciador de la conversación.  QUE ACEPTA VALORES NULL.<br /><br /> 0 = No es del iniciador.<br /><br /> 1 = Es del iniciador|  
|**to_service_name**|**nvarchar(512)**|Nombre del servicio al que se envía este mensaje. QUE ACEPTA VALORES NULL.|  
|**to_broker_instance**|**nvarchar(512)**|Identificador del agente que hospeda el servicio al que se envía este mensaje. QUE ACEPTA VALORES NULL.|  
|**from_service_name**|**nvarchar(512)**|Nombre del servicio que origina este mensaje. QUE ACEPTA VALORES NULL.|  
|**from_broker_instance**|**nvarchar(512)**|Identificador del agente que hospeda el servicio de donde viene este mensaje. QUE ACEPTA VALORES NULL.|  
|**adjacent_broker_address**|**nvarchar(512)**|Dirección de red a la que se envía este mensaje. QUE ACEPTA VALORES NULL.|  
|**message_sequence_number**|**bigint**|Número de secuencia del mensaje en el cuadro de diálogo. QUE ACEPTA VALORES NULL.|  
|**message_fragment_number**|**int**|Si el mensaje de diálogo está fragmentado, es el número de fragmento que contiene este mensaje de transporte. QUE ACEPTA VALORES NULL.|  
|**hops_remaining**|**tinyint**|Número de veces que se puede retransmitir el mensaje antes de que llegue el destino final. Cada vez que se reenvía el mensaje, este número disminuye en 1. QUE ACEPTA VALORES NULL.|  
|**time_to_live**|**int**|Tiempo máximo en que el mensaje permanece activo. Cuando llega a 0, el mensaje se descarta. QUE ACEPTA VALORES NULL.|  
|**time_consumed**|**int**|Tiempo que el mensaje ha estado activo. Cada vez que se reenvía el mensaje, este número aumenta en el tiempo que ha tardado en reenviarse el mensaje. No acepta valores NULL.|  
|**message_id**|**uniqueidentifier**|Id. del mensaje. QUE ACEPTA VALORES NULL.|  
  
## <a name="permissions"></a>Permisos  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vistas de administración dinámica relacionadas con Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

