---
title: Definir el cuadro de diálogo de relación (Analysis Services - datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.f1
helpviewer_keywords:
- Define Relationship dialog box
ms.assetid: 0fcee7f1-f138-4c2e-ae8c-245395ee0fe8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2bc1ab86373fc7c3b4b32cdfdbc87f5d5dd4acf8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732091"
---
# <a name="define-relationship-dialog-box-analysis-services---multidimensional-data"></a>Cuadro de diálogo Definir relación (Analysis Services - Datos multidimensionales)
  Use el cuadro de diálogo **Definir relación** para definir una relación entre una dimensión de cubo y un grupo de medida en el Diseñador de cubos. Puede mostrar el cuadro de diálogo **Definir relación** haciendo clic en los **...** de una celda del panel **Cuadrícula** que se encuentra en la pestaña **Uso de dimensiones** en el Diseñador de cubos.  
  
## <a name="options"></a>Opciones  
 **Seleccionar tipo de relación**  
 Seleccione el tipo de relación de dimensión que desea crear entre la dimensión de cubo y el grupo de medida. Si selecciona un tipo de relación de dimensión, se cambia el contenido del panel **Detalle** .  
  
 Si se elige **Sin relación** , no se crea ninguna relación de dimensión.  
  
 **Detail**  
 Muestra las opciones disponibles para el tipo de relación de dimensión seleccionado en **Seleccionar tipo de relación**.  
  
## <a name="detail-pane-options"></a>Opciones del panel Detalle  
 Las siguientes opciones se muestran en el panel **Detalle** , en función del tipo de relación seleccionado en **Seleccionar tipo de relación**:  
  
|Tipo de relación|Descripción|Opción|  
|-----------------------|-----------------|------------|  
|**Ninguna relación**|No hay ninguna relación definida y no se muestran opciones en el panel **Detalle** .||  
|**Regular**|Especifica una relación de dimensión normal. En el panel **Detalle** se muestran las siguientes opciones:|**Atributo de granularidad**: <br />                      Seleccione el atributo que define la granularidad del grupo de medida con respecto a la dimensión. Por lo general, este atributo es el atributo clave de la dimensión.|  
|||**Tabla de dimensión** : Muestra la tabla principal correspondiente a la dimensión.|  
|||**Tabla de grupos de medida** : Muestra la tabla de hechos correspondiente al grupo de medida.|  
|||**Relación**: Muestra una cuadrícula de columnas de dimensión y columnas de grupo de medida en que se basa la relación. La cuadrícula contiene las columnas siguientes:<br /><br /> **Columnas de dimensión**: Muestra las columnas asociadas al atributo de granularidad seleccionado. Nota: Si aún no se ha generado la dimensión, esta opción está establecida en **generar**.<br />**Columnas de grupo de medida** :<br />                              Seleccione las columnas del grupo de medida que están relacionadas con las columnas de dimensión.|  
|||**Avanzadas**:<br />                      Haga clic en esta opción para mostrar el cuadro de diálogo **Enlaces de grupo de medida** y editar las propiedades avanzadas, como el procesamiento de valores NULL, en las relaciones que se crearon entre las columnas de atributos y de grupos de medida. Para más información sobre el cuadro de diálogo **Enlaces de grupo de medida**, vea [Cuadro de diálogo Enlaces de grupo de medida &#40;Analysis Services - Datos multidimensionales&#41;](measure-group-bindings-dialog-box-analysis-services-multidimensional-data.md).|  
|**Fact**|Especifica una relación de dimensión de hechos. En el panel **Detalle** se muestran las siguientes opciones:|**Atributo de granularidad**: Seleccione el atributo que define la granularidad del grupo de medida con respecto a la dimensión. Por lo general, este atributo es el atributo clave de la dimensión.|  
|||**Tabla de dimensiones**: Muestra la tabla de dimensiones principal.|  
|||**Tabla de grupos de medida**: <br />                      Muestra la tabla sobre la que se basa el grupo de medida.|  
|**Al que hace referencia**|Especifica una relación de dimensión a la que se hace referencia. En el panel **Detalle** se muestran las siguientes opciones:|**Dimensión de referencia**: <br />                      Muestra la dimensión seleccionada.|  
|||**Dimensión intermedia**: <br />                      Seleccione la dimensión intermedia.|  
|||**Atributo de dimensión de referencia**: <br />                      Seleccione el atributo de la dimensión de referencia que está relacionado con el atributo de la dimensión intermedia especificado en **Atributo de dimensión intermedia**.|  
|||**Atributo de dimensión intermedia**: <br />                      Seleccione el atributo de la dimensión intermedia que está relacionado con el atributo de la dimensión de referencia especificado en **Dimensión de referencia**.|  
|||**Materializar**: <br />                      Seleccione el almacenamiento del miembro del atributo en la dimensión intermedia que vincula el atributo de la dimensión de referencia a la tabla de hechos de la estructura MOLAP. Materializar la relación es el comportamiento predeterminado para maximizar el rendimiento de la consulta, con el inconveniente de que aumenta el tiempo de procesamiento y el espacio de almacenamiento.|  
|**Many-to-Many**|Especifica una relación de dimensión de varios a varios. En el panel **Detalle** se muestran las siguientes opciones:|**Dimensión** : Muestra la dimensión seleccionada.|  
|||**Grupo de medida intermedio** : <br />                      Selecciona el grupo de medida intermedio asociado.<br /><br /> Nota: El grupo de medida intermedio debe tener al menos una dimensión en común con el grupo de medida seleccionado. Además, la granularidad de la relación entre el grupo de medida intermedio y la dimensión común debe ser mayor que o igual a la granularidad entre la dimensión común y el grupo de medida seleccionado.|  
|**Minería de datos**|Especifica una relación de dimensión de minería de datos. En el panel **Detalle** se muestran las siguientes opciones:|**Dimensión de destino**: Muestra la dimensión de minería de datos seleccionado.<br /><br /> Nota: Debe seleccionar una dimensión de minería de datos para crear una relación de dimensión de minería de datos.|  
|||**Dimensión de origen**: Selecciona la dimensión en la que la dimensión de minería de datos proporciona análisis predictivos.|  
  
## <a name="see-also"></a>Vea también  
 [Relaciones de dimensión](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Uso de dimensiones &#40;Diseñador de cubos&#41; &#40;Analysis Services - datos multidimensionales&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md)   
 [Diseñadores y cuadros de diálogo de Analysis Services &#40;datos multidimensionales&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
