---
title: catalog.environment_variables (base de datos de SSISDB) | Microsoft Docs
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
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb3d2a6db5f17bb8c180e590426cec34b6dbc359
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (base de datos de SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Muestra los detalles de las variables de entorno para todos los entornos del catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Identificador único de la variable de entorno.|  
|environment_id|**bigint**|Identificador único del entorno al que la variable está asociada.|  
|NAME|**sysname**|Nombre de la variable de entorno.|  
|description|**nvarchar(1024)**|Descripción de la variable de entorno.|  
|Tipo|**nvarchar(128)**|Tipo de datos de la variable de entorno.|  
|sensitive|**bit**|Cuando el valor es `1`, la variable es confidencial y se cifra cuando se almacena. Cuando el valor es `0`, la variable no es confidencial y el valor se almacena como texto simple.|  
|value|**sql_variant**|Valor de la variable de entorno. Cuando el parámetro "sensitive" es `0`, se muestra el valor de texto no cifrado. Cuando el parámetro "sensitive" es `1`, se muestra el valor **NULL**.|  
  
## <a name="remarks"></a>Notas  
 Esta vista muestra una fila para cada variable de entorno en el catálogo.  
  
## <a name="permissions"></a>Permisos  
 Esta vista exige uno de los siguientes permisos:  
  
-   Permiso de lectura en el entorno correspondiente  
  
-   Pertenencia al rol de base de datos de **ssis_admin**  
  
-   Pertenencia al rol de servidor de **sysadmin**  
  
> [!NOTE]  
>  Cuando se dispone de permiso para realizar una operación en el servidor, también se dispone de permiso para ver información sobre la operación. Se aplica la seguridad en el nivel de fila; solo se muestran las filas para las que disponga de permiso para ver.  
  
  
