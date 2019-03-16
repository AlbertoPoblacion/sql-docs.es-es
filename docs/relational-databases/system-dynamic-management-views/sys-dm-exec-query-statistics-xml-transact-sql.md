---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 63e1d22670929448110083c31e9900e462d576bc
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072309"
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Devuelve el plan de ejecución para que finalicen las solicitudes de consultas. Utilice esta DMV para recuperar el plan de presentación XML con estadísticas transitorias. 

## <a name="syntax"></a>Sintaxis

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Argumentos 
*session_id*  
 Es el identificador de sesión ejecutando el lote que se va a buscar. *session_id* es **smallint**. *session_id* puede obtenerse de los objetos de administración dinámica siguientes:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Tabla devuelta

|Nombre de la columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|Id. de la sesión. No acepta valores NULL.|
|request_id|**int**|Identificador de la solicitud. No acepta valores NULL.|
|sql_handle|**varbinary(64)**|Asignación hash del texto SQL de la solicitud. Acepta valores NULL.|
|plan_handle|**varbinary(64)**|Asignación hash del plan de consulta. Acepta valores NULL.|
|query_plan|**xml**|SHOWPLAN XML con estadísticas parciales. Acepta valores NULL.|

## <a name="remarks"></a>Comentarios
Esta función del sistema está disponible a partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1. Vea KB [3190871](https://support.microsoft.com/en-us/help/3190871)

Esta función del sistema que funciona en ambos **estándar** y **ligera** consultar las estadísticas de ejecución de generación de perfiles de infraestructura. Para obtener más información, vea [Infraestructura de generación de perfiles de consultas](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md).  

## <a name="permissions"></a>Permisos  
 Requiere el permiso `VIEW SERVER STATE` en el servidor.  

## <a name="examples"></a>Ejemplos  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Examinar las estadísticas de ejecución y el plan de consulta activa para un lote en ejecución  
 El ejemplo siguiente se consulta **sys.dm_exec_requests** para encontrar la consulta de interés y copiar su `session_id` desde la salida.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 A continuación, para obtener las estadísticas de ejecución y el plan de consulta activa, use el copiado `session_id` con la función del sistema **sys.dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 O combinado para todas las solicitudes de ejecución.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>Vea también
  [Marcas de seguimiento](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vistas de administración dinámica relacionadas con la base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

