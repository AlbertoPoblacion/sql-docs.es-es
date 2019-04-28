---
title: DrillupLevel (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e00851557b502bda3a98763eff4bac9c3abdccff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690775"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)


  Reduce el detalle de los miembros de un conjunto por debajo de un nivel especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Expresión MDX (Expresiones multidimensionales) válida que devuelve un conjunto.  
  
 *Level_Expression*  
 Expresión MDX válida que devuelve un nivel.  
  
## <a name="remarks"></a>Comentarios  
 El **DrillupLevel** función devuelve un conjunto de miembros se organiza jerárquicamente según los miembros incluidos en el conjunto especificado. Se mantiene el orden entre los miembros del conjunto especificado.  
  
 Si se especifica una expresión de nivel, el **DrillupLevel** función crea el conjunto mediante la recuperación solo aquellos miembros que están por encima del nivel especificado. Si se especifica una expresión de nivel y no hay un miembro del nivel especificado representado en el conjunto especificado, se devuelve el conjunto especificado.  
  
 Si no se especifica una expresión de nivel, la función crea el conjunto mediante la recuperación de solo aquellos miembros que se encuentran un nivel por encima del nivel más bajo de la primera dimensión a la que se hace referencia en el conjunto especificado.  
  
## <a name="example"></a>Ejemplo  
 EL ejemplo siguiente devuelve el conjunto de miembros del primer conjunto que están por encima del nivel Subcategory.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
