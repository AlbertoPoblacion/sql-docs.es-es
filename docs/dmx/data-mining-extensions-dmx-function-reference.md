---
title: Referencia de funciones de extensiones de minería de datos (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 68d57ac2db4149178a61424affef5e8948de0063
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070951"
---
# <a name="data-mining-extensions-dmx-function-reference"></a>Referencia de funciones de Extensiones de minería de datos (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] admite varias funciones en lenguaje DMX (Extensiones de minería de datos). Las funciones expanden los resultados de una consulta de predicción a fin de incluir información que permita describir la predicción con mayor nivel de detalle. Las funciones también brindan mayor control sobre la manera en la que se devuelven los resultados de la predicción. En la tabla siguiente se proporcionan vínculos a recursos para ayudarle a entender cómo utilizar las funciones en DMX.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[Funciones de predicción generales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)|Se muestran las funciones que se pueden utilizar con todos los tipos de modelo y se proporcionan vínculos a más información sobre cómo consultar tipos específicos de modelos de minería de datos.|  
|[Estructura y uso de las consultas de predicción de DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)|Se proporciona información general de cómo construir una consulta de predicción utilizando DMX.|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|Devuelve una tabla que contiene un número especificado de filas del nivel más bajo, en orden ascendente de rango en función de una expresión de rango.|  
  
 En la siguiente tabla se enumeran las funciones admitidas por DMX.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|Devuelve una tabla que contiene las últimas filas del elemento n de la expresión de tabla, en orden decreciente, según una expresión de rango.|  
|[BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)|Devuelve una tabla que contiene el número más pequeño de filas del nivel más bajo que cumplen con una expresión de porcentaje especificada, en orden ascendente de rango en función de una expresión de rango.|  
|[BottomSum &#40;DMX&#41;](../dmx/bottomsum-dmx.md)|Devuelve una tabla que contiene el número más pequeño de filas del nivel más bajo que cumplen con una expresión de suma especificada, en orden ascendente de rango en función de una expresión de rango.|  
|[Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)|Devuelve el clúster que tiene la mayor probabilidad de contener el caso de entrada.|  
|[ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)|Devuelve la probabilidad de que el caso de entrada pertenezca al clúster.|  
|[Existe &#40;DMX&#41;](../dmx/exists-dmx.md)|Devuelve true si el conjunto de resultados que devuelve la instrucción SELECT especificada contiene al menos una fila.|  
|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|Indica si el nodo actual desciende del nodo especificado.|  
|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|Indica si el nodo especificado contiene el caso.|  
|[IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)|Indica si un caso pertenece al conjunto de casos de prueba.|  
|[IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)|Indica si un caso pertenece al conjunto de casos de entrenamiento.|  
|[Lag &#40;DMX&#41;](../dmx/lag-dmx.md)|Devuelve el intervalo entre la fecha del caso actual y la última fecha que figura en los datos.|  
|[Predict &#40;DMX&#41;](../dmx/predict-dmx.md)|Realiza una predicción sobre una columna específica.|  
|[PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)|Devuelve la probabilidad ajustada de la columna de predicción especificada.|  
|[PredictAssociation &#40;DMX&#41;](../dmx/predictassociation-dmx.md)|Predice los miembros de asociaciones en una columna.|  
|[PredictCaseLikelihood &#40;DMX&#41;](../dmx/predictcaselikelihood-dmx.md)|Devuelve la probabilidad de que se ajuste a un caso de entrada del modelo existente. Esta función sólo puede usarse con los modelos de clústeres.|  
|[PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md)|Devuelve una tabla que representa el histograma de una columna especificada.|  
|[PredictNodeId &#40;DMX&#41;](../dmx/predictnodeid-dmx.md)|Devuelve el valor de NodeID de un caso seleccionado.|  
|[PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)|Devuelve la probabilidad de la columna especificada.|  
|[PredictSequence &#40;DMX&#41;](../dmx/predictsequence-dmx.md)|Predice los siguientes valores de una secuencia.|  
|[PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)|Recupera el valor de desviación estándar de una columna especificada.|  
|[PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)|Devuelve el valor admitido de la columna.|  
|[PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md)|Predice los valores futuros de una serie temporal.|  
|[PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)|Devuelve el valor de varianza de la columna especificada.|  
|[RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|Devuelve el valor más alto del depósito predicho que fue descubierto para una columna de datos discretos especificada.|  
|[RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)|Devuelve el valor medio del depósito predicho que fue descubierto para una columna de datos discretos especificada.|  
|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)|Devuelve el valor más bajo del depósito predicho que fue descubierto para una columna de datos discretos especificada.|  
|[StructureColumn &#40;DMX&#41;](../dmx/structurecolumn-dmx.md)|Devuelve el valor de la columna de estructura de minería de datos de la tabla especificada.|  
|[TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)|Devuelve una tabla que contiene un número especificado de filas del nivel más alto, en orden descendente de rango en función de una expresión de rango.|  
|[TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)|Devuelve una tabla que contiene el número más pequeño de filas del nivel más alto que cumplen con una expresión de porcentaje especificada, en orden descendente de rango en función de una expresión de rango.|  
|[TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)|Devuelve una tabla que contiene el número más pequeño de filas del nivel más alto que cumplen con una expresión de suma especificada, en orden descendente de rango en función de una expresión de rango.|  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de minería de datos &#40;DMX&#41; referencia de operadores](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de instrucciones](../dmx/data-mining-extensions-dmx-statements.md)   
 [Extensiones de minería de datos &#40;DMX&#41; convenciones de sintaxis](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Extensiones de minería de datos &#40;DMX&#41; elementos de sintaxis](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Funciones de predicción generales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Estructura y uso de las consultas de predicción DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Descripción de la instrucción Select de DMX](../dmx/understanding-the-dmx-select-statement.md)  
  
  
