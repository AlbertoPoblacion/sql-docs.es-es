---
title: StrToSet (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 729dae70fce03b3dec1394900126b216d09dc497
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036791"
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)


  Devuelve el conjunto especificado por una cadena con formato de expresiones multidimensionales (MDX).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Specification*  
 Expresión de cadena válida que especifica, directa o indirectamente, un conjunto.  
  
## <a name="remarks"></a>Observaciones  
 La función **StrToSet** devuelve el conjunto especificado en la expresión de cadena. La función **StrToSet** se utiliza normalmente con funciones definidas por el usuario para devolver una especificación de conjunto desde una función externa a una instrucción MDX o cuando se parametriza una consulta MDX.  
  
-   Cuando se utiliza la marca CONSTRAINED, la especificación Set debe contener nombres de miembro calificados o no calificados, o un conjunto de tuplas que contengan nombres de miembro calificados {}o no calificados entre llaves. Esta marca se utiliza para reducir el riesgo de ataques por inyección de código a través de la cadena especificada. Si se proporciona una cadena que no se resuelve directamente en nombres de miembro calificados o no calificados, aparece el siguiente error: "Se infringieron las restricciones impuestas por la marca CONSTRAINED en la función STRTOSET."  
  
-   Cuando no se utiliza la marca CONSTRAINED, la especificación de conjunto especificada se puede resolver en una expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
-   Para entender mejor las diferencias entre los conjuntos y los miembros, vea Usar expresiones de conjuntos y Usar expresiones de miembros.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelve el conjunto de miembros de la jerarquía de atributo State-provincia mediante la función **StrToSet** . La especificación de conjunto proporciona una expresión de conjunto MDX válida.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 El ejemplo siguiente devuelve un error debido a la marca CONSTRAINED. Mientras que la especificación de conjunto proporciona una expresión de conjunto MDX válida, la marca CONSTRAINED necesita nombres de miembro calificados o no calificados en la especificación de conjunto.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 El ejemplo siguiente devuelve la medida Reseller Sales Amount para los países Germany y Canada. La especificación de conjunto proporcionada en la cadena especificada contiene nombres de miembro calificados, tal y como exige la marca CONSTRAINED.  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
