---
title: Editar o eliminar particiones (Analysis Services - Multidimensional) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 739775890b324c89357ec4f1ba8f627277788087
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178227"
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a>Editar o eliminar particiones (Analysis Services - Multidimensional)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Las particiones de cubo se modifican mediante la pestaña **Particiones** del Diseñador de cubos en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. La pestaña **Particiones** presenta una lista de las particiones de todos los grupos de medida de un cubo. También muestra una lista de las particiones de reescritura que tienen habilitada esta característica.  
  
 Para editar las particiones de cualquier grupo de medida, expanda el grupo de medida en la pestaña **Particiones** . Las particiones de un grupo de medida aparecen ordenadas en una tabla por número ordinal, con las columnas incluidas en la tabla que aparece a continuación.  
  
 Los parámetros de un grupo de medida vinculado deben editarse en el cubo de origen.  
  
 La eliminación de particiones se realiza automáticamente al mezclar una partición de origen en una partición de destino. La partición especificada como origen se elimina una vez completada la mezcla. También puede eliminar particiones manualmente en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o en la pestaña Particiones de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Haga clic con el botón derecho y elija **Eliminar**. Recuerde que al eliminar una partición también se eliminan los datos y las agregaciones. Como medida de precaución, asegúrese de tener una copia de seguridad reciente de la base de datos por si necesita invertir este paso posteriormente.  
  
> [!NOTE]  
>  O bien, puede usar scripts XMLA que automaticen las tareas para crear, mezclar y eliminar particiones. El script XMLA se puede crear y ejecutar en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]o en paquetes personalizados de SSIS que se ejecutan como una tarea programada. Para más información, consulte [Automate Analysis Services Administrative Tasks with SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="partition-source"></a>Origen de la partición  
 Especifica la tabla o la consulta con nombre origen de la partición. Para cambiar la tabla de origen, haga clic en la celda y, después, haga clic en el botón Examinar ( **…** ).  
  
 ![Columna de origen en el panel de la partición](../../analysis-services/multidimensional-models/media/ssas-partitionsource.png "columna de origen en el panel de la partición")  
  
 Si la partición se basa en una consulta, haga clic en el botón Examinar ( **…** ) para editar la consulta. Esto edita la propiedad **Origen** de la partición. Para más información, consulte [Cambiar el origen de una partición para usar una tabla de hechos diferente](../../analysis-services/multidimensional-models/change-a-partition-source-to-use-a-different-fact-table.md).  
  
 Puede especificar una tabla en la vista del origen de datos que tenga la misma estructura que la tabla de origen original (en el origen de datos externo del que se recuperan los datos). El origen puede encontrarse en cualquier origen de datos o vista del origen de datos de la base de datos de cubo.  
  
## <a name="storage-settings"></a>Configuración de almacenamiento  
 En el Diseñador de cubos, en la pestaña Particiones, puede hacer clic en **Configuración de almacenamiento** para elegir una de las configuraciones estándar de almacenamiento MOLAP, ROLAP u HOLAP, así como configurar valores personalizados para el modo de almacenamiento y el almacenamiento automático en caché. El valor predeterminado es MOLAP porque es el que ofrece el rendimiento de las consultas más rápido. Para más información sobre cada opción, vea [Establecer el almacenamiento de particiones &#40;Analysis Services - Multidimensional&#41;](../../analysis-services/multidimensional-models/set-partition-storage-analysis-services-multidimensional.md).  
  
 El almacenamiento se puede configurar independientemente para cada partición de cada grupo de medida de un cubo. También puede configurar los valores de almacenamiento predeterminado de un cubo o un grupo de medida. El almacenamiento se configura en la pestaña **Particiones** del Asistente para cubos.  
  
## <a name="see-also"></a>Vea también  
 [Crear y administrar una partición local &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)   
 [Diseñar agregaciones &#40;Analysis Services - Multidimensional&#41;](../../analysis-services/multidimensional-models/designing-aggregations-analysis-services-multidimensional.md)   
 [Mezclar particiones en Analysis Services &#40;SSAS - Multidimensional&#41;](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
