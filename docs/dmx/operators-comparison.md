---
title: Operadores de comparación (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fcbfb95070783db002d34870e5508df5322210d7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008198"
---
# <a name="operators---comparison"></a>Operadores: comparación
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Puede usar los operadores de comparación con datos escalares en cualquier expresión de extensiones de minería de datos (DMX) de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Los operadores de comparación se evalúan como un tipo de datos booleano; devuelven TRUE o FALSE, según el resultado de la condición probada.  
  
 En la siguiente tabla se describen los operadores de comparación que admite DMX.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[&#60;&#40;Menor&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|En el caso de argumentos que se evalúan como un valor no NULL, devuelve TRUE si el valor del argumento de la izquierda es menor que el valor del argumento de la derecha; de lo contrario, devuelve FALSE. Si un argumento o ambos argumentos se evalúan como un valor NULL, el operador devuelve un valor NULL.|  
|[&#62;&#40;Mayor&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|En el caso de argumentos que se evalúan como un valor no NULL, devuelve TRUE si el valor del argumento de la izquierda es mayor que el valor del argumento de la derecha; de lo contrario, devuelve FALSE. Si un argumento o ambos argumentos se evalúan como un valor NULL, el operador devuelve un valor NULL.|  
|[= &#40;Igual a&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|En el caso de argumentos que se evalúan como un valor no NULL, devuelve TRUE si el valor del argumento de la izquierda es igual que el valor del argumento de la derecha; de lo contrario, devuelve FALSE. Si un argumento o ambos argumentos se evalúan como un valor NULL, el operador devuelve un valor NULL.|  
|[&#60;&#62;&#40;No es igual a&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|En el caso de argumentos que se evalúan como un valor no NULL, devuelve TRUE si el valor del argumento de la izquierda es distinto del valor del argumento de la derecha; de lo contrario, devuelve FALSE. Si un argumento o ambos argumentos se evalúan como un valor NULL, el operador devuelve un valor NULL.|  
|[&#60;= &#40;Menor o igual a&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|En el caso de argumentos que se evalúan como un valor no NULL, devuelve TRUE si el valor del argumento de la izquierda es menor o igual que el valor del argumento de la derecha; de lo contrario, devuelve FALSE. Si un argumento o ambos argumentos se evalúan como un valor NULL, el operador devuelve un valor NULL.|  
|[&#62;= &#40;Mayor o igual que&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|En el caso de argumentos que se evalúan como un valor no NULL, devuelve TRUE si el valor del argumento de la izquierda es mayor o igual que el valor del argumento de la derecha; de lo contrario, devuelve FALSE. Si un argumento o ambos argumentos se evalúan como un valor NULL, el operador devuelve un valor NULL.|  
  
 Los operadores de comparación se pueden usar también en instrucciones y funciones DMX para comprobar una condición.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de Extensiones de minería de datos &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de funciones](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de operadores](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de instrucciones](../dmx/data-mining-extensions-dmx-statements.md)   
 [Extensiones de minería de datos &#40;DMX&#41; convenciones de sintaxis](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Extensiones de minería de datos &#40;DMX&#41; elementos de sintaxis](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Expressions &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Funciones de predicción generales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Operators &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Estructura y uso de las consultas de predicción DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Descripción de la instrucción Select de DMX](../dmx/understanding-the-dmx-select-statement.md)  
  
  
