---
title: Sys.resource_governor_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c85332cb1c26f81cdbbaa7bffa5410cf29e711e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904549"
---
# <a name="sysresourcegovernorconfiguration-transact-sql"></a>sys.resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el estado del regulador de recursos almacenado.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|El Id. de la función clasificadora tal y como se almacena en los metadatos. No admite valores NULL.<br /><br /> **Tenga en cuenta** esta función se utiliza para clasificar nuevas sesiones y usa reglas para enrutar la carga de trabajo al grupo de cargas de trabajo adecuado. Para obtener más información, vea [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).|  
|is_enabled|**bit**|Indica el estado actual del regulador de recursos:<br /><br /> 0 = no está habilitado el regulador de recursos.<br /><br /> 1 = el regulador de recursos está habilitado.<br /><br /> No admite valores NULL.|  
|max_outstanding_io_per_volume|**int**|**Se aplica a**: desde [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Número máximo de operaciones de E/S pendientes por volumen.|  
  
## <a name="remarks"></a>Comentarios  
 La vista de catálogo muestra la configuración del regulador de recursos tal y como se almacena en los metadatos. Para ver la configuración en memoria, utilice la vista de administración dinámica correspondiente.  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso VIEW ANY DEFINITION para ver el contenido; requiere el permiso CONTROL SERVER para cambiar el contenido.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra cómo obtener y comparar los valores de metadatos almacenados y los valores en memoria de la configuración del regulador de recursos.  
  
```  
USE master;  
GO  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
GO  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo del regulador de recursos &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [Regulador de recursos](../../relational-databases/resource-governor/resource-governor.md)  
  
  
