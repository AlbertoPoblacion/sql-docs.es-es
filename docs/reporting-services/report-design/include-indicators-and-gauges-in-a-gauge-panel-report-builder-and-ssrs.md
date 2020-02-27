---
title: Inclusión de indicadores y medidores en un panel de medidores (Generador de informes) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0d9f5cf2619ea26c56f6511b829b5da524776602
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "77082042"
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a>Incluir indicadores y medidores en un panel de medidores (Generador de informes y SSRS)
  El panel de medidores es el contenedor de nivel superior que contiene uno o más medidores e indicadores. Los indicadores se pueden incrustar en los medidores o colocar a su lado en el panel de medidores.  
  
 Si el indicador y el medidor son adyacentes en el panel de medidores y muestran datos de campos distintos, podría desear agregar etiquetas para dejar claro qué datos comunican el medidor y el indicador.  
  
 Las opciones del medidor y el indicador se pueden establecer mediante expresiones. Para más información, vea [Expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a>Para incrustar un indicador en un medidor  
  
1.  Abra un informe existente o cree un informe que contenga una tabla y matriz con los datos que desea mostrar.   
  
2.  Inserte una columna en la tabla o matriz. Para más información, vea [Insertar o eliminar una columna &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  En la pestaña **Insertar** , en el grupo **Regiones de datos** , haga clic en **Medidor**y, a continuación, en una de las celdas de la nueva columna. Aparece el cuadro de diálogo **Seleccionar tipo de medidor** .  
  
4.  Haga clic en **Radial**. Se selecciona el primer medidor radial.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Haga clic en el medidor. El panel **Medidor de datos** se abre.  
  
7.  En el área **Valores** , en el cuadro de lista **(Sin especificar)** , haga clic en el campo cuyos valores quiere que se muestren en el medidor. Si lo prefiere, puede arrastrar el campo que desea utilizar desde el conjunto de datos de informe.  
  
8.  Haga clic con el botón derecho en el medidor, haga clic en **Agregar indicador**y, después, haga clic en **Secundario**. Se abre el cuadro de diálogo **Seleccionar estilo de indicador** .  
  
9. En el cuadro de diálogo **Seleccionar estilo de indicador** , en el panel izquierdo, haga clic en el tipo de indicador que desea y, a continuación, haga clic en el indicador establecido.  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
11. Haga clic en el indicador. El panel **Medidor de datos** se abre.  
  
12. En el área **Valores** , en el cuadro de lista **(Sin especificar)** , haga clic en el campo cuyos valores quiera mostrar como un indicador. Si lo prefiere, puede arrastrar el campo que desea utilizar desde el conjunto de datos de informe.  
  
     El campo puede ser el mismo que el utilizado en el medidor, u otro distinto.  
  
13. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a>Para mostrar un indicador y medidor en paralelo  
  
1.  Abra un informe existente o cree un informe que contenga una tabla y matriz con los datos que desea mostrar.  
  
2.  Inserte una columna en la tabla o matriz. Para más información, vea [Insertar o eliminar una columna &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  En la pestaña **Insertar** , en el grupo **Regiones de datos** , haga clic en **Medidor**y, a continuación, en una de las celdas de la columna que ha insertado. Aparecerá el cuadro de diálogo **Seleccionar tipo de medidor** .  
  
4.  Haga clic en **Radial**. Se selecciona el primer medidor radial.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Haga clic en el medidor. El panel **Medidor de datos** se abre.  
  
7.  En el área **Valores** , en el cuadro de lista **(Sin especificar)** , haga clic en el campo cuyos valores quiere que se muestren en el medidor. Si lo prefiere, puede arrastrar el campo que desea utilizar desde el conjunto de datos de informe.  
  
8.  Haga clic con el botón derecho en el medidor, haga clic en **Agregar indicador**y, después, haga clic en **Adyacente**. Se abre el cuadro de diálogo **Seleccionar estilo de indicador** .  
  
9. En el cuadro de diálogo **Seleccionar estilo de indicador** , en el panel izquierdo, haga clic en el tipo de indicador que desea y, a continuación, haga clic en el indicador establecido.  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
11. Haga clic en el indicador. El panel **Medidor de datos** se abre.  
  
12. En el área **Valores** , en el cuadro de lista **(Sin especificar)** , haga clic en el campo cuyos valores quiera mostrar como un indicador. Si lo prefiere, puede arrastrar el campo que desea utilizar desde el conjunto de datos de informe.  
  
     El campo puede ser el mismo que el utilizado en el medidor, u otro distinto.  
  
13. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
14. Haga clic con el botón derecho en el panel de medidores y, después, haga clic en **Agregar etiqueta**. Se agregará una etiqueta al panel de medidores. Realice los mismos pasos una vez más.  
  
     En el panel de medidores habrá dos etiquetas.  
  
15. Arrastre cada etiqueta hasta un lugar próximo al medidor o indicador.  
  
16. Haga clic con el botón derecho en la etiqueta próxima al medidor, haga clic en **Propiedades de etiqueta**y escriba el texto que quiera en el cuadro **Texto** .  
  
17. Haga clic con el botón derecho en la etiqueta próxima al indicador, haga clic en **Propiedades de etiqueta**y escriba el texto que quiera en el cuadro **Texto** .  
  
18. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Indicadores &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
