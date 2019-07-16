---
title: (Dividir) (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 17f1233310ce8b070e12fbf25dca0e256ff34664
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070740"
---
# <a name="divide-dmx"></a>(Dividir) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Realiza una operación aritmética que divide un número por otro número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Dividendo*  
 Expresión DMX (Extensiones de minería de datos) válida que devuelve un valor numérico.  
  
 *Divisor*  
 Expresión DMX válida que devuelve un valor numérico.  
  
## <a name="return-value"></a>Valor devuelto  
 Valor cuyo tipo de datos es el del parámetro con la mayor precedencia.  
  
## <a name="remarks"></a>Comentarios  
 El valor que devuelve el operador es el cociente de la primera expresión dividida por la segunda expresión.  
  
 Ambas expresiones deben ser del mismo tipo de datos o una se debe poder convertir implícitamente en el tipo de datos de la otra. Si el divisor se evalúa como un valor NULL, el operador genera un error. Si tanto el divisor como el dividendo se evalúan como un valor NULL, el operador devuelve un valor NULL.  
  
## <a name="see-also"></a>Vea también  
 [Operadores aritméticos &#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de operadores](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operators &#40;DMX&#41;](../dmx/operators-dmx.md)   
 [Dividir &#40;expresión de SSIS&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;Dividir&#41; &#40;Transact-SQL&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
