---
title: Vincular varias regiones de datos al mismo conjunto de datos (Generador de informes y SSRS) | Microsoft Docs
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 90c94a91-8fb2-42cb-b998-563691f30d2d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7c67ddcb48847d3618c9544c50868b555e263fd7
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65580146"
---
# <a name="linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs"></a>Vincular varias regiones de datos al mismo conjunto de datos (Generador de informes y SSRS)

Puede agregar varias regiones de datos a un informe paginado de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para proporcionar vistas diferentes de los datos a partir del mismo conjunto de datos de informe. Por ejemplo, es posible que le interese mostrar los datos en una tabla y, además, representarlos visualmente en un gráfico. Para ello, debe usar expresiones y ámbitos idénticos para las expresiones de filtro, las expresiones de ordenación y las expresiones de grupo correspondientes.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Usar un gráfico y una tabla o matriz para mostrar los mismos datos ayuda a comprender las similitudes entre una tabla y un gráfico de formas, y entre una matriz y un gráfico de áreas, de barras y de columnas. Una tabla con un solo grupo de filas se puede mostrar fácilmente como un gráfico circular. Si agrega varios grupos de filas, puede elegir otros tipos de gráficos que representen mejor los grupos anidados. Cuando se agregan grupos de filas anidados a un gráfico circular, aumenta el número de sectores del gráfico. Debe decidir si la suma del número de instancias de grupo para el grupo primario y el grupo secundario es un número demasiado grande para mostrarse en un único gráfico circular. Si en un gráfico circular existen varios valores de grupo que se muestran como pequeños sectores, puede establecer una propiedad para que todos los valores que se encuentren por debajo de un umbral determinado se muestren como un único sector en el gráfico. Para más información, vea [Recopilar segmentos pequeños en un gráfico circular](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md).  
  
 Una tabla con varios grupos de filas se puede mostrar como un gráfico de columnas con varios grupos de categorías. Para más información, vea [Mostrar los mismos datos en una matriz y en un gráfico](../../reporting-services/report-design/display-the-same-data-on-a-matrix-and-a-chart-report-builder.md). Para obtener un ejemplo de una tabla y un gráfico que presentan vistas diferentes del mismo conjunto de datos de informe, vea el informe Product Line Sales en los ejemplos de informes de AdventureWorks. Dado que la tabla y el gráfico están vinculados al mismo conjunto de datos de este informe, al hacer clic en el botón de ordenación interactiva Employee Name de la tabla Top Employees, el gráfico Top Employees también muestra automáticamente el nuevo criterio de ordenación. Para más información acerca de cómo descargar este y otros informes de ejemplo, consulte el tema sobre [informes de ejemplo del Generador de informes y el Diseñador de informes](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
 Una matriz con varios grupos de columnas y de filas se mostrará mejor mediante un gráfico de áreas, de barras o de columnas con grupos de categorías y de series. Use las mismas expresiones de grupo para los grupos de columnas de la matriz y los grupos de categorías del gráfico, y las mismas expresiones de grupo para los grupos de filas de la matriz y los grupos de series del gráfico. Debe tener presente que el número de instancias de grupo afecta a la legibilidad del gráfico. Puede definir grupos basados en valores de intervalo para reducir el número de instancias de grupo de un informe. Para más información, vea [Ejemplos de expresión de grupo](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md).  
  
## <a name="next-steps"></a>Pasos siguientes

[Gráficos](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Tablas, matrices y listas](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
[Regiones de datos anidadas](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)  

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
