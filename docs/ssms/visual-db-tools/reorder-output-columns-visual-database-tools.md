---
title: Reordenar las columnas de salida
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: f168b16ef5407b8ebf47e55f7062b1b7c8c7b180
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008870"
---
# <a name="reorder-output-columns-visual-database-tools"></a>Reordenar las columnas del resultado (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
El orden en que agregue columnas de datos a una consulta Select determinará el orden en el que se mostrarán en los resultados. La primera columna que agregue a la consulta será la que se muestre más a la izquierda en los resultados; a continuación, se mostrará la segunda columna agregada, y así sucesivamente.  
  
Si crea consultas Update o Insert, el orden en que agregue columnas afectará al orden en que se procesarán los datos.  
  
Para controlar si se muestra una columna de datos en el conjunto de resultados o el orden en que se va a mostrar, puede volver a ordenar las columnas.  
  
### <a name="to-reorder-columns-for-output"></a>Para volver a ordenar las columnas para los resultados  
  
1.  En el [panel Criterios](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md), seleccione la fila que contiene la columna; para ello, haga clic en el botón selector de fila situado a la izquierda de la fila.  
  
2.  Señale el botón selector de fila y arrastre la fila a una nueva ubicación.  
  
    O bien  
  
    Edite el orden de los nombres de columna en el [panel SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
> [!TIP]  
> Puede agregar una fila de datos en una determinada ubicación del panel Criterios; para ello, debe insertar una fila en blanco en el panel y especificar después la columna de datos que desea insertar. Para detalles, consulte [Agregar columnas a las consultas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md).  
  
## <a name="see-also"></a>Consulte también  
[Ordenar y agrupar los resultados de una consulta &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Resumir los resultados de una consulta &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Realizar operaciones básicas con consultas (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
