---
title: CALCULAR (instrucción, MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a4a8be73a94ccbca1eb0deeacc0e7cc33c5cfaa6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003445"
---
# <a name="mdx-scripting---calculate"></a>Scripting de MDX: CALCULATE


  Llena cada celda de un cubo con un valor agregado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Argumentos  
 None  
  
## <a name="remarks"></a>Comentarios  
 La instrucción CALCULATE se incluye automáticamente como la primera instrucción de un script MDX de un cubo al crearlo mediante [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. La instrucción CALCULATE indica que se agregue cada celda del cubo comenzando por las celdas de menor granularidad. Después de agregar una celda, si se llenan celdas de menor granularidad mediante expresiones, eso repercute en el valor agregado de las celdas de mayor granularidad. Casi siempre se prefiere realizar esta agregación, pero se puede eliminar o hacer que otras instrucciones se ejecuten antes que esta instrucción.  
  
 La instrucción CALCULATE no se puede incluir en un subcubo anidado del script MDX. Un subcubo anidado se define mediante la instrucción SCOPE. Para obtener más información acerca de la instrucción SCOPE, vea [instrucción SCOPE &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Los miembros calculados no se agregan.  
  
## <a name="see-also"></a>Vea también  
 [Las instrucciones de Scripting de MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Aspectos básicos de scripting MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Definir asignaciones y otros comandos de script](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
