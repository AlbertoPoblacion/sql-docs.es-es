---
title: Agregar columnas a una tabla | Documentos de Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5974a3cc-caf8-4558-8836-6e3c24b1ee23
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 5b5d09c35fcdfa2def6ec78422c1f4d40caa3ef3
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="add-columns-to-a-table"></a>Agregar columnas a una tabla
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Este artículo describe cómo agregar columnas a una tabla existente.  
  
## <a name="add-columns-from-the-datasource"></a>Agregar columnas del origen de datos  
 Cuando use el Asistente para la importación de tablas para importar datos de una tabla de origen, se creará una nueva tabla en el modelo que incluirá todas las columnas de la tabla de origen, o, si decide filtrar ciertas columnas mediante la característica Vista previa y filtro, solo incluirá las columnas y los datos filtrados que seleccione. También puede escribir una consulta SQL que especifique solo las columnas que desea importar. No obstante, puede determinar posteriormente si una tabla de origen tiene columnas adicionales que desea agregar a la tabla del modelo, o si debe agregar una columna calculada con valores procedentes de una fórmula DAX.  
  
 Por ejemplo, imagine que cuando importó inicialmente desde un origen de datos, usó la característica Vista previa y filtro del Asistente para la importación de tablas para seleccionar un número limitado de columnas de la tabla de origen, y posteriormente se da cuenta de que necesita agregar otra columna que existe en la tabla de origen, pero que aún no existe en la tabla del modelo. O, por ejemplo, si se ha agregado una nueva columna AdjustedProfit a la tabla FactSales del origen de datos y ahora desea agregar la misma columna AdjustedProfit y sus datos a la tabla Sales del modelo.  
  
 En estos casos, puede usar el cuadro de diálogo Editar propiedades de tabla para seleccionar columnas de la tabla de origen y agregarlas a la tabla del modelo. El cuadro de diálogo Editar propiedades de tabla incluye la ventana de vista previa de la tabla. La ventana de vista previa de la tabla muestra la tabla en el origen. Las columnas que ya están incluidas en la definición de tabla del modelo ya están seleccionadas. Las columnas que todavía no están incluidas en la definición de tabla del modelo no están seleccionadas. Puede agregar columnas del origen a la definición de tabla del modelo; para ello, debe seleccionar la columna y hacer clic en Aceptar. La ventana de vista previa de la tabla del cuadro de diálogo Editar propiedades de tabla proporciona la misma vista y las mismas características que la ventana de vista previa de la página Vista previa y filtrar del Asistente para la importación de tablas.  
  
> [!IMPORTANT]  
>  Al agregar una columna a una tabla que contiene dos o más particiones, antes de agregar la columna a la definición de tabla con el cuadro de diálogo Editar propiedades de tabla, primero debe usar el administrador de particiones para agregar la columna a todas las particiones definidas. Después de agregar la columna a las particiones definidas, puede agregar la misma columna a la definición de tabla mediante el cuadro de diálogo Editar propiedades de tabla.  
  
> [!NOTE]  
>  Si usó una consulta SQL para seleccionar las tablas y las columnas cuando usó inicialmente el Asistente para la importación de tablas para importar los datos, deberá usar de nuevo una consulta SQL en el cuadro de diálogo Editar propiedades de tabla para agregar columnas a la tabla del modelo.  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a>Para agregar una columna del origen de datos mediante el cuadro de diálogo Editar propiedades de tabla  
  
1.  En el diseñador de modelos, haga clic en la tabla a la que desee agregar una columna, haga clic en el menú **Tabla** y, a continuación, haga clic en  **Propiedades de tabla**.  
  
2.  En el cuadro de diálogo **Editar propiedades de tabla** , en la ventana de vista previa de la tabla, seleccione la columna de origen que desee agregar y haga clic en Aceptar. Las columnas que ya están incluidas en la definición de tabla aparecen seleccionadas.  
  
## <a name="add-a-calculated-column"></a>Agregar una columna calculada  
 En una columna calculada, la fórmula DAX se usa para definir un valor para cada fila. Por ejemplo, puede crear una columna calculada con una fórmula simple () =1 que agregue el valor 1 a cada fila. Las columnas calculadas también pueden tener fórmulas más complejas que calculen los valores basándose en otros datos del modelo. Las columnas calculadas se tratan con más detalle en otros temas. Para más información, vea [Columnas calculadas](../../analysis-services/tabular-models/ssas-calculated-columns.md).  
  
#### <a name="to-create-a-calculated-column"></a>Para crear una columna calculada  
  
1.  En el diseñador de modelos, en Vista de datos, seleccione la tabla donde quiere agregar una nueva columna calculada en blanco, desplácese hasta la columna del extremo derecho o haga clic en el menú **Columna** y, después, haga clic en **Agregar columna**.  
  
     Para crear una columna entre dos columnas existentes, haga clic con el botón derecho en una columna existente y, después, haga clic en **Insertar columna**.  
  
2.  En la barra de fórmulas, escriba una fórmula DAX para agregar los atributos de cada fila.  
  
## <a name="add-a-blank-column"></a>Agregar una columna en blanco  
 En una tabla del modelo se puede crear una columna en blanco con nombre. Las columnas en blanco pueden resultar útiles si desea pegar datos de otro origen. Tenga en cuenta que los datos pegados se almacenan de forma diferente que los datos importados. Para obtener más información, consulte [copiar y pegar datos](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md).  
  
#### <a name="to-create-a-named-blank-column"></a>Para crear una columna en blanco con nombre  
  
1.  En el diseñador de modelos, en Vista de datos, seleccione la tabla donde quiere agregar una nueva columna en blanco, desplácese hasta la columna del extremo derecho o haga clic en el menú **Columna** y, después, haga clic en **Agregar columna**.  
  
     Para crear una columna entre dos columnas existentes, haga clic con el botón derecho en una columna existente y, después, haga clic en **Insertar columna**.  
  
2.  Haga clic en la celda superior, escriba un nombre y, a continuación, presione ENTRAR.  
  
## <a name="see-also"></a>Vea también  
 [Editar cuadro de diálogo de propiedades de tabla](http://msdn.microsoft.com/library/8d913e83-7246-44cc-8fc7-31729023c0d8)   
 [Cambiar las asignaciones de filtros de tabla, columna o fila](../../analysis-services/tabular-models/change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
