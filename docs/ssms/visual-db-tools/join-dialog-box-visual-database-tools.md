---
title: Cuadro de diálogo Combinar
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: cff110d8eccc22ac9c6705420c845713bfffdb74
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "75224673"
---
# <a name="join-dialog-box-visual-database-tools"></a>Combinar (cuadro de diálogo, Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Utilice este cuadro de diálogo para especificar las opciones de combinación de tablas. Para tener acceso a este cuadro de diálogo, en el panel **Diseño** seleccione una línea de combinación. Después, en la ventana **Propiedades**, haga clic en **Condición y tipo de combinación** y haga clic en los puntos suspensivos **(...)** situados a la derecha de la propiedad.  
  
De forma predeterminada, las tablas relacionadas se combinan mediante una combinación interna que crea un conjunto de resultados a partir de filas que contienen información coincidente en las columnas de combinación. Puede establecer opciones en la el cuadro de diálogo **Combinación** para especificar una combinación basada en un operador diferente o para especificar una combinación externa.  
  
Para más información sobre cómo combinar las tablas, consulte [Realizar consultas con combinaciones &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md).  
  
## <a name="options"></a>Opciones  
  
|**Término**|**Definición**|  
|------------|------------------|  
|**Table**|Los nombres de las tablas u objetos con valores de tabla que participan en la combinación. Aquí no puede cambiar los nombres de las tablas; esta información solo se muestra con fines informativos.|  
|**Columna**|Los nombres de las columnas utilizadas para combinar las tablas. El operador seleccionado en la lista de operadores especifica la relación entre los datos de las columnas. Aquí no puede cambiar los nombres de las columnas; esta información solo se muestra con fines informativos.|  
|**Operador**|Especifica el operador que se va a utilizar para relacionar las columnas de combinación. Si desea especificar un operador distinto de igual (=), selecciónelo de la lista. Cuando cierre la página de propiedades, el operador seleccionado aparecerá en el gráfico con forma de diamante de la línea de combinación, como se muestra en la ilustración siguiente:<br /><br />![Icono de Visual Database Tools](../../ssms/visual-db-tools/media/dv3wbii.gif "Icono de Visual Database Tools")|  
|**Todas las filas de <table1>**|Especifica que se mostrarán todas las filas de la tabla de la izquierda en los resultados, aunque no tengan correspondencias en la tabla de la derecha. Las columnas que no tienen datos coincidentes en la tabla de la derecha se mostrarán como columnas de valores NULL. Elegir esta opción equivale a especificar LEFT OUTER JOIN en la instrucción SQL.|  
|**Todas las filas de <table2>**|Especifica que se mostrarán todas las filas de la tabla de la derecha en los resultados, aunque no tengan correspondencias en la tabla de la izquierda. Las columnas que no tienen datos coincidentes en la tabla de la izquierda se mostrarán como columnas de valores NULL. Elegir esta opción equivale a especificar RIGHT OUTER JOIN en la instrucción SQL.|  
  
La selección de Todas las **filas de <table1>** y **Todas las filas de <table2>** equivale a especificar FULL OUTER JOIN en la instrucción SQL.  
  
Cuando selecciona una opción para crear una combinación externa, el gráfico en forma de diamante de la línea de combinación cambiará para indicar si la combinación es una combinación externa izquierda, externa derecha o externa completa.  
  
> [!NOTE]  
> Las palabras "izquierda" y "derecha" no se corresponden necesariamente con la posición de las tablas en el panel Diagrama. "Izquierda" hace referencia a la tabla cuyo nombre aparece a la izquierda de la palabra clave JOIN en la instrucción SQL y "derecha" hace referencia a la tabla cuyo nombre aparece a la derecha de la palabra clave JOIN. Si mueve las tablas en el panel **Diagrama** , las tablas izquierda o derecha seguirán siendo las mismas.  
  
## <a name="see-also"></a>Consulte también  
[Realizar consultas con combinaciones &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
[Temas de procedimientos de diseño de consultas y vistas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
