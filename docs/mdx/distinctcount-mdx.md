---
title: DistinctCount (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DISTINCTCOUNT
dev_langs: kbMDX
helpviewer_keywords: DistinctCount function
ms.assetid: b1a725a6-d81e-4777-a2f7-ecbc39f9b1e8
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ba80869d48f1ad7e3b4ebe3151b2497e8b75ed68
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="distinctcount-mdx"></a>DistinctCount (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Devuelve el número de tuplas distintas y no vacías de un conjunto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DistinctCount(Set_Expression)  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
## <a name="remarks"></a>Comentarios  
 El **DistinctCount** función es equivalente a `Count(Distinct(Set_Expression), EXCLUDEEMPTY)`.  
  
## <a name="examples"></a>Ejemplos  
 La consulta siguiente muestra el modo de usar la función DistinctCount:  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `*`  
  
 `{([Date].[Calendar].[Date].&[20010701],[Measures].[Internet Sales Amount] )}`  
  
 `//Returns the value 3 because Internet Sales Amount is null`  
  
 `//for the UK on the date specified`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `DISTINCTCOUNT(MySet)`  
  
 `SELECT {MEASURES.SETDISTINCTCOUNT} ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vea también  
 [Número de &#40; Conjunto de &#41; &#40; MDX &#41;](../mdx/count-set-mdx.md)   
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
