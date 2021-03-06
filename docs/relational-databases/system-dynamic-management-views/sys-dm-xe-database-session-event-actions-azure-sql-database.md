---
title: sys.dm_xe_database_session_event_actions (Azure SQL Database) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4b3fcfe0e335b53dc483cde24520ea136c9af37
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxedatabasesessioneventactions-azure-sql-database"></a>sys.dm_xe_database_session_event_actions (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Devuelve información sobre las acciones de la sesión de eventos. Se ejecutan las acciones cuando se activan los eventos. Esta vista de administración agrega estadísticas del número de veces que se ha ejecutado una acción y el tiempo de ejecución total de la acción.  
  
||  
|-|  
|**Se aplica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 y todas las versiones futuras.|  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|La dirección de memoria de la sesión de eventos. No admite valores NULL.|  
|action_name|**nvarchar(60)**|El nombre de la acción. No admite valores NULL.|  
|action_package_guid|**uniqueidentifier**|El GUID del paquete que contiene la acción. No admite valores NULL.|  
|event_name|**nvarchar(60)**|Nombre del evento al que se enlaza la acción. No admite valores NULL.|  
|event_package_guid|**uniqueidentifier**|El GUID para el paquete que contiene el evento. No admite valores NULL.|  
  
## <a name="permissions"></a>Permissions  
 Requiere el permiso VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalidades de relación  
  
|De|En|Relación|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_event_actions.event_session_address|sys.dm_xe_database_sessions.address|Varios a uno|  
|sys.dm_xe_database_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_database_session_events.event_package_guid|Varios a uno|  
|sys.dm_xe_database_session_event_actions.event_name<br /><br /> sys.dm_xe_database_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|Varios a uno|  
  
## <a name="see-also"></a>Vea también  
 [Eventos extendidos](../../relational-databases/extended-events/extended-events.md)  
  
  
