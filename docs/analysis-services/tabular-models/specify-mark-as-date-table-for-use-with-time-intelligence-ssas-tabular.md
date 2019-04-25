---
title: Especificar marcar como tabla de fechas en los modelos tabulares de Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df4afbecebd3c076f80064dbd3d13f35ba2cbcf0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472085"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence"></a>Especificar marcar como tabla de fechas para su uso con inteligencia de tiempo
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Para poder usar las funciones de inteligencia de tiempo en fórmulas DAX, debe especificar una tabla de fechas y una columna de identificador único (datetime) del tipo de datos de fecha. Una vez especificada una columna en la tabla de fechas como identificador único, puede crear relaciones entre las columnas de la tabla de fechas y cualquier tabla de hechos.  
  
 Al utilizar las funciones de inteligencia de tiempo, se aplican las reglas siguientes:  
  
-   Al utilizar las funciones de inteligencia de tiempo DAX, no especifique nunca una columna de fecha y hora de una tabla de hechos. Cree siempre una tabla de fechas independiente en el modelo con al menos una columna datetime del tipo de datos Date y con valores únicos.  
  
-   Asegúrese de que la tabla de fechas tiene un intervalo de fechas continuo.  
  
-   La columna datetime de la tabla de fechas debe estar desglosada por día (sin fracciones de día).  
  
-   Debe especificar una tabla de fechas y una columna de identificador único mediante el cuadro de diálogo **Marcar como tabla de fechas** .  
  
-   Cree relaciones entre las tablas de hechos y las columnas de tipo de datos Date en la tabla de fechas.  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>Para especificar una tabla de fechas y un identificador único  
  
1.  En el diseñador de modelos, haga clic en la tabla de fechas.  
  
2.  Haga clic en el menú **Tabla** , haga clic en **Fecha**y después haga clic en **Marcar como tabla de fechas**  
  
3.  En el cuadro de diálogo **Marcar como tabla de fechas** , en el cuadro de lista **Fecha** , seleccione la columna que se utilizará como identificador único. Esta columna debe contener valores únicos y debe ser de tipo de datos Date. Por ejemplo:  
  
    |date|  
    |----------|  
    |1/7/2010 12:00:00 a.m.|  
    |2/7/2010 12:00:00 a.m.|  
    |3/7/2010 12:00:00 a.m.|  
    |4/7/2010 12:00:00 a.m.|  
    |5/7/2010 12:00:00 a.m.|  
  
4.  Si fuera necesario, cree las relaciones entre las tablas de hechos y la tabla de fechas.  
  
## <a name="see-also"></a>Vea también  
 [Cálculos](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [Funciones de inteligencia de tiempo (DAX)](http://msdn.microsoft.com/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  
