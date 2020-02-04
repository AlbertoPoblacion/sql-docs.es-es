---
title: Agregar, mover o eliminar un cuadro de texto (Generador de informes y SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 09a8fd213f8bebd171a9e9fa2427345e677523a5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "65581955"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a>Agregar, mover o eliminar un cuadro de texto (Generador de informes y SSRS)
  Los cuadros de texto son los elementos de informe más usados en los informes paginados de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] . Puede agregar un cuadro de texto al cuerpo del informe para mostrar información como títulos, opciones de parámetros, campos integrados y fechas.  
  
 Cada celda de una tabla o matriz es en realidad un cuadro de texto. Casi todos los datos de informe mostrados en un informe con tablas y matrices son el resultado de la evaluación por parte del procesador de informes del contenido de cada cuadro de texto del informe. Como tal, puede dar formato a las celdas de la misma manera que daría formato a otros cuadros de texto que estuvieran fuera de la región de datos.  
  
 Para agregar un cuadro de texto a una región de datos de lista, debe agregar primero el cuadro de texto y, a continuación, arrastrarlo a la lista.  
  
> [!NOTE]  
>  Al hacer clic en un cuadro de texto, puede editar inmediatamente el texto de ese cuadro. Para seleccionar el propio cuadro de texto, no el texto que contiene, presione ESC.  
  
## <a name="to-add-a-text-box"></a>Para agregar un cuadro de texto  
  
1.  En la vista Diseño, en la pestaña **Insertar** , haga clic en **Cuadro de texto**.  
  
2.  En la superficie de diseño, haga clic y, a continuación, arrastre un cuadro hasta obtener el tamaño deseado del cuadro de texto.  
  
## <a name="to-add-a-text-box-in-a-list"></a>Para agregar un cuadro de texto a una lista  
  
1.  En la vista de diseño de informe, en la pestaña **Insertar** , haga clic en **Lista**.  
  
2.  En la superficie de diseño, haga clic y, a continuación, arrastre un cuadro hasta obtener el tamaño deseado de la lista.  
  
3.  En la pestaña **Insertar** , haga clic en **Cuadro de texto**.  
  
4.  En la superficie de diseño, haga clic en cuadro y, a continuación, arrástrelo hasta obtener el tamaño deseado dentro de la lista que agregó en el paso 1.   
  
5.  Para confirmar que el cuadro de texto se ha anidado correctamente dentro de la lista, selecciónelo.  
  
    > [!NOTE]  
    >  Si hace clic en el cuadro de texto y está en modo de edición, presione ESC para seleccionar el cuadro de texto.  
  
6.  En el panel Propiedades, compruebe que la propiedad **Parent** es el rectángulo que se agregó automáticamente a la región de datos de lista.  
  
    > [!NOTE]  
    >  Si el panel de propiedades no está visible, en la pestaña **Ver** seleccione **Propiedades** .  
  
## <a name="to-move-a-text-box"></a>Para mover un cuadro de texto  
  
1.  En la vista de diseño de gráfico, haga clic en un espacio vacío del cuadro de texto para seleccionarlo.  
  
    > [!NOTE]  
    >  Si hace clic en el cuadro de texto y está en modo de edición, presione ESC para seleccionar el cuadro de texto.  
  
2.  Haga clic en el identificador del cuadro de texto y arrastre el cuadro de texto a la nueva ubicación.   
    O bien, use las teclas de dirección para mover horizontal o verticalmente un cuadro de texto seleccionado. Para mover el cuadro de texto en incrementos más pequeños en la superficie de diseño, mantenga presionada la tecla CTRL mientras usa las teclas de dirección.  
  
## <a name="to-delete-a-text-box"></a>Para eliminar un cuadro de texto  
  
1.  En la vista de diseño de gráfico, haga clic con el botón derecho en un espacio vacío del cuadro de texto para seleccionarlo y, después, haga clic en **Eliminar**. O bien, haga clic en un espacio vacío del cuadro de texto y, a continuación, presione SUPRIMIR.  
  
    > [!NOTE]  
    >  Si hace clic en el cuadro de texto y está en modo de edición, presione ESC para seleccionar el cuadro de texto.  
  
## <a name="see-also"></a>Consulte también  
 [Cuadros de texto &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Métodos abreviados de teclado &#40;Generador de informes&#41;](../../reporting-services/report-builder/keyboard-shortcuts-report-builder.md)  
  
  
