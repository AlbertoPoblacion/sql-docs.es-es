---
title: sys.pdw_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28a38f60127100d80a7f9c52caa9851597403c45
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Almacena las propiedades para las alertas diferentes que se pueden producir en el sistema; se trata de una tabla de catálogos para las alertas.  
  
|Nombre de la columna|Tipo de datos|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Identificador único de la alerta.<br /><br /> Clave para esta vista.|NOT NULL|  
|component_id|**int**|Id. del componente al que se aplica esta alerta. El componente es un identificador de componente general, por ejemplo, "Alimentación" y no es específico para una instalación. See [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Nombre de la alerta.|NOT NULL|  
|state|**nvarchar(32)**|Estado de la alerta.|NOT NULL<br /><br /> Valores posibles:<br /><br /> 'Operational'<br /><br /> 'NonOperational'<br /><br /> 'Degradado'<br /><br /> "Error"|  
|severity|**nvarchar(32)**|Gravedad de la alerta.|NOT NULL<br /><br /> Valores posibles:<br /><br /> 'Informativo'<br /><br /> 'Advertencia'<br /><br /> 'Error'|  
|tipo|**nvarchar(32)**|Tipo de alerta.|NOT NULL<br /><br /> Valores posibles:<br /><br /> StatusChange - ha cambiado el estado del dispositivo.<br /><br /> Umbral - un valor ha superado el valor de umbral.|  
|description|**nvarchar(4000)**|Descripción de la alerta.|NOT NULL|  
|condición|**nvarchar(255)**|Utiliza cuando escriba = umbral. Define cómo se calcula el umbral de alerta.|NULL|  
|status|**nvarchar(32)**|Estado de alerta|NULL|  
|condition_value|**bit**|Indica si la alerta se permite que se produzca durante la operación del sistema.|NULL<br /><br /> Valores posibles<br /><br /> 0 - no se generará la alerta.<br /><br /> 1 - la alerta se genera.|  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de datos SQL y vistas de catálogo del almacén de datos en paralelo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
