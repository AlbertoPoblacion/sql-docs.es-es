---
title: 'Analysis Services lección 12 del tutorial: Analizar en Excel | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: c807825bfd4ef90491fb38e09e81eb79134fdbc9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62467816"
---
# <a name="analyze-in-excel"></a>Analizar en Excel

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

En esta lección, usará el analizar en función de Excel para abrir Microsoft Excel, crear automáticamente una conexión al área de trabajo del modelo y agregar automáticamente una tabla dinámica a la hoja de cálculo. La característica Analizar en Excel se ha diseñado para proporcionar una manera rápida y sencilla de probar la eficacia del diseño de su modelo antes de implementarlo. No realice ningún análisis de datos en esta lección. El propósito de esta lección es familiarizar al autor de modelos con las herramientas que puede usar para probar el diseño de sus modelos.   
  
Para completar esta lección, Excel debe instalarse en el mismo equipo que Visual Studio.
  
Tiempo estimado para completar esta lección: **5 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  

En este artículo forma parte de un tutorial de modelado tabular, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [Lección 11: Crear roles](../tutorial-tabular-1400/as-lesson-11-create-roles.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Examinar utilizando las perspectivas Predeterminada y Venta por Internet  

En estas primeras tareas, examinar el modelo utilizando tanto la perspectiva predeterminada, que incluye todos los objetos del modelo, y también mediante el uso de la perspectiva venta por Internet que creó anteriormente. La perspectiva Venta por Internet excluye el objeto de tabla Cliente.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Para examinar con la perspectiva predeterminada  
  
1.  Haga clic en el **modelo** menú > **analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel** , haga clic en **Aceptar**.  
  
    Excel se abre con un nuevo libro. Se crea una conexión de origen de datos con la cuenta de usuario actual y se utiliza la perspectiva predeterminada para definir los campos visibles. Una tabla dinámica se agrega automáticamente a la hoja de cálculo.  
  
3.  En Excel, en el **lista de campos de tabla dinámica**, tenga en cuenta la **DimDate** y **FactInternetSales** aparecen los grupos de medida. El **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, y **FactInternetSales** también aparecen las tablas con sus respectivas columnas.  
  
4.  Cierre Excel sin guardar el libro.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Para examinar con la perspectiva Venta por Internet  
  
1.  Haga clic en el **modelo** menú y, a continuación, haga clic en **analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel** , mantenga seleccionado **Usuario de Windows actual** y, después, en el cuadro de lista desplegable **Perspectiva** , seleccione **Venta por Internet**y haga clic en **Aceptar**. 
    
    ![as-lesson12-perspective](../tutorial-tabular-1400/media/as-lesson12-perspective.png)
    
3.  En Excel, en **PivotTable Fields**, tenga en cuenta la tabla DimCustomer se excluye de la lista de campos.  
    
    ![as-lesson12-fields](../tutorial-tabular-1400/media/as-lesson12-fields.png)
    
4.  Cierre Excel sin guardar el libro.  
  
## <a name="browse-by-using-roles"></a>Examinar mediante roles  

Las funciones son una parte importante de cualquier modelo tabular. Si no hay al menos un rol al que se agregan usuarios como miembros, los usuarios no pueden acceder y analizar los datos del modelo. La característica Analizar de Excel proporciona una manera de probar los roles que ha definido.  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Para examinar mediante el rol de usuario director de ventas  
  
1.  En SSDT, haga clic en el **modelo** menú y, a continuación, haga clic en **analizar en Excel**.  
  
2.  En **especifique el nombre de usuario o rol que se usará para conectarse al modelo**, seleccione **rol**y, a continuación, en el cuadro de lista desplegable, seleccione **jefe de ventas**y, a continuación, haga clic en **Aceptar**.  
  
    Excel se abre con un nuevo libro. Automáticamente se crea una tabla dinámica. La lista de campos de tabla dinámica incluye todos los campos de datos disponibles en el nuevo modelo.  
      
3.  Cierre Excel sin guardar el libro.  
  
## <a name="whats-next"></a>¿Qué sigue?

Vaya a la lección siguiente: [Lección 13: Implementar](../tutorial-tabular-1400/as-lesson-13-deploy.md).

  
  
  
