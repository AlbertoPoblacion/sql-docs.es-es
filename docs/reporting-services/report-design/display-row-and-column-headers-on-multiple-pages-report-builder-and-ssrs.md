---
title: Visualización de encabezados de columna y de fila en varias páginas (Generador de informes) | Microsoft Docs
description: Puede controlar si se deben repetir los encabezados de fila y de columna en cada página de un informe paginado de Reporting Services de una región de datos Tablix (una tabla, matriz o lista) que abarca varias páginas.
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.date: 12/09/2019
ms.openlocfilehash: ca1b00d98c71808cd42acb220e7fbf5d1c382555
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254590"
---
# <a name="display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs"></a>Mostrar encabezados de fila y de columna en varias páginas (Generador de informes y SSRS)

  Puede controlar si se deben repetir los encabezados de fila y de columna en cada página de un informe paginado de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] de una región de datos Tablix (una tabla, matriz o lista) que abarca varias páginas.
  
 El modo en que controle las filas y las columnas dependerá de si la región de datos Tablix tiene encabezados de grupo. Al hacer clic en una región de datos Tablix que tiene encabezados de grupo, una línea de puntos muestra las áreas Tablix, como se muestra en la figura siguiente:  
  
 ![Descripción de las áreas de la región de datos Tablix](../../reporting-services/report-design/media/rs-tablixareas.gif "Descripción de las áreas de la región de datos Tablix")  
  
 Los encabezados de grupo de filas y de columnas se crean automáticamente al agregar los grupos usando el asistente Nueva tabla o matriz o el asistente Nuevo gráfico, agregando los campos al Panel de agrupación o usando los menús contextuales. Si la región de datos Tablix tiene solamente un área de cuerpo de Tablix y ningún encabezado de grupo, las filas y columnas son miembros de Tablix.  
  
 Para los miembros estáticos, puede mostrar la parte superior de las filas adyacentes o las columnas adyacentes las laterales en varias páginas.  
  
## <a name="to-display-row-headers-on-multiple-pages"></a>Para mostrar encabezados de fila en varias páginas  
  
1. Haga clic con el botón derecho en la fila o columna o en el controlador de tabla de una región de datos Tablix y, después, haga clic en **Propiedades de Tablix**.  
  
2. En **Encabezados de fila**, seleccione **Repetir filas de encabezado en todas las páginas**.  
  
3. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="to-display-column-headers-on-multiple-pages"></a>Para mostrar encabezados de columna en varias páginas  
  
1. Haga clic con el botón derecho en la fila o columna o en el controlador de tabla de una región de datos Tablix y, después, haga clic en **Propiedades de Tablix**.  
  
2. En **Encabezados de columna**, seleccione **Repetir columnas de encabezado en todas las páginas**.  
  
3. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="to-display-a-static-row-or-column-on-multiple-pages"></a>Para mostrar una columna o fila estática en varias páginas  
  
1. En la superficie de diseño, haga clic en el controlador de fila o de columna de la región de datos Tablix para seleccionarlo. El Panel de agrupación muestra los grupos de filas y de columnas.  
  
2. En el lado derecho del panel Agrupación, haga clic en la flecha abajo y, a continuación, haga clic en **Modo avanzado**. El panel Grupos de filas muestra los miembros jerárquicos estáticos y dinámicos de la jerarquía de grupos de fila, mientras que el panel Grupos de columnas muestra una vista similar de la jerarquía de grupos de columna.  
  
3. Haga clic en el miembro estático que corresponde al miembro estático (fila o columna) que desea que se mantenga visible durante el desplazamiento. El panel de propiedades muestra las propiedades de **Miembro de Tablix** .  
  
     Si no ve el panel Propiedades, haga clic en la pestaña **Ver** en la parte superior de la ventana del Generador de informes y, después, haga clic en **Propiedades**.  
  
4. En el panel Propiedades, configure **RepeatOnNewPage** en True.  
  
5. Establezca **KeepWithGroup** en Después.  
  
6. Repita este paso para todos los miembros adyacentes que desee repetir.  
  
7. Obtenga una vista previa del informe.  
  
 Cuando ve cada página del informe que abarca la región de datos Tablix, los miembros estáticos de Tablix se repiten en cada página.  
  
## <a name="see-also"></a>Consulte también  
 [Buscar, ver y administrar informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportación de informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [Controlar saltos de página, encabezados, columnas y filas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md)   
 [Mostrar encabezados y pies de página con un grupo &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [Mantener visibles los encabezados al desplazarse a través de un informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
  
