---
title: "CALCULATE (instrucción MDX) | Documentos de Microsoft"
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
f1_keywords: CALCULATE
dev_langs: kbMDX
helpviewer_keywords: CALCULATE statement
ms.assetid: 41e196a1-d49e-487b-a42a-73e5d441ed1b
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a7bc4b283d3874b68c4bbe532bc32dcf4014896f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-scripting---calculate"></a>Scripting de MDX - calcular
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Llena cada celda de un cubo con un valor agregado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Argumentos  
 None  
  
## <a name="remarks"></a>Comentarios  
 La instrucción CALCULATE se incluye automáticamente como la primera instrucción de un script MDX de un cubo al crearlo mediante [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. La instrucción CALCULATE indica que se agregue cada celda del cubo comenzando por las celdas de menor granularidad. Después de agregar una celda, si se llenan celdas de menor granularidad mediante expresiones, eso repercute en el valor agregado de las celdas de mayor granularidad. Casi siempre se prefiere realizar esta agregación, pero se puede eliminar o hacer que otras instrucciones se ejecuten antes que esta instrucción.  
  
 La instrucción CALCULATE no se puede incluir en un subcubo anidado del script MDX. Un subcubo anidado se define mediante la instrucción SCOPE. Para obtener más información acerca de la instrucción SCOPE, vea [instrucción SCOPE &#40; MDX &#41; ](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Los miembros calculados no se agregan.  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de Scripting de MDX &#40; MDX &#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Aspectos básicos de Scripting de MDX &#40; Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Definir asignaciones y otros comandos de script](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
