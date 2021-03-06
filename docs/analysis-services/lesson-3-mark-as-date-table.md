---
title: "Lección 4: Marcar como tabla de fechas | Documentos de Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: e463f148b07d8fbe7061dca0eed66bba1b0fee94
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-3-mark-as-date-table"></a>Lección 3: Marcar como tabla de fechas
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

En la lección 2: Agregar datos, importó una tabla de dimensiones denominada DimDate. Mientras que en el modelo de esta tabla se denomina DimDate, también se conoce como un *tabla de fechas*, ya que contiene datos de fecha y hora.  
  
Cada vez que se utilizan funciones de inteligencia de tiempo DAX en los cálculos, tal y como se llevará a cabo al crear medidas un poco más adelante, debe especificar propiedades de tabla de fecha, que incluyen un *tabla de fechas* y un identificador único *fecha columna* de esa tabla.
  
En esta lección, podrá marcar la tabla DimDate como el *tabla de fechas* y la columna de fecha (en la tabla Date) como el *columna de fecha* (identificador único).  

Antes de que se marque la tabla de fechas y la columna de fecha, que necesitamos un poco mantenimiento para hacer que nuestro modelo más fácil de entender. Notará en la tabla DimDate una columna denominada **FullDateAlternateKey**. Contiene una fila para cada día de cada año de calendario incluido en la tabla. Usaremos esta columna mucho en fórmulas de medida y en los informes. Sin embargo, FullDateAlternateKey no es realmente un buen identificador para esta columna. Vamos a cambiar el nombre a **fecha**, lo que sea más fácil identificar e incluir en las fórmulas. Siempre que sea posible, es una buena idea cambiar el nombre de objetos, como tablas y columnas para facilitar su identificación en las aplicaciones como Power BI y Excel de informes. 
  
Tiempo estimado para completar esta lección: **3 minutos**  
  
## <a name="prerequisites"></a>Prerequisites  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [lección 2: agregar datos](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Para cambiar el nombre de la columna FullDateAlternateKey

1.  En el Diseñador de modelos, haga clic en el **DimDate** tabla.

2.  Haga doble clic en el encabezado de la **FullDateAlternateKey** columna y, a continuación, cambie su nombre a **fecha**.

  
### <a name="to-set-mark-as-date-table"></a>Para establecer la marca como tabla de fecha  
  
1.  Seleccione la columna **Date** y, en la ventana **Propiedades** , en **Tipo de datos**, asegúrese de que  **Date** está seleccionada.  
  
2.  Haga clic en el menú **Tabla** , haga clic en **Date**y, después, haga clic en **Marcar como tabla de fechas**.  
  
3.  En el cuadro de diálogo **Marcar como tabla de fechas** en el cuadro de lista **Date** , seleccione la columna **Date** como identificador único. Normalmente se seleccionará de forma predeterminada. Haga clic en **Aceptar**. 

    ![como-tabular-lesson3-date-table](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>¿Qué sigue?
Vaya a la siguiente lección: [lección 4: crear relaciones](../analysis-services/lesson-4-create-relationships.md).
  
