---
title: Ver atributos en el Diseñador de dimensiones | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c8e0535a1df60b4a4e1550e2b49a02e7a60e2c04
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179379"
---
# <a name="attribute-properties---view-attributes-in-dimension-designer"></a>Propiedades de atributos: Ver atributos en el Diseñador de dimensiones
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Los atributos se crean en objetos de dimensión. Para ver y configurar atributos, use el Diseñador de dimensiones en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. El panel **Atributos** de la pestaña **Estructura de dimensión** del Diseñador de dimensiones contiene los atributos presentes en una dimensión. Use este panel para agregar, quitar o configurar atributos. También puede seleccionar atributos para usarlos como un nivel en una jerarquía nueva o para agregarlos como un nivel a una jerarquía existente.  
  
 Para ver los atributos de una dimensión, abra el Diseñador de dimensiones para la dimensión. En el panel **Atributos** de la pestaña **Estructura de dimensión**  del diseñador se muestran los atributos presentes en la dimensión. Para cambiar entre una vista de lista, un árbol o una cuadrícula, seleccione **Mostrar atributos en** en el menú **Dimensión** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] y, a continuación, haga clic en uno de los comandos siguientes:  
  
1.  Mostrar atributos en una **Lista**. Muestra los atributos con formato de lista. Haga clic con el botón secundario en un atributo para eliminarlo de la lista, para cambiar su nombre o para cambiar su uso. Use esta vista para crear jerarquías. La información del atributo y las propiedades de miembro no están visibles.  
  
2.  Mostrar atributos en un **Árbol**. Muestra los atributos con formato de árbol, con la dimensión como nodo de nivel superior del árbol. Expanda un atributo para ver las relaciones de atributo correspondientes o para crear una nueva relación de atributo, efectuando las siguientes acciones:  
  
    -   Haga clic en la dimensión, un atributo o una propiedad del miembro para ver sus propiedades en la ventana **Propiedades** .  
  
    -   Haga clic con el botón secundario en un atributo o una propiedad del miembro para eliminarlo de la lista, para cambiar su nombre o para cambiar su uso.  
  
     Use esta vista para ver y crear propiedades de miembros. También puede utilizarla para generar jerarquías.  
  
3.  Mostrar atributos en una **Cuadrícula**. Muestra los atributos con formato de cuadrícula. La cuadrícula contiene las columnas siguientes:  
  
    -   **Nombre** muestra el valor de la propiedad **Name** . Escriba otro nombre para cambiar la configuración.  
  
    -   **Uso** especifica si se trata de un atributo Regular, Key, Parent o AccountType. Haga clic en un valor de la columna para seleccionar otra opción.  
  
    -   **Tipo** especifica la categoría de Business Intelligence para el atributo. Haga clic en esta celda para seleccionar otra opción.  
  
    -   **Columna de clave** muestra el tipo de datos OLE DB para la propiedad **KeyColumn** del atributo. Esta columna no puede modificarse.  
  
    -   **Columna de nombre** indica si el valor de la propiedad **NameColumn** en el atributo es la misma columna que el valor para la propiedad **KeyColumn** . Esta columna no puede modificarse.  
  
     Haga clic en una fila de la cuadrícula para ver las propiedades correspondientes a ese atributo.  
  
     Use esta vista para crear y configurar atributos.  
  
 En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], los iconos que aparecen en la tabla siguiente marcan los atributos según su uso.  
  
|Icono|Uso del atributo|  
|----------|---------------------|  
|![Icono atributo](../../analysis-services/multidimensional-models/media/as-icon-attribute.gif "icono de atributo")|Regular o AccountType|  
|![Icono de atributo clave](../../analysis-services/multidimensional-models/media/as-icon-key-attribute.gif "icono de atributo clave")|Key|  
|![Icono de atributo primario](../../analysis-services/multidimensional-models/media/as-icon-parent-attribute.gif "icono de atributo primario")|Parent|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de las propiedades de los atributos de dimensión](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
