---
title: + (Unión) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: be12a1af53957ab0d8f3347a0464dd987152bca0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63129825"
---
# <a name="union---mdx-operator-reference"></a>Unión - referencia de operadores de MDX


  Realiza una operación de conjunto que devuelve una unión entre dos conjuntos y elimina los miembros duplicados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Parámetros  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
## <a name="return-value"></a>Valor devuelto  
 Un conjunto que contiene los miembros de ambos conjuntos especificados.  
  
## <a name="remarks"></a>Comentarios  
 El **+ (unión)** operador es funcionalmente equivalente a la [unión &#40;MDX&#41; ](../mdx/union-mdx.md) función.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra el uso de este operador.  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de operadores de MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
