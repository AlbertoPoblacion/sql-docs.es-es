---
title: catalog.object_versions (base de datos de SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8a790874900f5fc69e4f8e50d4f84d835d63c1a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (base de datos de SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Muestra las versiones de objetos en el catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. En esta versión, solo las versiones de proyectos se admiten en esta vista.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|Identificador único (ID) de la versión del objeto. No se garantiza que este número sea secuencial.|  
|object_id|**bigint**|Identificador único del objeto.|  
|object_type|**smallint**|Tipo de objeto. Se mostrará un valor `20` para los proyectos.|  
|object_name|**sysname(nvarchar(128))**|Nombre del objeto.|  
|description|**nvarchar(1024)**|Descripción del proyecto.|  
|created_by|**nvarchar(128)**|Nombre del usuario que agregó el objeto al catálogo.|  
|created_time|**datetimeoffset**|Fecha y hora en que el objeto se agregó al catálogo.|  
|restored_by|**nvarchar(128)**|Nombre del usuario que restauró el objeto.|  
|last_restored_time|**datetimeoffset**|Fecha y hora en que el objeto se restauró por última vez.|  
  
## <a name="remarks"></a>Notas  
 Esta vista muestra una fila para cada versión de un objeto en el catálogo.  
  
## <a name="permissions"></a>Permisos  
 Para ver las filas en esta vista, debe tener uno de los siguientes permisos:  
  
-   Permiso READ en el objeto  
  
-   Pertenencia al rol de base de datos de **ssis_admin**  
  
-   Pertenencia al rol de servidor **sysadmin**  
  
> [!NOTE]  
>  Se aplica la seguridad en el nivel de fila; solo se muestran las filas para las que disponga de permiso para ver.  
  
  
