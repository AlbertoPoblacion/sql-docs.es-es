---
title: Objetos (Analysis Services - datos multidimensionales) de cubo | Documentos de Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 27fab4d1fb52df03991db9559f54f6d829e3256d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Objetos de cubo (Analysis Services - Datos multidimensionales)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
    
## <a name="introducing-cube-objects"></a>Introducción a los objetos de cubo  
 Un objeto <xref:Microsoft.AnalysisServices.Cube> simple se compone de la información básica, dimensiones y grupos de medida. La información básica incluye el nombre del cubo, la medida predeterminada del cubo, el origen de datos, el modo de almacenamiento y otros aspectos.  
  
 La colección Dimensions contiene el conjunto real de dimensiones que se utilizan en el cubo de la colección de dimensiones de la base de datos. Todas las dimensiones deben estar definidas en la colección de dimensiones de la base de datos para hacer referencia a ellas en el cubo. Las dimensiones privadas no están disponibles en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Los grupos de medida son conjuntos de medidas del cubo. Un grupo de medida es una colección de medidas con una vista del origen de datos común y un conjunto común de dimensiones. El grupo de medida es la unidad de proceso de las medidas; los grupos de medida se pueden procesar de forma individual y, a continuación, se pueden examinar.  
  
## <a name="in-this-section"></a>En esta sección  
  
|||  
|-|-|  
|Tema||  
|[Acciones &#40;Analysis Services - Datos multidimensionales&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Agregaciones y diseños de agregaciones](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[Cálculos](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[Las celdas del cubo &#40; Analysis Services - datos multidimensionales &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[Propiedades de cubo: Programación de modelos multidimensionales](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[Almacenamiento de cubos &#40; Analysis Services - datos multidimensionales &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[Traducciones de cubo](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[Relaciones de dimensión](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[Indicadores clave de rendimiento &#40;KPI&#41; en modelos multidimensionales](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Medidas y grupos de medida](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[Particiones &#40;Analysis Services - Datos multidimensionales&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[Perspectivas](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  
