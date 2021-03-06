---
title: "Métodos de discretización (minería de datos) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1acf124467d3a6c5cdeb35a1d617e0dbc9d34d63
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="discretization-methods-data-mining"></a>Métodos de discretización (minería de datos)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Algunos de los algoritmos que se utilizan para crear modelos de minería de datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] requieren tipos de contenido específicos para poder funcionar correctamente. Por ejemplo, el algoritmo Bayes naive de [!INCLUDE[msCoName](../../includes/msconame-md.md)] no puede utilizar columnas continuas como entrada ni predecir valores continuos. Además, algunas columnas pueden contener tal cantidad de valores que el algoritmo no puede identificar con facilidad patrones de interés en los datos para crear un modelo a partir de los mismos.  
  
 En estos casos, puede discretizar los datos en las columnas de modo que pueda utilizar los algoritmos para producir un modelo de minería de datos. La*discretización* es el proceso mediante el cual los valores se incluyen en depósitos para que haya un número limitado de estados posibles. Los depósitos se tratan como si fueran valores ordenados y discretos. Puede discretizar tanto columnas numéricas como de cadena.  
  
 Pueden utilizarse varios métodos para discretizar datos. Si la solución de minería de datos usa datos relacionales, puede controlar el número de depósitos que se usarán para agrupar los datos si establece el valor de la propiedad <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> . El número predeterminado de depósitos es 5.  
  
 Si la solución de minería de datos usa datos de un cubo OLAP (procesamiento analítico en línea), el algoritmo de minería de datos calcula automáticamente el número de depósitos que es necesario generar con la siguiente ecuación, donde n es el número de valores de datos distintos en la columna:  
  
 `Number of Buckets = sqrt(n)`  
  
 Si no quiere que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calcule el número de depósitos, puede usar la propiedad <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> para especificar manualmente el número de depósitos.  
  
 La siguiente tabla describe los métodos que puede utilizar para discretizar datos en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Método de discretización|Description|  
|---------------------------|-----------------|  
|**AUTOMATIC**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determina el método de discretización que se va a utilizar.|  
|**CLUSTERS**|El algoritmo divide los datos en grupos mediante el muestreo de los datos de entrenamiento, inicializa en un número de puntos aleatorios y, a continuación, ejecuta varias iteraciones del algoritmo de clústeres de Microsoft utilizando el método de agrupación en clústeres EM (Expectation Maximization). El método **CLUSTERS** resulta útil porque funciona en cualquier curva de distribución. Sin embargo, requiere más tiempo de procesamiento que otros métodos de discretización.<br /><br /> Este método solo puede utilizarse con columnas numéricas.|  
|**EQUAL_AREAS**|El algoritmo divide los datos en grupos que contienen el mismo número de valores. Este método es la mejor opción para las curvas de distribución normales, pero no se obtendrán resultados óptimos si la distribución incluye grandes cantidades de valores en un grupo pequeño de los datos continuos. Por ejemplo, si la mitad de los productos tiene un costo de 0, la mitad de los datos se encontrarán bajo un solo punto de la curva. En esta distribución, este método divide los datos en un intento de establecer una discretización igual en varias áreas. Esto produce una representación inexacta de los datos.|  
  
## <a name="remarks"></a>Comentarios  
  
-   Puede usar el método **EQUAL_AREAS** para discretizar cadenas.  
  
-   El método **CLUSTERS** usa una muestra aleatoria de 1000 registros para discretizar los datos. Use el método **EQUAL_AREAS** si no quiere que el algoritmo realice un muestreo de datos.  
  
  
  
## <a name="see-also"></a>Vea también  
 [Contenido tipos &#40; minería de datos &#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Contenido tipos &#40; DMX &#41;](../../dmx/content-types-dmx.md)   
 [Algoritmos de minería de datos &#40; Analysis Services: minería de datos &#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Estructuras de minería de datos &#40; Analysis Services: minería de datos &#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Tipos de datos &#40; minería de datos &#41;](../../analysis-services/data-mining/data-types-data-mining.md)   
 [Columnas de estructura de minería de datos](../../analysis-services/data-mining/mining-structure-columns.md)   
 [Distribuciones de columnas &#40;minería de datos&#41;](../../analysis-services/data-mining/column-distributions-data-mining.md)  
  
  
