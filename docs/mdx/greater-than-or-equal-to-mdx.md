---
title: '&gt;= (Mayor o igual que) (MDX) | Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14babb777aa4c5de85c0a0324621aebf91cb5367
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62653485"
---
# <a name="gt-greater-than-or-equal-to-mdx"></a>&gt;= (Mayor o igual que) (MDX)


  Realiza una operación de comparación que determina si el valor de una expresión multidimensional (MDX) es superior o igual al valor de otra expresión MDX.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
MDX_Expression >= MDX_Expression  
```  
  
#### <a name="parameters"></a>Parámetros  
 *MDX_Expression*  
 Una expresión MDX válida.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor booleano basado en las condiciones siguientes:  
  
-   **True** si el primer parámetro tiene un valor que es mayor o igual que el valor del segundo parámetro.  
  
-   **false** si el primer parámetro tiene un valor que es menor que el valor del segundo parámetro.  
  
-   **True** si ambos parámetros son null o si un parámetro es null y el otro parámetro es 0.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra el uso de este operador.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is greater than or equal to 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] >= .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
    NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[HighGPM])  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de operadores de MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
