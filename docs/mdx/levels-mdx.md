---
title: Niveles (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e8edfdc3c6888c34dd789c521bc42c6b919e1a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63269954"
---
# <a name="levels-mdx"></a>Levels (MDX)


  Devuelve el nivel cuya posición en una dimensión o jerarquía se especifica mediante una expresión numérica, o cuyo nombre se especifica mediante una expresión de cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Argumentos  
 *Hierarchy_Expression*  
 Expresión MDX válida que devuelve una jerarquía.  
  
 *Level_Number*  
 Expresión numérica válida que especifica un número de nivel.  
  
 *Level_Name*  
 Expresión de cadena válida que especifica un nombre de nivel.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica un número de nivel, el **niveles** función devuelve el nivel asociado con la posición de base cero especificada.  
  
 Si se especifica un nombre de nivel, el **niveles** función devuelve el nivel especificado.  
  
> [!NOTE]  
>  Utilice la sintaxis de expresión de cadena para funciones definidas por el usuario.  
  
## <a name="examples"></a>Ejemplos  
 Los ejemplos siguientes muestran cada uno de los **niveles** sintaxis de función.  
  
### <a name="numeric"></a>Numérico  
 El ejemplo siguiente devuelve el nivel Country:  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 El ejemplo siguiente devuelve el nivel Country:  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
