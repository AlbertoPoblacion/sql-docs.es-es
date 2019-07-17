---
title: Sys.dm_resource_governor_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_resource_governor_configuration_TSQL
- dm_resource_governor_configuration
- sys.dm_resource_governor_configuration
- sys.dm_resource_governor_configuration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_configuration dynamic management view
ms.assetid: c89aab6a-0434-4ce6-af8c-f8a1a3284e38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 00b425e5efd441868bfa763fe544827bd7279dc2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067790"
---
# <a name="sysdmresourcegovernorconfiguration-transact-sql"></a>sys.dm_resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila que contiene el estado actual de la configuración en memoria del regulador de recursos.  
  

|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|El Id. de la función clasificadora usada actualmente por el regulador de recursos. Devuelve el valor 0 si no se utiliza ninguna función. No admite valores NULL.<br /><br /> **Nota:** Esta función se utiliza para clasificar nuevas solicitudes y usa reglas para enrutar estas solicitudes al grupo de cargas de trabajo adecuado. Para obtener más información, vea [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).|  
|is_reconfiguration_pending|**bit**|Indica si los cambios a un grupo o fondo se realizaron con la instrucción ALTER RESOURCE GOVERNOR RECONFIGURE pero no se han aplicado a la configuración en memoria. El valor devuelto puede ser:<br /><br /> 0 = No es necesaria una instrucción de reconfiguración.<br /><br /> 1 = Es necesaria una instrucción de reconfiguración o un reinicio del servidor para aplicar los cambios de la configuración pendientes.<br /><br /> **Nota:** El valor devuelto es siempre 0 cuando se deshabilita el regulador de recursos.<br /><br /> No admite valores NULL.|  
|max_outstanding_io_per_volume|**int**|**Se aplica a**: desde [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Número máximo de operaciones de E/S pendientes por volumen.|  
  
## <a name="remarks"></a>Comentarios  
 Esta vista de administración dinámica muestra la configuración en memoria. Utilice la vista de catálogo correspondiente para ver los metadatos almacenados de la configuración.  
  
 En el siguiente ejemplo se muestra cómo obtener y comparar los valores de metadatos almacenados y los valores en memoria de la configuración del regulador de recursos.  
  
```  
USE master;  
go  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
go  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
go  
```  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso VIEW SERVER STATE.  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.resource_governor_configuration &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-configuration-transact-sql.md)   
 [Regulador de recursos](../../relational-databases/resource-governor/resource-governor.md)  
  
  

