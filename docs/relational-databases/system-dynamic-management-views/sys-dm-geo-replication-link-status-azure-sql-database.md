---
title: Sys.dm_geo_replication_link_status (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
author: mashamsft
ms.author: mathoma
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8302de76b45ca09e86c87c29ab99c30898168de5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900887"
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Contiene una fila para cada vínculo de replicación entre bases de datos principales y secundarias en una asociación de replicación geográfica. Esto incluye las bases de datos principales y secundarias. Si existe más de un vínculo de replicación continua para una base de datos principal, esta tabla contiene una fila para cada una de las relaciones. La vista se crea en todas las bases de datos, incluida a la maestra lógica. Sin embargo, al consultar esta vista en la maestra lógica se devuelve un conjunto vacío.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|Id. exclusivo del vínculo de replicación.|  
|partner_server|**sysname**|Nombre del servidor de base de datos SQL que contiene la base de datos vinculado.|  
|partner_database|**sysname**|Nombre de la base de datos vinculada en la que reside el servidor de SQL Database vinculado.|  
|last_replication|**datetimeoffset**|La marca de tiempo de confirmación de la última transacción mediante la base de datos secundaria según el reloj de la base de datos principal. Este valor está disponible en la base de datos principal solo.|  
|replication_lag_sec|**int**|Diferencia de tiempo en segundos entre el valor de last_replication y la marca de tiempo de confirmación de la transacción en el servidor principal según el reloj de la base de datos principal.  Este valor está disponible en la base de datos principal solo.|  
|replication_state|**tinyint**|El estado de replicación geográfica para esta base de datos, uno de:.<br /><br /> 1 = la inicialización. Se está propagando el destino de replicación geográfica pero las dos bases de datos no se ha sincronizado. Hasta que se complete la propagación, no se puede conectar a la base de datos secundaria. Quitar la base de datos secundaria de la réplica principal se cancelará la operación de propagación.<br /><br /> 2 = puesta al día. La base de datos secundaria está en un estado transaccionalmente coherente y se está sincronizando constantemente con la base de datos principal.<br /><br /> 4 = suspendido. Esto no es una relación de copia continua activa. Este estado suele indicar que el ancho de banda disponible para el interlink es insuficiente para el nivel de actividad de transacción en la base de datos principal. Sin embargo, la relación de copia continua sigue intacta.|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|role|**tinyint**|Rol de replicación geográfica, uno de:<br /><br /> 0 = primary. El database_id hace referencia a la base de datos principal de la asociación de replicación geográfica.<br /><br /> 1 = la base de datos secundaria.  El database_id hace referencia a la base de datos principal de la asociación de replicación geográfica.|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|El tipo secundario, uno de:<br /><br /> 0 no = directa se permiten las conexiones a la base de datos secundaria y la base de datos no está disponible para acceso de lectura.<br /><br /> 2 = all se permiten conexiones a la base de datos en el repl secundaria; ication para acceso de solo lectura.|  
|secondary_allow_connections_desc|**nvarchar(256)**|No<br /><br /> Todo|  
|last_commit|**datetimeoffset**|La hora de última transacción confirmada en la base de datos. Si puede recuperar la base de datos principal, indica la última hora de confirmación en la base de datos principal. Si puede recuperar la base de datos secundaria, indica la última hora de confirmación en la base de datos secundaria. Si puede recuperar la base de datos secundaria cuando el elemento principal del vínculo de replicación está inactivo, indica hasta qué punto la base de datos secundaria se puso al día.|
  
> [!NOTE]  
>  Si se termina la relación de replicación mediante la eliminación de la base de datos secundaria (sección 4.2), la fila para esa base de datos en el **sys.dm_geo_replication_link_status** desaparece de la vista.  
  
## <a name="permissions"></a>Permisos  
 Puede consultar cualquier cuenta con permiso view_database_state **sys.dm_geo_replication_link_status**.  
  
## <a name="example"></a>Ejemplo  
 Mostrar los retrasos de replicación y la última hora de la replicación de mis bases de datos secundarias.  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE &#40;base de datos SQL Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [Sys.geo_replication_links &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [Sys.dm_operation_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
