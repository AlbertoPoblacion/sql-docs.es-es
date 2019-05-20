---
title: Usar constantes en expresiones (Generador de informes y SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 52b3fd24cf36aebeb87e41885b9e992fca1338a3
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581600"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a>Usar constantes en expresiones (Generador de informes y SSRS)
  Una constante consta de texto literal o de texto predefinido. El procesador de informes tiene acceso a las constantes predefinidas para que cuando se incluyan en una expresión, los valores que representan se sustituyan en la expresión antes de evaluarla.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a>Texto literal  
 En una expresión, el texto literal es texto que está encerrado entre comillas dobles. También puede escribir directamente el texto en un cuadro de texto sin las comillas dobles cuando no forma parte de una expresión. Si el valor del cuadro de texto no comienza por un signo igual (=), el texto se trata como texto literal. En la tabla siguiente se muestran varios ejemplos de texto literal en una expresión.  
  
|Constante|Texto que se muestra|Texto de la expresión|  
|--------------|------------------|---------------------|  
|Report run at:|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|Adventure Works Cycles|Adventure Works Cycles|Adventure Works Cycles|  
|[Texto que se muestra entre corchetes]|\\[Texto que se muestra entre corchetes\\]|[Texto que se muestra entre corchetes]|  
  
## <a name="rdl-constants"></a>Constantes RDL  
 Puede usar constantes definidas en lenguaje RDL (Report Definition Language) en una expresión. En el cuadro de diálogo **Expresión** , las constantes aparecen al crear una expresión para una propiedad de informe que solo acepta ciertos valores válidos, también conocidos como tipos enumerados. En la tabla siguiente se muestran dos ejemplos.  
  
|Propiedad|Descripción|Valores|  
|--------------|-----------------|------------|  
|TextAlign|Valores válidos para alinear texto en un cuadro de texto.|General, Left, Center, Right|  
|BorderStyle|Valores válidos para una línea agregada a un informe.|Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot|  
  
## <a name="visual-basic-constants"></a>Constantes de Visual Basic  
 Puede usar constantes definidas en la biblioteca en tiempo de ejecución de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] en una expresión. Por ejemplo, puede usar la constante **DateInterval.Day**. La siguiente expresión para la fecha 10 de enero de 2008 devuelve el número 10:  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a>Constantes CLR  
 Puede usar constantes definidas en clases de Common Language Runtime (CLR) de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en una expresión. En la tabla siguiente se muestra un ejemplo de un color definido por el sistema.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|MistyRose|Al crear una expresión para una propiedad de informe que está basada en el color de fondo, puede especificar un color por su nombre. La lista de los nombres válidos se encuentra en el cuadro de diálogo **Expresión** .|  
  
## <a name="see-also"></a>Consulte también  
 [Expresión (cuadro de diálogo)](https://msdn.microsoft.com/library/e6c74ccb-4594-4d4f-b958-618d710e34eb)   
 [Expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Expresión &#40;cuadro de diálogo del Generador de informes&#41;](https://msdn.microsoft.com/library/e89c4d97-5d41-4b55-8695-79329edac15d)  
  
  
