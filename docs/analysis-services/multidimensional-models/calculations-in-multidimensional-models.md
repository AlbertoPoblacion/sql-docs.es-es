---
title: Cálculos en modelos multidimensionales | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c72d43c95013074051356c690ac2d7abf0a575e0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990508"
---
# <a name="calculations-in-multidimensional-models"></a>Cálculos en modelos multidimensionales
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Use la pestaña **Cálculos** del Diseñador de cubos para crear miembros calculados, conjuntos con nombre y otros cálculos de expresiones multidimensionales (MDX).  
  
 La pestaña **Cálculos** presenta los siguientes tres paneles:  
  
-   En el panel **Organizador de script** se enumeran los cálculos de un cubo. Utilice este panel para crear, organizar y seleccionar cálculos para su edición.  
  
-   El panel **Herramientas de cálculo** proporciona metadatos, funciones y plantillas con los que se crean los cálculos.  
  
-   El panel de las expresiones de cálculo admite una vista de formulario y otra de script.  
  
  
## <a name="creating-a-new-calculation"></a>Crear un cálculo  
 Para crear un cálculo, en la pestaña **Cálculos** del Diseñador de cubos, en el menú **Cubo** , haga clic en **Nuevo miembro calculado**, **Nuevo conjunto con nombre**, o **Nuevo comando de script**, según el tipo de cálculo que desee crear. También se puede hacer clic en cualquiera de los botones correspondientes de la barra de herramientas, o bien hacer clic con el botón derecho en cualquier punto del panel **Organizador de scripts** y, después, hacer clic en uno de los comandos del menú contextual. Esta acción agrega un nuevo cálculo al panel **Organizador de script** y muestra los campos correspondientes del formulario de cálculos del panel de las expresiones de cálculo. Si crea un nuevo script, esta acción abre la Vista de script del panel de las expresiones de cálculo. Para más información sobre cómo crear los tres tipos de cálculos, vea [Crear miembros calculados](../../analysis-services/multidimensional-models/create-calculated-members.md), [Crear conjuntos con nombre](../../analysis-services/multidimensional-models/create-named-sets.md)y [Definir asignaciones y otros comandos de script](../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md).  
  
## <a name="editing-scripts"></a>Editar scripts  
 Edite los scripts en el panel de las expresiones de cálculo de la pestaña **Cálculos** . El panel de las expresiones de cálculo tiene dos vistas: Vista de script y Vista de formulario. En la vista de formulario se muestran las expresiones y propiedades para un solo comando. Al editar un script MDX, un cuadro de expresión llena toda la Vista de formulario.  
  
 La Vista de script proporciona un editor de códigos en el que se editan los scripts. Cuando el panel de las expresiones de cálculo se encuentra en la Vista de script, el panel **Organizador de script** se encuentra oculto. La Vista de script proporciona codificación de color, coincidencia de paréntesis, autocompletar y regiones de código MDX. Las regiones de código MDX se pueden contraer o expandir para facilitar la edición.  
  
 Se puede alternar entre la Vista de formulario y la Vista de script haciendo clic en el menú **Cubo** , seleccionando **Mostrar cálculos en**y, a continuación, haciendo clic en **Script** o **Formulario**. También se puede hacer clic en **Vista de formulario** o **Vista de script** en la barra de herramientas.  
  
## <a name="changing-solve-order"></a>Cambiar el orden de resolución  
 Los cálculos se resuelven en el orden enumerado en el panel del **Organizador de script** . Para volver a ordenar los cálculos, haga clic con el botón derecho en cualquier cálculo y, después, haga clic en **Subir** o **Bajar** en el menú contextual. Puede hacer clic en un cálculo y luego hacer clic en el botón **Subir** o **Bajar** en la barra de herramientas.  
  
 Puede anular este orden de forma manual para las celdas calculadas y los miembros calculados. Para más información sobre el orden de paso y el orden de resolución, vea [Información sobre el orden de paso y el orden de solución &#40;MDX&#41;](../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
## <a name="deleting-a-calculation"></a>Eliminar un cálculo  
 Para eliminar un cálculo existente, en la pestaña **Cálculos** , en el panel **Organizador de script** , seleccione el cálculo que desee eliminar y haga clic en **Eliminar** en el menú **Editar** o haga clic en el icono de **Eliminar** de la barra de herramientas. También puede hacer clic con el botón derecho en el cálculo en el panel **Organizador de scripts** y seleccionar **Eliminar** en el menú contextual.  
  
  
