---
title: EXISTING, palabra clave (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ceaeac711ed30028dab3bc09827df9b6ae1f0e0a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725359"
---
# <a name="existing-keyword-mdx"></a>EXISTING (Palabra clave, MDX)
  Exige que un conjunto especificado se evalúe en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Argumentos  
 *Set_Expression*  
 Una expresión de conjunto de MDX (Expresiones multidimensionales) válida.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, los conjuntos se evalúan en el contexto del cubo que contiene los miembros del conjunto. La palabra clave `Existing` fuerza a un conjunto especificado a evaluarse en el contexto actual.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve el recuento de los distribuidores cuyas ventas han disminuido en el período de tiempo anterior, de acuerdo con los valores de los miembros State-Province seleccionados por el usuario, evaluados mediante la función `Aggregate`. La palabra clave [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) y [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) se usan para devolver valores para las ventas que han disminuido en las categorías de productos de la dimensión Product. El `Existing` palabra clave fuerza el conjunto en el `Filter` función va a evaluar en el contexto actual, es decir, para los miembros Washington y Oregon de la jerarquía de atributo State-Province.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx)   
 [Filter &#40;MDX&#41;](/sql/mdx/filter-mdx)   
 [Properties &#40;MDX&#41;](/sql/mdx/properties-mdx)   
 [DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx)   
 [Referencia de funciones MDX &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
