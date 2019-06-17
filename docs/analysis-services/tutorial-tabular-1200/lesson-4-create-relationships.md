---
title: 'Lección 4: Crear relaciones | Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8cad8c81021587a9dc3742983d7c7c2cd80fc174
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404857"
---
# <a name="lesson-4-create-relationships"></a>Lección 4: Crear relaciones
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

En esta lección, comprobará las relaciones que se han creado de forma automática al importar datos y agregará nuevas relaciones entre tablas diferentes. Una relación es una conexión entre dos tablas de datos que establece cómo se deben poner en correlación los datos de esas tablas. Por ejemplo, la tabla DimProduct y la tabla DimProductSubcategory tienen una relación basada en el hecho que cada producto pertenece a una subcategoría. Para obtener más información, consulte [relaciones](../tabular-models/relationships-ssas-tabular.md).
  
Tiempo estimado para completar esta lección: **10 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [Lección 3: Marcar como tabla de fechas](lesson-3-mark-as-date-table.md). 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Examinar las relaciones existentes y agregar nuevas relaciones  
Cuando importó los datos mediante el Asistente para importación de tablas, se obtendrán siete tablas de la base de datos AdventureWorksDW. Por lo general, al importar datos desde un origen relacional, las relaciones existentes se importan automáticamente junto con los datos. Sin embargo, para poder crear el modelo debe comprobar que esas relaciones entre las tablas se crearon correctamente. En este tutorial, agregará también tres relaciones nuevas.  
  
#### <a name="to-review-existing-relationships"></a>Para revisar las relaciones existentes  
  
1.  Haga clic en el **modelo** menú > **vista de modelo** > **vista de diagrama**.  

    El diseñador de modelos se muestra ahora en la vista de diagrama, un formato gráfico que muestra todas las tablas que importó con líneas entre ellas. Las líneas entre las tablas indican las relaciones que se crearon automáticamente cuando importó los datos.
    
    ![as-tabular-lesson4-diagram](media/as-tabular-lesson4-diagram.png)
  
    Use los controles de minimapa de la esquina inferior derecha del diseñador de modelos para ajustar la vista e incluir tantas tablas como sea posible. También puede haga clic y arrastre las tablas a ubicaciones diferentes, aunando las tablas o colocándolas en un orden concreto. El movimiento de las tablas no afecta a las relaciones existentes entre ellas. Para ver todas las columnas de una tabla determinada, haga clic y arrastre un borde de tabla para expandir o reducir el tamaño.  
  
2.  Haga clic en la línea sólida entre la **DimCustomer** tabla y el **DimGeography** tabla. La línea sólida entre estas dos tablas muestra que esta relación está activa, es decir, se utiliza de forma predeterminada al calcular fórmulas DAX.  
  
    Tenga en cuenta la **GeographyKey** columna en el **DimCustomer** tabla y el **GeographyKey** columna en el **DimGeography** tabla ahora ambos aparecen dentro de un cuadro. Esta presentación trata las columnas utilizadas en la relación. Propiedades de la relación aparecen ahora también en el **propiedades** ventana.  
  
    > [!TIP]  
    > Además de usar el Diseñador de modelos de vista de diagrama, también puede usar el cuadro de diálogo Administrar relaciones para mostrar las relaciones entre todas las tablas en un formato de tabla. Haga clic en **relaciones** en el Explorador de modelos tabulares y, a continuación, haga clic en **administrar relaciones**. El cuadro de diálogo Administrar relaciones muestra las relaciones que se crearon automáticamente cuando importó los datos.  
  
3.  Use el Diseñador de modelos en la vista de diagrama o en el cuadro de diálogo Administrar relaciones, para comprobar que se crearon las siguientes relaciones cuando se importó cada una de las tablas de la base de datos AdventureWorksDW:  
  
    |Activo|Table|Tabla de búsqueda relacionada|  
    |----------|---------|------------------------|  
    |Sí|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |Sí|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |Sí|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |Sí|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |Sí|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    Si falta cualquiera de las relaciones en la tabla anterior, compruebe que el modelo incluye las siguientes tablas: DimCustomer, DimDate, DimGeography, DimProduct, DimProductCategory, DimProductSubcategory y FactInternetSales. Si las tablas de la misma conexión del origen de datos se importan en momentos distintos, no se creará ninguna relación entre estas tablas y las relaciones deberán crearse manualmente.  

### <a name="take-a-closer-look"></a>Échele un vistazo
En la vista de diagrama, observará una flecha, un asterisco y un número en las líneas que muestran la relación entre tablas.

![as-tabular-lesson4-line](media/as-tabular-lesson4-line.png)

La flecha muestra la dirección del filtro, que el asterisco muestra que esta tabla es el lado "varios" de la cardinalidad de la relación y el 1 indica que esta tabla es el uno lado de la relación. Si necesita modificar una relación; Por ejemplo, cambiar la dirección de filtro de la relación y cardinalidad, haga doble clic en la línea de relación en la vista de diagrama para abrir el cuadro de diálogo Editar relación.

![as-tabular-lesson4-edit](media/as-tabular-lesson4-edit.png)

Probablemente, nunca tendrá que editar una relación. Estas características están diseñadas para el modelado de datos avanzados y están fuera del ámbito de este tutorial. Para obtener más información, consulte [bidireccional entre los filtros para modelos tabulares de SQL Server 2016 Analysis Services](../tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md).

En algunos casos, tal vez necesite crear relaciones adicionales entre las tablas de su modelo para permitir una determinada lógica empresarial. Para este tutorial, deberá crear tres relaciones adicionales entre la tabla FactInternetSales y DimDate.  
  
#### <a name="to-add-new-relationships-between-tables"></a>Para agregar nuevas relaciones entre las tablas  
  
1.  En el Diseñador de modelos en el **FactInternetSales** de tabla, haga clic y mantenga presionado el **OrderDate** columna, a continuación, arrastre el cursor hasta la **fecha** columna en el  **DimDate** de tabla y suéltelo.  

    Aparece una línea sólida que indica que ha creado una relación activa entre la **OrderDate** columna en el **Internet Sales** tabla y el **fecha** columna en el **Fecha** tabla. 
  
      ![as-tabular-lesson4-new](media/as-tabular-lesson4-new.png) 
  
    > [!NOTE]  
    > Al crear relaciones, se selecciona automáticamente la dirección del filtro y cardinalidad entre la tabla principal y la tabla de búsqueda relacionada.  
  
2.  En el **FactInternetSales** de tabla, haga clic y mantenga presionado el **DueDate** columna, a continuación, arrastre el cursor hasta la **fecha** columna en el **DimDate** tabla y, a continuación, suelte.  
  
    Aparece una línea punteada que indica que ha creado una relación inactiva entre la **DueDate** columna en el **FactInternetSales** tabla y el **fecha** columna en el  **DimDate** tabla. Puede haber varias relaciones entre las tablas, pero solo una puede estar activa cada vez.  
  
3.  Por último, cree una relación más; en el **FactInternetSales** de tabla, haga clic y mantenga presionado el **ShipDate** columna, a continuación, arrastre el cursor hasta la **fecha** columna en el **DimDate**de tabla y suéltelo.  
    
     ![as-tabular-lesson4-newinactive](media/as-tabular-lesson4-newinactive.png)
  
## <a name="whats-next"></a>¿Qué sigue?
Vaya a la lección siguiente: [Lección 5: Crear columnas calculadas](lesson-5-create-calculated-columns.md).
  
  
  
