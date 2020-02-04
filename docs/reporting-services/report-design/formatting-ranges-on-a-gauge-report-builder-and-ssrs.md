---
title: Aplicar formato a los rangos de un medidor (Generador de informes y SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: eebf7f66e968ec2c7c3d0dcca168eb79fbbc3797
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "65575599"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>Aplicar formato a los rangos de un medidor (Generador de informes y SSRS)
 En un informe paginado de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , un intervalo de medidor es una zona o área en la escala del medidor que indica una subsección importante de valores en el medidor. Use un intervalo de medidor para indicar visualmente el momento en el que el valor de puntero entra en cierto intervalo de valores. Los intervalos están definidos por un valor inicial y un valor final.  
  
 También se pueden usar intervalos para definir secciones diferentes de un medidor. Por ejemplo, en un medidor con valores comprendidos entre 0 y 10, puede definir un intervalo rojo para los valores comprendidos entre 0 y 3, un intervalo amarillo para los valores comprendidos entre 4 y 7 y un intervalo verde para los valores comprendidos entre 8 y 10. Si el valor inicial especificado es mayor que el valor final especificado, se intercambian los valores para que el valor inicial sea el valor final y el valor final sea el valor inicial.  
  
 Puede colocar el intervalo del mismo modo que coloca los punteros en una escala. Las propiedades **Posición** y **Distancia desde escala** determinan la posición del intervalo. Para obtener más información, vea [Medidores &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Aplicar formato a las escalas de un medidor &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Aplicar formato a los punteros de un medidor &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Establecer un valor mínimo o máximo en un medidor &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [Tutorial: Agregar un KPI al informe &#40;Generador de informes&#41;](../../reporting-services/tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [Medidores &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
