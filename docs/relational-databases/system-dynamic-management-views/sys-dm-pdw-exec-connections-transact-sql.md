---
title: sys.dm_pdw_exec_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e93d397d10a99f844454494c4bf0d82b7fe6d660
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502969"
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Devuelve información acerca de las conexiones establecidas con esta instancia de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y los detalles de cada conexión.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifica la sesión asociada a esta conexión. Use `SESSION_ID()` para devolver el `session_id` de la conexión actual.|  
|connect_time|**datetime**|Marca de tiempo en que se estableció la conexión. No admite valores NULL.|  
|encrypt_option|**nvarchar(40)**|Indica TRUE (la conexión está cifrada) o FALSE (conexión no es enctypred).|  
|auth_scheme|**nvarchar(40)**|Especifica el esquema de autenticación [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows usado en esta conexión. No admite valores NULL.|  
|client_id|**varchar(48)**|Dirección IP del cliente que se conecta a este servidor. Acepta valores NULL.|  
|sql_spid|**int**|El identificador de proceso de servidor de la conexión. Use `@@SPID` para devolver el `sql_spid` de la conexión actual. Con fines más, utilice el `session_id` en su lugar.|  
  
## <a name="permissions"></a>Permisos  
 Requiere **VIEW SERVER STATE** permiso en el servidor.  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relación  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|Uno a uno|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|Varios a uno|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Consulta típica para recopilar información sobre una conexión solo para consultas.  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>Vea también  
 [Vistas de administración dinámica de almacenamiento de datos en paralelo y SQL Data Warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

