---
title: "Columnas de índice de texto completo (cuadro de diálogo, Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ec4029fc816c963a2a0ac5ddc61ffc354e50589
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a>Columnas de índice de texto completo (cuadro de diálogo, Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] En este cuadro de diálogo se enumeran las columnas que participan en el índice de texto completo de la tabla abierta en el Diseñador de tablas. Para tener acceso a este cuadro de diálogo, haga clic en la tabla con el botón derecho en el Diseñador de tablas, elija **Índice de texto completo**y, en el cuadro de diálogo **Índice de texto completo** , haga clic en el índice con columnas que desee ver o editar, haga clic en el campo **Columnas** de la cuadrícula situada a la derecha y haga clic en los puntos suspensivos (**...**).  
  
## <a name="options"></a>.  
**Columna**  
Muestra los nombres de las columnas que participan en el índice de texto completo. Para agregar una columna, haga clic en la primera celda vacía y elija una columna en la lista desplegable. Solo serán accesibles las columnas con tipos de datos de imagen o basados en texto.  
  
**Tipo de datos**  
Muestra el tipo de datos de cada columna. Se trata de una propiedad de solo lectura. Para cambiar un tipo de datos, abra la tabla en el Diseñador de tablas, haga clic en la columna y edite el tipo de datos en la pestaña **Propiedades de columna** .  
  
**Escrito por columna**  
Solo se aplica a columnas con el tipo de datos **image**. Proporciona una lista desplegable en la que se puede elegir qué otras columnas representan el tipo de datos de esta columna. Si esta columna no es del tipo de datos **image** , el valor será Ninguno.  
  
Las columnas con el tipo de datos **image** pueden contener archivos de Microsoft Office (.doc, .xls y .ppt), de texto (.txt) y HTML (.htm), y al establecer el tipo de datos de dicha columna en image, se permite la búsqueda de texto completo en el contenido de los archivos.  
  
**Lenguaje**  
Muestra los idiomas disponibles. En la lista desplegable, elija el idioma en el que están los datos de la columna. Por ejemplo, si utiliza un sistema operativo en inglés, pero desea indizar una columna que contiene texto en alemán, elija el alemán en la lista desplegable para mejorar el rendimiento del índice.  
  
**Semántica estadística**  
Seleccione si desea habilitar la indización semántica para la columna seleccionada. Para más información, consulte [Marcador de posición de Búsqueda semántica](http://msdn.microsoft.com/en-us/cd8faa9d-07db-420d-93f4-a2ea7c974b97).  
  
Si selecciona **Idioma** antes de seleccionar **Semántica estadística**y el idioma seleccionado no tiene un modelo semántico asociado, la casilla **Semántica estadística** está deshabilitada. Si selecciona **Semántica estadística** antes de seleccionar **Idioma**, los idiomas disponibles en el cuadro combinado desplegable estarán limitados a aquellos para los que exista un modelo de idioma semántico.  
  
## <a name="see-also"></a>Ver también  
[Cuadro de diálogo Índice de texto completo &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/full-text-index-dialog-box-visual-database-tools.md)  
  
