---
title: Crear Scripts de Analysis Services en Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services objects, scripts
- objects [Analysis Services], scripts
- scripts [Analysis Services], objects
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e3cca216f7c2312b4e7b54f2236a5d1f7bafd9e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080108"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a>Crear scripts de Analysis Services en Management Studio
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] incluye características, plantillas y editores de generación de script que se pueden usar para incluir objetos y tareas de Analysis Services en un script.  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a>Incluir tareas de Analysis Services en un script en Management Studio  
 La inclusión de tareas en un script en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] se logra haciendo clic en una de las opciones de script de un cuadro de diálogo orientado a tareas. Todos los cuadros de diálogo que se usan para realizar tareas tales como copia de seguridad o restauración de base de datos, procesar un objeto o diseñar una agregación, incluyen una opción de script en la parte superior del cuadro de diálogo. La selección de una de estas opciones genera un script XMLA basado en la información y los valores del cuadro de diálogo.  
  
 De forma predeterminada, el script se genera y se coloca en un editor de consultas XMLA, pero también se puede expandir la lista de opciones de script para dirigir el script al Portapapeles de Windows o a un archivo.  
  
#### <a name="to-script-an-analysis-services-task"></a>Para incluir en script una tarea de Analysis Services  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
2.  Haga clic con el botón derecho en una base de datos y haga clic en **Copia de seguridad**. Se abre el cuadro de diálogo Copia de seguridad de la base de datos. Especifique un nombre de archivo de copia de seguridad y elija las opciones que desee para esta copia de seguridad.  
  
3.  Haga clic en **Script** en la parte superior del cuadro de diálogo. La característica Script forma parte de todos los cuadros de diálogo basados en tareas en Management Studio. Tiene las siguientes opciones: **Script de acción en ventana nueva consulta** para abrir la ventana del editor de consultas, **acción de Script en archivo** para guardar el script XMLA en un archivo, o **acción de Script en Portapapeles** para guardar el script XMLA para el Portapapeles.  
  
     Tenga en cuenta que la opción **Generar script de acción en trabajo** que aparece como una opción de script en Management Studio no se admite para los scripts de Analysis Services.  
  
4.  Si selecciona la opción predeterminada, **Generar script de acción en la ventana Nueva consulta**, un script generado se colocará en una ventana de consulta XMLA.  
  
     A continuación puede cerrar el cuadro de diálogo Copia de seguridad de la base de datos y editar o ejecutar el script XMLA directamente.  
  
## <a name="script-analysis-services-objects-in-management-studio"></a>Incluir objetos de Analysis Services en un script en Management Studio  
 La inclusión de objetos en un script en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] se realiza haciendo clic con el botón derecho en un objeto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y seleccionando **Create to**, **Alter to**o **Delete to**. Cada una de estas opciones se puede dirigir a una ventana o a un archivo, pero independientemente de ello, aparecerá en forma de script DDL en un contenedor XMLA. Una enorme ventaja de estos scripts es que se pueden ejecutar en cualquier servidor. Igualmente, los nombres de los scripts pueden cambiarse y ejecutarse de manera reiterativa para la construcción, modificación o eliminación masiva de objetos.  
  
 Entre los objetos que se pueden incluir en un script se hallan los elementos de una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , incluidos orígenes de datos, vistas de origen de datos, cubos, dimensiones, estructuras de minería de datos y roles.  
  
 Entre los requisitos previos se incluye estar familiarizado con XML for Analysis (XMLA). Afortunadamente, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dispone de una característica que crea automáticamente el script XMLA necesario para crear objetos tales como cubos. Esta característica de automatización ayuda a reducir la curva de aprendizaje de XMLA. Para obtener más información sobre cómo usar XMLA, vea [Desarrollar con XMLA en Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md). Para obtener más información sobre cómo usar XMLA, vea [Desarrollar con XMLA en Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).  
  
> [!IMPORTANT]  
>  Al incluir el objeto Role en un script, debe tener presente que los permisos de seguridad están incluidos en los objetos que protegen y no en el rol de seguridad al que están asociados.  
  
#### <a name="to-script-analysis-services-objects"></a>Para incluir objetos de Analysis Services en script  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conéctese a una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
2.  Busque el objeto para el que desee crear un script que cree, altere o elimine objetos.  
  
3.  Haga clic en el objeto, elija **incluir cubo como**, apunte a **CREATE To**, **ALTER To**, o **Delete To**y, a continuación, haga clic en uno de los siguientes opciones: **Nueva ventana del Editor de consultas** para abrir la ventana del editor de consultas, **archivo** para guardar el script XMLA en un archivo, o **Portapapeles** para guardar el script XMLA en el Portapapeles.  
  
    > [!NOTE]  
    >  Normalmente se selecciona **Archivo** para crear versiones diferentes del archivo.  
  
## <a name="see-also"></a>Vea también  
 [Crear scripts para tareas administrativas en Analysis Services](../script-administrative-tasks-in-analysis-services.md)   
 [Editor de consultas XMLA &#40;Analysis Services: datos multidimensionales&#41;](../xmla-query-editor-analysis-services-multidimensional-data.md)  
  
  
