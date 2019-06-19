---
title: 'Lección 9: Crear jerarquías | Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 388df29badcde95c04c3db3604af63ed995666ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403747"
---
# <a name="lesson-9-create-hierarchies"></a>Lección 9: Crear jerarquías
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

En esta lección, creará jerarquías. Las jerarquías son grupos de columnas dispuestas en niveles; por ejemplo, una jerarquía Geografía puede tener subniveles para País, Provincia y Ciudad. Las jerarquías pueden aparecer por separado de otras columnas en una lista de campos de la aplicación cliente de informes, lo que facilita la navegación de los usuarios del cliente y su inclusión en un informe. Para obtener más información, consulte [jerarquías](../tabular-models/hierarchies-ssas-tabular.md).  
  
Para crear jerarquías, usará el Diseñador de modelos en *vista de diagrama*. Crear y administrar jerarquías no se admiten en la vista de datos.  
  
Tiempo estimado para completar esta lección: **20 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [Lección 8: Crear perspectivas](lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Crear jerarquías  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Para crear una jerarquía de categorías en la tabla DimProduct  
  
1.  En el Diseñador de modelos (vista de diagrama), haga clic en el **DimProduct** tabla > **crear jerarquía**. Aparece una nueva jerarquía en la parte inferior de la ventana de tabla. Cambiar el nombre de la jerarquía **categoría**.  
  
2.  Haga clic y arrastre el **ProductCategoryName** columna a la nueva **categoría** jerarquía.  
  
3.  En el **categoría** jerarquía, haga clic en el **ProductCategoryName** > **cambiar el nombre de**y, a continuación, escriba **categoría**.  
  
    > [!NOTE]  
    > Al cambiar el nombre de una columna de la jerarquía no se cambia el nombre de esa columna en la tabla. Una columna de una jerarquía es simplemente una representación de la columna de la tabla.  
  
4.  Haga clic y arrastre el **ProductSubcategoryName** columna a la **categoría** jerarquía. Cámbiele el nombre **subcategoría**. 
  
5.  Haga clic en el **ModelName** columna > **agregar a jerarquía**y, a continuación, seleccione **categoría**. Lo mismo para **EnglishProductName**. Cambiar el nombre de estas columnas en la jerarquía **modelo** y **producto**.  

    ![as-tabular-lesson9-category](media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Para crear jerarquías en la tabla DimDate  
  
1.  En el **DimDate** de tabla, cree una nueva jerarquía llamada **calendario**.  
  
3.  Agregue las columnas siguientes en el orden:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  En el **DimDate** de tabla, cree un **Fiscal** jerarquía. Incluir las columnas siguientes:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Por último, en el **DimDate** de tabla, cree un **ProductionCalendar** jerarquía. Incluir las columnas siguientes:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>¿Qué sigue?
Vaya a la lección siguiente: [Lección 10: Crear particiones](lesson-10-create-partitions.md). 
  
  
