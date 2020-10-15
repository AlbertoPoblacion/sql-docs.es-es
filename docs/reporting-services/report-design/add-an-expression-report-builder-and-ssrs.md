---
title: Adición de una expresión (Generador de informes) | Microsoft Docs
description: Obtenga información sobre cómo usar expresiones para definir propiedades de elementos de informe, filtros y valores de parámetro en el Generador de informes.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b5fc151010d455bb3fee29b92bc86adf24da32f4
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91935144"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a>Agregar una expresión (Generador de informes y SSRS)
  Las expresiones se usan en los informes para definir propiedades de elementos de informe, filtros, grupos, criterios de ordenación, cadenas de conexión y valores de parámetros. Las expresiones comienzan por un signo igual (=) y se escriben en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. El procesador de informes, que combina el resultado de la evaluación con elementos de diseño de informe, evalúa las expresiones en tiempo de ejecución.  
  
 Las expresiones pueden ser simples o complejas. Una expresión simple hace referencia a un único elemento de una colección integrada. Las expresiones complejas pueden contener constantes, operadores, elementos de recopilación globales y llamadas a funciones. Para más información, vea [Expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a>Para agregar una expresión a un cuadro de texto  
  
-   En la vista **Diseño** , haga clic en el cuadro de texto de la superficie de diseño al que desea agregar una expresión.  
  
    -   Si se trata de una expresión simple, escriba el texto para mostrar de la expresión en el cuadro de texto. Por ejemplo, para el campo de conjunto de datos Sales, escriba `[Sales]`.  
  
    -   Si se trata de una expresión compleja, haga clic con el botón derecho en el cuadro de texto y seleccione **Expresión**. Se abre el cuadro de diálogo **Expresión** . Escriba o cree de forma interactiva la expresión después del signo '=' en el panel de expresión y, a continuación, haga clic en Aceptar.  
  
         La expresión aparece en la superficie de diseño como `<<Expr>>`.  
  
## <a name="see-also"></a>Consulte también  
 [Aplicar formato a texto y a marcadores de posición &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Cuadros de texto &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Usar expresiones en informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Ejemplos de ecuaciones de filtro &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Ejemplos de expresión de grupo &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Expresión &#40;cuadro de diálogo del Generador de informes&#41;](./expressions-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Agregar código a un informe &#40;SSRS&#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)  
  
