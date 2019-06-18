---
title: sys.fn_hadr_backup_is_preferred_replica  (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_backup_is_preferred_replica_TSQL
- sys.fn_hadr_backup_is_preferred_replica
- fn_hadr_backup_is_preferred_replica_TSQL
- fn_hadr_backup_is_preferred_replica
dev_langs:
- TSQL
helpviewer_keywords:
- backup on secondary replicas
- active secondary replicas [SQL Server], backup on secondary replicas
- sys.fn_hadr_backup_is_preferred_replica function
ms.assetid: 61b9be77-e2f6-4da1-b2ae-a62cbe226145
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a6bba59d680a9f7ba1595808eed27762670aab97
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62640400"
---
# <a name="sysfnhadrbackupispreferredreplica--transact-sql"></a>sys.fn_hadr_backup_is_preferred_replica  (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Se usa para determinar si la réplica actual es la réplica de copia de seguridad preferida.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sys.fn_hadr_backup_is_preferred_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>Argumentos  
 '*dbname*'  
 Es el nombre de la base de datos de la que se realiza una copia de seguridad. *dbname* es de tipo sysname.  
  
## <a name="returns"></a>Devuelve  
 Devuelve 1 si la base de datos en la instancia actual está en la réplica preferida. De lo contrario, devuelve 0.  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta función en un script de copia de seguridad para determinar si la base de datos actual está en la réplica preferida para las copias de seguridad. Puede ejecutar un script en cada réplica de disponibilidad. Cada uno de estos trabajos examina los mismos datos para determinar qué trabajo debe ejecutarse, por lo que solamente los trabajos programados pasan a la etapa de copia de seguridad. El código de ejemplo podría ser similar al siguiente.  
  
```  
If sys.fn_hadr_backup_is_preferred_replica( @dbname ) <> 1   
BEGIN  
-- If this is not the preferred replica, exit (probably without error).  
END  
-- If this is the preferred replica, continue to do the backup.  
  
```  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-sysfnhadrbackupispreferredreplica"></a>A. Uso de sys.fn_hadr_backup_is_preferred_replica  
 En el ejemplo siguiente se devuelve 1 si la base de datos actual es la réplica de copia de seguridad preferida.  
  
```  
SELECT sys.fn_hadr_backup_is_preferred_replica ('TestDB');  
GO  
```  
  
##  <a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Configurar la copia de seguridad en réplicas de disponibilidad &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
## <a name="see-also"></a>Vea también  
 [Funciones de grupos de disponibilidad AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [Secundarias activas: Copia de seguridad en réplicas secundarias &#40;grupos de disponibilidad Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)[vistas de catálogo de grupos de disponibilidad AlwaysOn &#40;Transact-SQL    &#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)  
  
  
