---
title: Instrucción UPDATE CUBE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 248605667afe073e2261585444555a1d254ffc26
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794123"
---
# <a name="mdx-data-manipulation---update-cube"></a>Manipulación de datos de MDX: UPDATE CUBE


  La instrucción UPDATE CUBE se emplea para reescribir datos en cualquier celda de un cubo que se agrega a su primario mediante la agregación SUM. Para obtener más información y un ejemplo, vea "Descripción de las asignaciones" en esta entrada de blog: [Compilar una aplicación de reescritura con Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *Cube_Name*  
 Cadena válida que proporciona el nombre de un cubo.  
  
 *Tuple_Expression*  
 Expresión MDX válida que devuelve una tupla.  
  
 *New_Value*  
 Una expresión numérica válida.  
  
 *Weight_Expression*  
 Expresión numérica MDX (Expresiones multidimensionales) válida que devuelve un valor decimal entre 0 y 1.  
  
## <a name="remarks"></a>Comentarios  
 Puede actualizar el valor de una celda hoja o de una celda no hoja especificada de un cubo, asignando opcionalmente el valor de una celda no hoja especificada a través de las celdas hoja dependientes. La celda especificada por la expresión de tupla puede ser cualquier celda válida del espacio multidimensional (es decir, la celda no tiene que ser una celda hoja). Sin embargo, debe agregarse la celda con el [suma](../mdx/sum-mdx.md) función de agregado y no puede contener un miembro calculado en la tupla que se usa para identificar la celda.  
  
 Puede resultar útil pensar en el **UPDATE CUBE** instrucción como una subrutina que generará automáticamente una serie de operaciones de reescritura de celda individual a las celdas hoja y no hoja que se acumularán en la suma especificada.  
  
 La siguiente es una descripción de los métodos de asignación.  
  
 **USE_EQUAL_ALLOCATION:** Cada celda hoja que contribuye a la celda actualizada se asignará un valor igual basado en la siguiente expresión.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:** Cada celda hoja que contribuye a la celda actualizada se cambiará de acuerdo con la siguiente expresión.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:** Cada celda hoja que contribuye a la celda actualizada se asignará un valor igual a la que se basa en la siguiente expresión.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:** Cada celda hoja que contribuye a la celda actualizada se cambiará de acuerdo con la siguiente expresión.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Si no se especifica una expresión de peso, el **UPDATE CUBE** instrucción usa implícitamente la expresión siguiente.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Una expresión de peso debería expresarse como un valor decimal entre cero (0) y 1. Este valor especifica la proporción del valor asignado que desea asignar a las celdas hoja afectadas por la asignación. El programador de la aplicación cliente es el responsable de crear expresiones con valores agregados de resumen que sean iguales al valor asignado de la expresión.  
  
> [!CAUTION]  
>  La aplicación cliente debe considerar la asignación de todas las dimensiones de forma simultánea para evitar posibles resultados inesperados, incluidos los valores de resumen incorrectos o los datos incoherentes.  
  
 Cada **UPDATE CUBE** asignación debe considerarse atómicas para fines transaccionales. Eso significa que si alguna de las operaciones de asignación no tiene éxito por alguna razón, como un error en una fórmula o una infracción de seguridad, se producirá un error de toda la operación UPDATE CUBE. Antes de procesar los cálculos de las operaciones de asignación individuales, se toma una instantánea de los datos para garantizar que los cálculos resultantes sean correctos.  
  
> [!CAUTION]  
>  Cuando se utiliza en una medida que contiene enteros, el método USE_WEIGHTED_ALLOCATION puede devolver resultados imprecisos causados por cambios en el redondeo incremental.  
  
> [!IMPORTANT]  
>  Si las celdas actualizadas no se superponen, se puede utilizar la propiedad de la cadena de conexión **Update Isolation Level** para mejorar el rendimiento de UPDATE CUBE.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Instrucciones de manipulación de datos MDX &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
