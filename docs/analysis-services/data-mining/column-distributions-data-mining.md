---
title: Distribuciones de columnas (minería de datos) | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83da6c1ba0a278d2d6b80f309a7bc7f6a1688ba4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724990"
---
# <a name="column-distributions-data-mining"></a>Distribuciones de columnas (minería de datos)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  En [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]puede definir distribuciones de columnas en una estructura de minería de datos para modificar la forma en que los algoritmos procesan los datos de estas columnas cuando se crean modelos de minería de datos. Para algunos algoritmos, resulta útil definir la distribución de las columnas continuas antes de procesar el modelo, si se sabe que las columnas contienen distribuciones de valores comunes. Si no define las distribuciones, los modelos de minería de datos resultantes podrían generar predicciones menos precisas que si se definieran las distribuciones porque los algoritmos disponen de menos información con la que interpretar los datos.  
  
 Los algoritmos que están disponibles en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] admiten los siguientes tipos de distribución:  
  
 **Normal**  
 Los valores de la columna continua forman un histograma con una distribución normal.  
  
 ![Histograma con distribución normal](../../analysis-services/data-mining/media/normal-distribution.gif "histograma con distribución normal")  
  
 **Logarítmica normal**  
 Los valores de la columna continua forman un histograma, donde la curva se alarga en el extremo superior y se desvía hacia el extremo inferior.  
  
 ![Histograma con distribución log-normal](../../analysis-services/data-mining/media/log-normal-distribution.gif "histograma con distribución log-normal")  
  
 **Uniforme**  
 Los valores de la columna continua forman una curva plana, en la que todos los valores tienen la misma probabilidad.  
  
 ![Histograma con distribución uniforme](../../analysis-services/data-mining/media/uniform-distribution.gif "histograma con distribución uniforme")  
  
 Para más información sobre los algoritmos que proporciona [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vea [Algoritmos de minería de datos &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Vea también  
 [Tipos de contenido &#40;minería de datos&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Estructuras de minería de datos &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Métodos de discretización &#40;minería de datos&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [Distribuciones &#40;DMX&#41;](../../dmx/distributions-dmx.md)   
 [Columnas de la estructura de minería de datos](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
