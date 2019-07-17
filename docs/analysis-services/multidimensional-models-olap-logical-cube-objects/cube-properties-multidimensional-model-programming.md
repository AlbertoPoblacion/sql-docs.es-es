---
title: Programación del modelo de propiedades del cubo - multidimensionales | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85453133ab9facd9f3ed56ad98fa2761ac527e40
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209372"
---
# <a name="cube-properties---multidimensional-model-programming"></a>Propiedades de cubo: Programación de modelos multidimensionales
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Los cubos tienen varias propiedades que se pueden establecer para modificar el comportamiento del cubo. Estas propiedades se resumen en la tabla siguiente.  
  
> [!NOTE]  
>  Algunas propiedades se establecen automáticamente cuando se crea el cubo y no se pueden cambiar.  
  
 Para obtener más información sobre cómo establecer las propiedades de cubo, vea [Diseñador de cubos &#40;Analysis Services - datos multidimensionales&#41;](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|Property|Descripción|  
|--------------|-----------------|  
|**AggregationPrefix**|Especifica el prefijo normal que se utiliza para los nombres de agregación.|  
|**Intercalación**|Especifica el identificador de configuración regional (LCID) y la marca de comparación, separados por un carácter de subrayado. por ejemplo, Latin1_General_C1_AS.|  
|**Elemento DefaultMeasure**|Contiene una expresión MDX (Expresiones multidimensionales) que define la medida predeterminada para el cubo.|  
|**Descripción**|Proporciona una descripción del cubo, que se puede mostrar en aplicaciones cliente.|  
|**ErrorConfiguration**|Contiene valores de control de errores configurables para controlar claves duplicadas, claves desconocidas, límites de error, acciones al detectar errores, archivos de registro de errores y control de claves nulas.|  
|**EstimatedRows**|Especifica el número de filas estimadas del cubo.|  
|**ID**|Contiene el identificador único (Id.) del cubo.|  
|**Lenguaje**|Especifica el identificador de idioma predeterminado del cubo.|  
|**Name**|Especifica el nombre descriptivo del cubo.|  
|**ProactiveCaching**|Define la configuración de almacenamiento en caché automático para el cubo.|  
|**ProcessingMode**|Indica si la indización y la agregación se deben producir durante o después del procesamiento. Las opciones son **regular** o **diferida**.|  
|**ProcessingPriority**|Determina la prioridad de procesamiento del cubo durante las operaciones de fondo, como indizaciones y agregaciones diferidas. El valor predeterminado es **0**.|  
|**ScriptCacheProcessingMode**|Indica si la caché de script se debe generar durante o después del procesamiento. Las opciones son **regular** y **diferida**.|  
|**ScriptErrorHandlingMode**|Determina el control de errores. Las opciones son **IgnoreNone** o **IgnoreAll**|  
|**Origen**|Muestra la vista del origen de datos utilizada para el cubo.|  
|**StorageLocation**|Especifica la ubicación de almacenamiento del sistema de archivos para el cubo. Si no se especifica ninguna ubicación, se hereda de la base de datos que contiene el objeto de cubo.|  
|**StorageMode**|Especifica el modo de almacenamiento del cubo. Los valores son **MOLAP**, **ROLAP**, o **HOLAP**.|  
|**Visible**|Determina la visibilidad del cubo|  
  
> [!NOTE]  
>  Para obtener más información acerca de cómo establecer valores para la propiedad ErrorConfiguration cuando se trabaja con valores nulos y otros problemas de integridad de datos, vea [controlar problemas de integridad de datos en Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento en caché automático &#40;particiones&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  
