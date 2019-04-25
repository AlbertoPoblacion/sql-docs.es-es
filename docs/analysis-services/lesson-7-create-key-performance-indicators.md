---
title: 'Lección 7: Creación de indicadores clave de rendimiento | Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ecfedbbc4b7e606f1589f2b5415c5355bb0d95e1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62523369"
---
# <a name="lesson-7-create-key-performance-indicators"></a>Lección 7: Crear indicadores clave de rendimiento
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

En esta lección, creará indicadores clave de rendimiento (KPI). Los KPI miden el rendimiento de un valor, definido por una medida *base* , con respecto a un valor de *destino* , también definido por una medida o por un valor absoluto. En aplicaciones cliente de informes, los KPI pueden proporcionar a los profesionales del negocio una manera rápida y sencilla de identificar un resumen de logros empresariales o tendencias. Para obtener más información, consulte [KPI](../analysis-services/tabular-models/kpis-ssas-tabular.md).  
  
Tiempo estimado para completar esta lección: **15 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [Lección 6: Crear medidas](../analysis-services/lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Crear indicadores clave de rendimiento  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Para crear un KPI InternetCurrentQuarterSalesPerformance  
  
1.  En el Diseñador de modelos, haga clic en el **FactInternetSales** tabla (pestaña).  
  
2.  En la cuadrícula de medidas, haga clic en una celda vacía.  
  
3.  En la barra de fórmulas situada encima de la tabla, escriba la siguiente fórmula: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IFERROR([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Esta medida servirá como la medida base del KPI.  
  
4.  Haga clic en **InternetCurrentQuarterSalesPerformance** > **crear KPI**.   
  
5.  En el cuadro de diálogo indicador clave de rendimiento (KPI), en **destino** seleccione **valor absoluto**y, a continuación, escriba **1.1**.  
  
7.  En el campo de control deslizante situado abajo a la izquierda, escriba **1**y, en el de arriba a la derecha, escriba **1.07**.  
  
8.  En **Seleccionar el estilo de icono**, seleccione el tipo de icono de rombo (rojo), triángulo (amarillo), círculo (verde).
  
    ![as-tabular-lesson7-kpi](../analysis-services/media/as-tabular-lesson7-kpi.png)
    
    > [!TIP]  
    > Observe la **descripciones** etiqueta debajo de los estilos de icono disponibles. Utilice esto para especificar descripciones para los distintos elementos KPI para que sean más fáciles de identificar en las aplicaciones cliente.  
  
9. Haga clic en **Aceptar** para completar el KPI.  
  
    En la cuadrícula de medidas, observe el icono situado junto a la **InternetCurrentQuarterSalesPerformance** medida. Este icono indica que esta medida actúa como valor base de un KPI.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>Para crear un KPI InternetCurrentQuarterMarginPerformance  
  
1.  En la cuadrícula de medidas para la **FactInternetSales** de tabla, haga clic en una celda vacía.  
  
2.  En la barra de fórmulas situada encima de la tabla, escriba la siguiente fórmula:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Haga clic en **InternetCurrentQuarterMarginPerformance** > **crear KPI**.  
  
4.  En el cuadro de diálogo indicador clave de rendimiento (KPI), en **destino** seleccione **valor absoluto**y, a continuación, escriba **1.25**.   
  
5.  En **Definir umbrales de estado**, desplace el campo de control deslizante de abajo a la izquierda hasta que el campo muestre **0.8**y el de arriba a la derecha hasta que muestre **1.03**.  
  
6.  En **Seleccionar estilo de icono**, seleccione el tipo de icono de rombo (rojo), triángulo (amarillo) y círculo (verde), y haga clic en **Aceptar**.  
  
## <a name="whats-next"></a>¿Qué sigue?
Vaya a la lección siguiente: [Lección 8: Crear perspectivas](../analysis-services/lesson-8-create-perspectives.md).
  
  
