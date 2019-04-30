---
title: TopCount (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fa8edcf8af510a41affdcbcc9924edf69cf4c220
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63228044"
---
# <a name="topcount-mdx"></a>TopCount (MDX)


  Ordena un conjunto de forma descendente y devuelve el número de elementos especificado con los valores más altos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
 *Count*  
 Expresión numérica válida que especifica el número de tuplas que serán devueltas.  
  
 *Numeric_Expression*  
 Expresión numérica válida que suele ser una expresión MDX de las coordenadas de celdas que devuelven un número.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica una expresión numérica, la **TopCount** función clasifica, en orden descendente, las tuplas del conjunto especificado por el conjunto especificado de acuerdo con el valor especificado por la expresión numérica, según se ha evaluado sobre especificado conjunto. Después de ordenar el conjunto, la **TopCount** función, a continuación, devuelve el número especificado de tuplas con el valor más alto.  
  
> [!IMPORTANT]  
>  Al igual que el [BottomCount](../mdx/bottomcount-mdx.md) función, el **TopCount** siempre rompe la jerarquía.  
  
 Si no se especifica una expresión numérica, la función devuelve el conjunto de miembros en orden natural, sin ordenamiento, comportándose como la [Head (MDX)](../mdx/head-mdx.md) función.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelven las 10 fechas superiores según Internet Sales Amount:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 El ejemplo siguiente devuelve, para la categoría Bike, los primeros cinco miembros del conjunto que contiene todas las combinaciones de miembros del nivel City de la jerarquía Geography de la dimensión Geography y los años fiscales de la jerarquía Fiscal de la dimensión Date, ordenados por la medida Reseller Sales Amount (comenzando por los miembros de este conjunto con la mayor cifra de ventas).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
