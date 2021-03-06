---
title: Establecer el contexto de cubo en una consulta (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 570d327b099508fc98f0e247b919fb222db54509
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>Establecer el contexto de cubo en una consulta (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Las consultas de MDX se ejecutan en un contexto de cubo especificado. En este contexto se definen los miembros que se evalúan mediante las expresiones contenidas en la consulta.  
  
 En la instrucción SELECT, la cláusula FROM determina el contexto de cubo. Este contexto puede ser todo el cubo o simplemente un subcubo de ese cubo. Al especificar el contexto de cubo mediante la cláusula FROM, puede utilizar funciones adicionales para expandir o restringir ese contexto.  
  
> [!NOTE]  
>  Las instrucciones SCOPE y CALCULATE también le permiten gestionar el contexto de cubo desde un script de MDX. Para más información, vea [Aspectos básicos de scripting MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
## <a name="from-clause-syntax"></a>Sintaxis de la cláusula FROM  
 La siguiente sintaxis describe la cláusula FROM:  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 En esta sintaxis, observe que es la cláusula `<SELECT subcube clause>` la que describe el cubo o el subcubo en el que se ejecuta la instrucción SELECT.  
  
 Un sencillo ejemplo de una cláusula FROM sería una que se ejecutase contra la totalidad del cubo de ejemplo Adventure Works. Esa cláusula FROM tendría el formato siguiente:  
  
```  
FROM [Adventure Works]  
```  
  
 Para más información sobre la cláusula FROM de la instrucción MDX SELECT, vea [SELECT &#40;Instrucción, MDX&#41;](../../../mdx/mdx-data-manipulation-select.md).  
  
## <a name="refining-the-context"></a>Refinar el contexto  
 Aunque la cláusula FROM especifica el contexto de cubo para un solo cubo, esto no debe limitarle a la hora de trabajar con datos de más de un cubo de forma simultánea.  
  
 Puede utilizar la función de MDX [LookupCube](../../../mdx/lookupcube-mdx.md) para recuperar datos de cubos que se encuentren fuera del contexto de cubo. Además, funciones como [Filter](../../../mdx/filter-mdx.md) están disponibles para permitir la restricción temporal del contexto mientras se evalúa la consulta.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de consulta MDX &#40; Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
