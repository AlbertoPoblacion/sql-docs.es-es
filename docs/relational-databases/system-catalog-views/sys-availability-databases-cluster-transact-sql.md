---
title: Sys.availability_databases_cluster (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_databases_cluster_TSQL
- sys.availability_databases_cluster
- availability_databases_cluster_TSQL
- availability_databases_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.availability_databases_cluster catalog view
- Availability Groups [SQL Server], databases
ms.assetid: 8d9c57e5-7f39-4315-b466-92748231140a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 206c9b1c250cb95a6ad49ccf20f8badf11f870ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046535"
---
# <a name="sysavailabilitydatabasescluster-transact-sql"></a>sys.availability_databases_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene una fila por cada base de datos de disponibilidad en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que hospeda una réplica de disponibilidad para cualquier grupo de disponibilidad Always On en el clúster de clústeres de conmutación por error de servidor de Windows (WSFC), independientemente de si el equipo local copiar base de datos ya se ha unido al grupo de disponibilidad.  
  
> [!NOTE]  
>  Cuando una base de datos se agrega a un grupo de disponibilidad, la base de datos principal se une automáticamente al grupo. Las bases de datos secundarias se deben preparar en cada réplica secundaria para poder unirse al grupo de disponibilidad.   
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificador único del grupo de disponibilidad dentro del grupo de disponibilidad en que la base de datos participa, si hay alguno.<br /><br /> NULL = la base de datos no forma parte de una réplica de disponibilidad en el grupo de disponibilidad.|  
|**group_database_id**|**uniqueidentifier**|Identificador único de la base de datos dentro del grupo de disponibilidad en que la base de datos participa, si hay alguno. **group_database_id** es el mismo para esta base de datos en la réplica principal y en cada réplica secundaria en el que la base de datos se ha unido al grupo de disponibilidad.<br /><br /> NULL = la base de datos no forma parte de una réplica de disponibilidad en ningún grupo de disponibilidad.|  
|**database_name**|**sysname**|Nombre de la base de datos que se agregó al grupo de disponibilidad.|  
  
## <a name="permissions"></a>Permisos  
 Si el llamador de **sys.availability_databases_cluster** no es el propietario de la base de datos, los permisos mínimos necesarios para ver la fila correspondiente son ALTER ANY DATABASE o permiso de nivel de servidor VIEW ANY DATABASE o CREATE Permiso de base de datos en el **maestro** base de datos.  
  
## <a name="see-also"></a>Vea también  
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)   
 [sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md)   
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
