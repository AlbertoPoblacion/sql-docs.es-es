---
title: Uso de expresiones escalares | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a80933b1a9845ec2676fba470ed39e06ee7f4ad8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251413"
---
# <a name="using-scalar-expressions"></a>Usar expresiones escalares


  En las expresiones multidimensionales (MDX), una expresión escalar es un elemento de la sintaxis MDX que, al ser evaluado, devuelve un solo valor en el contexto de la evaluación.  
  
 En MDX, las expresiones escalares incluyen expresiones de cadena, numéricas y de fecha.  
  
 Las expresiones escalares se utilizan normalmente en definiciones de miembros calculados, puesto que los miembros calculados deben devolver un valor escalar. La consulta siguiente muestra ejemplos de miembros calculados de la dimensión Measures que utilizan distintos tipos de expresiones escalares:  
  
 `WITH`  
  
 `MEMBER MEASURES.NumericValue AS 10`  
  
 `MEMBER MEASURES.NumericExpression AS 10 + 10`  
  
 `MEMBER MEASURES.NumericExpressionBasedOnMeasure AS [Measures].[Internet Sales Amount] + 10`  
  
 `MEMBER MEASURES.StringValue AS "10"`  
  
 `MEMBER MEASURES.ConcatenatedString AS "10" + "10"`  
  
 `MEMBER MEASURES.StringFunction AS MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.TodaysDate AS NOW()`  
  
 `SELECT`  
  
 `{MEASURES.NumericValue,MEASURES.NumericExpression,MEASURES.NumericExpressionBasedOnMeasure,`  
  
 `MEASURES.StringValue, MEASURES.ConcatenatedString, MEASURES.StringFunction, MEASURES.TodaysDate}`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 El único tipo de datos que puede devolver una medida, ya sea calculada o de cualquier otro tipo, es el tipo OLE Variant. Por lo tanto, es posible que en ocasiones tenga que convertir un valor de medida en un tipo determinado para recibir el comportamiento que espera. La consulta siguiente muestra un ejemplo de esto:  
  
```  
WITH  
//Two calculated measures that return strings  
MEMBER MEASURES.NumericString1 AS "10"  
MEMBER MEASURES.NumericString2 AS "10"  
//In this case, the + operator acts to concatenate the strings  
MEMBER MEASURES.Concatenation AS MEASURES.NumericString1 + MEASURES.NumericString2  
//Casting one value to an integer with the CINT function causes the second measure  
//to be treated as an integer too, so that the + operator now acts to add the values  
MEMBER MEASURES.Addition AS CINT(MEASURES.NumericString1) + MEASURES.NumericString2  
SELECT  
{MEASURES.NumericString1,MEASURES.NumericString2,MEASURES.Concatenation,MEASURES.Addition }  
ON COLUMNS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Expressions &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
