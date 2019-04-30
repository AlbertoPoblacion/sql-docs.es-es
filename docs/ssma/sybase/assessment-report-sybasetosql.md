---
title: Informe de evaluación (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: aae49bb6eb8ecf067911b2cb64017af0f3143aa0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63132800"
---
# <a name="assessment-report-sybasetosql"></a>Informe de evaluación (SybaseToSQL)
La ventana Informe de evaluación muestra los resultados de la conversión de objetos de base de datos a [!INCLUDE[tsql](../../includes/tsql-md.md)] sintaxis, y también puede ayudarle a estimar la complejidad y el costo de los proyectos de migración.  
  
Para tener acceso al informe de evaluación, seleccionar objetos para convertir en el Explorador de metadatos de origen, haga clic en **bases de datos**y, a continuación, seleccione **crear informe**.  
  
## <a name="options"></a>Opciones  
**Estadísticas de conversión**  
Muestra las estadísticas de la conversión al tipo de instrucción. Este panel está visible solo cuando un objeto de grupo, como un esquema, o se selecciona un objeto sin código en el panel izquierdo.  
  
**Objetos por categoría**  
Muestra las estadísticas de la conversión al tipo de objeto. Este panel está visible solo cuando un objeto de grupo, como un esquema, o se selecciona un objeto sin código en el panel izquierdo.  
  
**Estadísticas**  
Muestra las estadísticas de conversión para el objeto seleccionado. Este panel está visible solo cuando se selecciona un objeto individual con el código en el panel izquierdo. Es posible que deba expandir **estadísticas** para ver este panel.  
  
**Navegación por código fuente**  
Muestra el código de ASE para el objeto seleccionado y resalta el código que no se ha convertido a [!INCLUDE[tsql](../../includes/tsql-md.md)]. Este panel está visible solo cuando se selecciona un objeto individual con el código en el panel izquierdo.  
  
Haga clic en los números de línea para establecer o borrar marcadores. Utilice los botones en la parte superior del panel para navegar por el código.  
  
**Navegación de destino**  
Se muestra la conversión del resultante [!INCLUDE[tsql](../../includes/tsql-md.md)] código para el objeto seleccionado y los mensajes de error para el código que no se ha convertido. Este panel está visible solo cuando se selecciona un objeto individual con el código en el panel izquierdo.  
  
Haga clic en los números de línea para establecer o borrar marcadores. Utilice los botones en la parte superior del panel para navegar por el código.  
  
**Panel de mensajes**  
Muestra los errores, advertencias y mensajes de información que se generan al crear el informe de evaluación. Los mensajes se agrupan por número. Para ver el código que produjo el error, haga clic en **Error**, **advertencia**, o **información**, expanda la categoría de mensajes y, a continuación, haga clic en un mensaje.  
  
