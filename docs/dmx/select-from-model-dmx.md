---
title: SELECT FROM &lt;modelo&gt; (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5611ce3da4f12bca5cb271cabe8af3e149dcbf35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928327"
---
# <a name="select-from-ltmodelgt-dmx"></a>SELECT FROM &lt;modelo&gt; (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Realiza una combinación de predicción vacía que devuelve el valor o valores más probables para las columnas especificadas. Para crear la predicción, solo se emplea el contenido del modelo de minería de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumentos  
 *lista de expresiones*  
 Lista delimitada por comas de expresiones o de columnas PREDICT o PREDICT ONLY.  
  
 *n*  
 Opcional. Entero que especifica el número de filas que se devuelven.  
  
 *model*  
 Identificador de modelo.  
  
 *lista de condiciones*  
 Opcional. Condiciones para restringir los valores que devuelve la lista de columnas.  
  
 *expression*  
 Opcional. Expresión que devuelve un valor escalar.  
  
## <a name="remarks"></a>Comentarios  
 Las columnas de la *lista de expresiones* debe ser definida como predict o predict only, o relacionados con una columna de predicción.  
  
## <a name="naive-bayes-example"></a>Ejemplo de Bayes naive  
 En el siguiente ejemplo se realiza una combinación de predicción vacía en la columna Bike Buyer, que devuelve el estado más probable del modelo de minería de datos TM Naive Bayes.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Ejemplo de serie temporal  
 En el siguiente ejemplo se realiza una predicción en la columna Amount del modelo Forecasting, que devuelve los siguientes cuatro estadios temporales. La columna Model Region combina modelos de bicicleta y regiones en un único identificador. La consulta utiliza la [PredictTimeSeries &#40;DMX&#41; ](../dmx/predicttimeseries-dmx.md) función para realizar la predicción.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Vea también  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Extensiones de minería de datos &#40;DMX&#41; instrucciones de definición de datos](../dmx/dmx-statements-data-definition.md)   
 [Extensiones de minería de datos &#40;DMX&#41; instrucciones de manipulación de datos](../dmx/dmx-statements-data-manipulation.md)   
 [Referencia de instrucciones de Extensiones de minería de datos &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
