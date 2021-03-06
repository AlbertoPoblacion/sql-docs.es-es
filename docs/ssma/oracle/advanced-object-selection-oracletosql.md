---
title: "Advanced selección de objetos (OracleToSQL) | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c978fba4-c953-4ed0-a21d-1b38e7225552
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: v-pelars
ms.workload: Inactive
ms.openlocfilehash: 967e803d7827b987cd6b457b9e6737138fec144d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="advanced-object-selection--oracletosql"></a>Selección avanzada de objetos (OracleToSQL)
El **sección avanzada de problemas de objeto** cuadro de diálogo permite filtrar los objetos de base de datos mediante el uso de cadenas y subcadenas en el nombre de objeto y, a continuación, seleccione o anule la selección de esos objetos. SSMA realiza operaciones de conversión y la migración en los objetos seleccionados.  
  
Para obtener acceso a este cuadro de diálogo, haga clic en el Explorador de metadatos y, a continuación, seleccione **selección avanzada de objeto**.  
  
Cuando abra por primera vez el cuadro de diálogo, haga clic en **mostrar elementos de subcategorías** para mostrar todos los objetos que tienen metadatos cargado en el proyecto. A continuación, puede escribir cadenas para filtrar los elementos. Por ejemplo, escriba la cadena "empresa" para mostrar todos los elementos con nombres que contengan esa cadena.  
  
Antes de utilizar este cuadro de diálogo, puede forzar SSMA para cargar todos los metadatos por convertir esquemas o guardar el proyecto.  
  
## <a name="options"></a>.  
**Compruebe todos los elementos**  
Agrega una marca de verificación junto a todos los elementos. Estos elementos se seleccionará inmediatamente en el Explorador de metadatos.  
  
**Desactive todos los elementos**  
Quita la marca de verificación junto a todos los elementos. Estos elementos se borrará inmediatamente en el Explorador de metadatos.  
  
**Modo de vista de lista**  
Muestra elementos filtrados en una lista.  
  
**Modo de vista de tabla**  
Muestra elementos filtrados en una tabla.  
  
**Muestra elementos solo cargados**  
Alterna la presentación de categorías o elementos. Cuando se selecciona este botón, SSMA muestra todos los elementos que coinciden con los criterios de filtro y las que se haya cargado anteriormente. Cuando no se selecciona este botón, SSMA muestra las carpetas de categoría.  
  
**Filter**  
Escriba la cadena que desea usar para filtrar elementos. Por ejemplo, para buscar disponibles todos los elementos que contengan la cadena "Id." en el nombre del elemento, escriba la cadena "ID" en la **filtro** cuadro.  
  
Si los elementos que coincidan con los criterios de filtro, se mostrarán las categorías o los elementos a medida que escribe la cadena. Para ver los elementos coincidentes, se recomienda que haga clic en el **muestra solo los elementos cargados** botón.  
  
**Borrar filtro**  
Borra la **filtro** cuadro.  
  
