---
title: Cambiar un elemento de una celda (Diseñador de informes y SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cc13f82453349b16e4c9fc00b8f0f083652daa75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581750"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>Cambiar un elemento de una celda (Diseñador de informes y SSRS)
En informes paginados de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , solo un elemento no contenedor, como un cuadro de texto, una línea o una imagen, se puede reemplazar por un elemento de informe nuevo. Por ejemplo, puede arrastrar una tabla hasta un cuadro de texto para reemplazar éste por la tabla.  
  
 Si la celda contiene un elemento contenedor, por ejemplo un rectángulo, una lista, una tabla o una matriz, el nuevo elemento se agrega al elemento contenedor en lugar de reemplazarlo. Para reemplazar un elemento contenedor por un nuevo elemento, elimine el contenedor. De este modo, el elemento contenedor se reemplaza por un cuadro de texto que, a su vez, se puede reemplazar por otro elemento.  
  
 De forma predeterminada, todas las celdas de una tabla, matriz o región de datos de lista contienen un cuadro de texto.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-an-item-within-a-cell"></a>Para cambiar un elemento de una celda  
  
-   En la pestaña **Insertar** , en el grupo **Regiones de datos** o **Elementos de informe** , haga clic en el elemento que desee agregar al informe y, a continuación, haga clic en este último. El elemento se agregará al informe.  
  
> [!NOTE]  
>  El cuadro de diálogo **Propiedades de la imagen** se abre al arrastrar un elemento de informe de imagen a una celda; en él puede establecer propiedades como el origen de la imagen antes de agregarla a la celda.  
  
## <a name="see-also"></a>Consulte también  
 [Imágenes, cuadros de texto, rectángulos y líneas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)   
 [Tablas, matrices y listas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
