---
title: Dividir (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6d0569234b3ba6fbfde102bb5e71a419cd9f4f5a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081079"
---
# <a name="divide-ssis-expression"></a>Divide (SSIS Expression)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Divide la primera expresión numérica por la segunda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *dividend*  
 Es la expresión numérica que se va a dividir. *dividend* puede ser cualquier expresión numérica. Para más información, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Es la expresión numérica entre la que se va a dividir el dividendo. *divisor* puede ser cualquier expresión numérica excepto cero.  
  
## <a name="result-types"></a>Tipos de resultado  
 Determinados por los tipos de datos de los dos argumentos. Para más información, consulte [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Notas  
 Si alguno de los operandos es NULL, el resultado será NULL.  
  
 No se permite dividir por cero. En función de cómo se evalúe la subexpresión *divisor* , se producirá uno de los siguientes errores:  
  
-   Si la subexpresión *divisor* que devuelve cero es una constante, el error aparecerá en tiempo de diseño y hará que no se valide la expresión.  
  
-   Si la subexpresión *divisor* que devuelve cero contiene variables pero no contiene columnas de entrada, el componente al que la expresión pertenece no superará la validación previa a la ejecución del paquete.  
  
-   Si la subexpresión *divisor* que se evalúa como cero contiene columnas de entrada, el error aparecerá en tiempo de ejecución y se controlará en función de las reglas de flujo de errores del componente de flujo de datos.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo divide dos literales numéricos.  
  
```  
25 / 5  
```  
  
 Este ejemplo divide los valores de la columna **ListPrice** por los valores de la columna **StandardCost** .  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>Consulte también  
 [Precedencia y capacidad de asociación de operadores](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operadores &#40;expresión de SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
