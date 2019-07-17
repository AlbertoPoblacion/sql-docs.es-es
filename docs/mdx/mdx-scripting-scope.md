---
title: ÁMBITO (instrucción, MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f355842999b505a97c3387ab9e51d3b651c3b7c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138279"
---
# <a name="mdx-scripting---scope"></a>Scripting de MDX: SCOPE


  Limita el ámbito de las instrucciones de Expresiones multidimensionales (MDX) especificadas a un subcubo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SCOPE(Subcube_Expression)   
   [ MDX_Statement ]  
END SCOPE  
  
Subcube_Expression ::=(Auxiliary_Subcube [, Auxiliary_Subcube,...n])  
  
Auxiliary_Subcube ::=   
        Limited_Set   
    | Root([dimension_name])   
    | Leaves([dimension_name])  
  
Limited_Set ::=   
        single_tuple   
    | member   
    | Common_Grain_Members   
    | hierarchy.members   
    | level.members   
    | {}   
    | Descendants  
            (  
                  Member  
         , [level  
         [  
            , SELF   
             | AFTER   
                          | BEFORE   
                          | SELF_AND_AFTER   
                          | SELF_AND_BEFORE   
                          | SELF_BEFORE_AFTER   
                          | LEAVES  
                  ]  
            )   
[* <limited set>]  
```  
  
## <a name="arguments"></a>Argumentos  
 *Subcube_Expression*  
 Una expresión de subcubo de MDX válida.  
  
 *MDX_Statement*  
 Una instrucción de MDX válida.  
  
 *Common_Grain_Members*  
 Una instrucción de MDX válida que se evalúa como los miembros que tienen la misma granularidad.  
  
 *single_tuple*  
 Una tupla sencilla.  
  
## <a name="remarks"></a>Comentarios  
 La instrucción SCOPE determina el subcubo que se verá afectado por la ejecución de una o más de las instrucciones MDX. A menos que una instrucción MDX esté contenida en una instrucción SCOPE, el ámbito implícito de una instrucción MDX es la totalidad del cubo.  
  
> [!NOTE]  
>  Los miembros oculto se exponen en las instrucciones SCOPE.  
  
 Las instrucciones SCOPE crearán subcubos que exponen "agujeros" con independencia de la **MDX Compatibility** configuración. Por ejemplo, la instrucción `Scope( Customer.State.members )` puede incluir estados de países o regiones que no contienen estados, pero para los que se han insertado miembros de marcadores de posición invisibles.  
  
 Los miembros calculados y los conjuntos con nombre creados en una instrucción SCOPE no se ven afectados por la instrucción SCOPE.  
  
## <a name="example"></a>Ejemplo  
 Solución de ejemplo el siguiente ejemplo, desde el script de cálculo MDX en el de Adventure Works, define el ámbito actual como fiscal quarter del año fiscal 2005 y la medida sales amount quota y, a continuación, asigna un valor a las celdas en el ámbito actual mediante el uso de la ** ParallelPeriod** función. En el ejemplo, a continuación, modifica el ámbito mediante otra instrucción SCOPE y, a continuación, realiza otra asignación mediante el [This (MDX)](../mdx/this-mdx.md) función.  
  
```  
Scope   
 (   
    [Date].[Fiscal Year].&[2005],  
    [Date].[Fiscal].[Fiscal Quarter].Members,  
    [Measures].[Sales Amount Quota]  
 ) ;     
  
   This = ParallelPeriod                               
          (   
             [Date].[Fiscal].[Fiscal Year], 1,  
             [Date].[Fiscal].CurrentMember   
          ) * 1.35 ;  
  
/*-- Allocate equally to months in FY 2002 -----------------------------*/  
  
  Scope   
  (   
     [Date].[Fiscal Year].&[2002],  
     [Date].[Fiscal].[Month].Members   
  ) ;     
  
    This = [Date].[Fiscal].CurrentMember.Parent / 3 ;     
  
  End Scope ;     
End Scope ;     
```  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones para scripting de MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
