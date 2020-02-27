---
title: Importación de HTML en un informe (Generador de informes) | Microsoft Docs
ms.date: 12/06/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
description: Obtenga información sobre cómo usar un cuadro de texto para insertar en un informe texto con formato HTML recuperado de un campo del conjunto de datos.
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: dd0410ea-8839-4e8c-9944-8cdfe5465591
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2e89fb3f197037d757916a60d246c158d43b565b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "77082050"
---
# <a name="importing-html-into-a-report-report-builder-and-ssrs"></a>Importar HTML en un informe (Generador de informes y SSRS)
  Se puede usar un cuadro de texto para insertar en un informe texto con formato HTML recuperado de un campo de conjunto de datos. El texto puede proceder de cualquier expresión simple o compleja que se evalúe como HTML con un formato correcto. El texto con formato se puede representar en todos los formatos de salida compatibles, incluso PDF.  
  
 ![rs_HTMLFormatting](../../reporting-services/report-design/media/rs-htmlformatting.gif "rs_HTMLFormatting")  
  
 Esta ilustración se muestra texto con formato HTML en la vista de diseño de informe y el mismo texto como se representa cuando se ejecuta el informe.  
  
> [!NOTE]  
>  Cuando se importa texto que contiene marcado HTML, el cuadro de texto siempre debe analizar los datos en primer lugar. Dado que solo se admite un subconjunto de etiquetas HTML, el HTML que se muestra en el informe representado puede diferir del HTML original.  
  
 Para empezar rápidamente, vea [Tutorial: Dar formato a texto &#40;Generador de informes&#41;](../../reporting-services/tutorial-format-text-report-builder.md).  
  
## <a name="supported-html-tags"></a>Etiquetas HTML compatibles  
 La lista siguiente es una lista completa de las etiquetas que se representarán como HTML cuando se definan como texto de marcador de posición:  
  
-   Hipervínculos: \<A HREF>  
  
-   Fuentes: \<FONT>  
  
-   Encabezado, estilo y elementos de bloque: \<H{n}>, \<DIV>, \<SPAN>,\<P>, \<DIV>, \<LI>, \<HN>  
  
-   Formato de texto: \<B>, \<I>, \<U>, \<S>  
  
-   Administración de listas: \<OL>, \<UL>, \<LI>  
  
 Cualquier otra etiqueta de marcado HTML se omitirá durante el procesamiento del informe. Si el HTML representado por la expresión en el texto del marcador de posición no está bien formado, el marcador de posición se representa como texto simple. Todas las etiquetas HTML distinguen entre mayúsculas y minúsculas.  
  
 Si el texto del cuadro de texto contiene solo un bloque de texto, cualquier HTML del marcador de posición que defina elementos de bloque se representará correctamente. Sin embargo, si el cuadro de texto tiene varios bloques de texto, se omitirán las etiquetas HTML y los bloques de texto definirán la estructura del texto.  
  
 Si se definen varias etiquetas para el texto, y [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] detecta un conflicto entre las restricciones del HTML y del informe existente, solo se considerará HTML la etiqueta HTML más interna.  
  
 Para más información, vea [Agregar HTML a un informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/add-html-into-a-report-report-builder-and-ssrs.md).  
  
## <a name="limitations-of-cascading-style-sheet-attributes"></a>Limitaciones de los atributos de las hojas de estilos en cascada  
 Cuando se usan atributos de hoja de estilos en cascada (CSS), solo se define un conjunto básico de etiquetas. La lista siguiente es una lista de los atributos admitidos:  
  
-   text-align, text-indent  
  
-   font-family  
  
-   tamaño de fuente  
  
    -   Solo se admiten valores válidos de tamaño RDL, en unidades de longitud CSS absolutas. Las unidades admitidas son: pda, cm, mm, pt y pc.  
  
    -   Las unidades de longitud de CSS relativas se pasan por algo y no se admiten. Las unidades no admitidas son em, ex, px,%,rem.  
  
-   color  
  
-   padding, padding-bottom, padding-top, padding-right, padding-left  
  
-   font-weight  
  
 Estas son algunas consideraciones sobre el uso de CSS:  
  
-   Los valores de CSS incorrectos se omiten de la misma manera que se omite el HTML incorrecto.  
  
-   Cuando en una misma etiqueta hay un atributo y atributos de estilo CSS, la propiedad de CSS tiene una prioridad más alta. Por ejemplo, si el texto es **\<p style="text-align: right" align="left">** , solo se aplicará el atributo text-align y el texto estará alineado a la derecha.  
  
-   Para los atributos y los estilos CSS, si una propiedad se especifica más de una vez, solo se aplica la última instancia de la propiedad. Por ejemplo, si el texto es **\<p align="left" align="right">** , el texto estará alineado a la derecha.  
  
## <a name="see-also"></a>Consulte también  
 [Representar en HTML &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-builder/rendering-to-html-report-builder-and-ssrs.md)  
  
  
