---
title: Sys.sysconfigures (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b423d21fe65751502e41de6639bc85b0ac8c61f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una fila por cada opción de configuración establecida por un usuario. **sysconfigures** contiene las opciones de configuración definidas antes de la última vez que se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], además de las opciones de configuración dinámicas establecen desde ese momento.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**value**|**int**|Valor de la variable, que el usuario puede modificar. [!INCLUDE[ssDE](../../includes/ssde-md.md)] lo utiliza solo si se ha ejecutado RECONFIGURE.|  
|**config**|**int**|Número de la variable de configuración.|  
|**comment**|**nvarchar(255)**|Explicación de la opción de configuración.|  
|**status**|**smallint**|Mapa de bits que indica el estado de la opción. Entre los valores posibles figuran los siguientes:<br /><br /> 0 = Estático. Configuración surte efecto cuando se reinicia el servidor.<br /><br /> 1 = Dinámico. La variable surte efecto cuando se ejecuta la instrucción RECONFIGURE.<br /><br /> 2 = Avanzado. Se muestra la variable solo cuando la **Mostrar opciones avanzadas** se establece. Configuración surte efecto cuando se reinicia el servidor.<br /><br /> 3 = Dinámico y avanzado.|  
  
## <a name="see-also"></a>Vea también  
 [Asignar tablas del sistema a vistas del sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vistas de compatibilidad &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
