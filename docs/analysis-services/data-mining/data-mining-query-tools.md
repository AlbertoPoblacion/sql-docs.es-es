---
title: "Herramientas de consulta de minería de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- predictions [Analysis Services]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: a8952427-fd8c-4300-8f62-25f57ac1be0c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71337bc66abab8e91fd997cd2cde635945b0ef82
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="data-mining-query-tools"></a>Herramientas de consulta de minería de datos
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Todas las consultas de minería de datos usan el lenguaje DMX (Extensiones de minería de datos). DMX se puede usar para crear modelos para todos los tipos de tareas de aprendizaje automático, como clasificación, análisis de riesgos, generación de recomendaciones y regresión lineal. También se pueden escribir consultas DMX para obtener información sobre los patrones y estadísticas que se generen al procesar el modelo.  
  
 Puede escribir su propia consulta DMX, o bien puede crear una consulta DMX básica con una herramienta como el **Generador de consultas de predicción** y, después, modificarla. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] proporcionan herramientas que le ayudarán a generar las consultas de predicción DMX. En este tema se describe cómo crear y ejecutar consultas de minería de datos con estas herramientas.  
  
-   [Generador de consultas de predicción](#bkmk_Builder)  
  
-   [Editor de consultas](#bkmk_QueryEditor)  
  
-   [Plantillas DMX](#bkmk_Templates)  
  
-   [Integration Services](#bkmk_SSIS)  
  
-   [Interfaces de programación de aplicaciones](#bkmk_API)  
  
##  <a name="bkmk_Builder"></a> Generador de consultas de predicción  
 El Generador de consultas de predicción se incluye en la pestaña **Predicción de modelo de minería de datos** del Diseñador de minería de datos, el cual está disponible en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]y en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Al usar el generador de consultas, puede seleccionar un modelo de minería de datos, agregar nuevos datos de casos y agregar funciones de predicción. Después, puede cambiar al editor de texto para modificar la consulta de forma manual, o bien cambiar al panel de **resultados** para ver los resultados de la consulta.  
  
##  <a name="bkmk_QueryEditor"></a> Editor de consultas  
 El Editor de consultas de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] también le permite crear y ejecutar consultas DMX. Puede conectarse a una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]y, después, seleccionar una base de datos, columnas de estructura de minería de datos y un modelo de minería de datos. El **Explorador de metadatos** contiene una lista de funciones de predicción que puede examinar.  
  
##  <a name="bkmk_Templates"></a> Plantillas DMX  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] proporciona plantillas de consulta DMX interactivas que puede usar para compilar consultas DMX. Si no ve la lista de plantillas, haga clic en **Ver** en la barra de herramientas y seleccione **Explorador de plantillas**. Para ver todas las plantillas de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , incluidas las plantillas para DMX, MDX y XMLA, haga clic en el icono de cubo.  
  
 Para compilar una consulta mediante una plantilla, puede arrastrar la plantilla a una ventana de consulta abierta, o puede hacer doble clic en la plantilla para abrir una nueva conexión y un nuevo panel de consulta.  
  
 Para consultar un ejemplo de cómo crear una consulta de predicción a partir de una plantilla, vea [Crear una consulta de predicción singleton desde una plantilla](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md).  
  
> [!WARNING]  
>  El Complemento de minería de datos para Microsoft Office Excel también contiene varias plantillas, junto con un generador de consultas interactivo que puede ayudarle a crear instrucciones DMX complejas. Para utilizar las plantillas, haga clic en **Consulta**, y haga clic en **Avanzadas** en el Cliente de minería de datos.  
  
##  <a name="bkmk_SSIS"></a> Componentes de minería de datos de Integration Services  
 También puede incluir consultas de predicción como parte de un paquete de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Las siguientes tareas y transformaciones de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] admiten la creación y ejecución de consultas de predicción DMX e instrucciones DMX.  
  
|Componente|Description|  
|---------------|-----------------|  
|Tarea Consulta de minería de datos|Ejecuta consultas DMX y otras instrucciones DMX como parte de un flujo de control.<br /><br /> El editor de tareas incorpora el Generador de consultas de predicción y un cuadro de texto para modificar la consulta DMX manualmente. Sin embargo, el editor de tareas no puede validar la consulta con los objetos de una solución de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Por consiguiente, es mejor crear una consulta dentro de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] o [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] y, a continuación, pegar el texto de la instrucción o consulta en el editor de tareas.|  
|Consulta de minería de datos, transformación|Ejecuta una consulta de predicción en un flujo de datos usando los datos proporcionados por un origen de flujo de datos.<br /><br /> El editor de tareas incorpora el Generador de consultas de predicción y un cuadro de texto para modificar la consulta DMX manualmente.<br /><br /> La transformación solo se puede utilizar para crear consultas que utilicen los datos del flujo de datos; es decir, consultas que utilicen la sintaxis de PREDICTION JOIN. Este componente no se puede utilizar para ejecutar consultas de contenido u otros tipos de instrucciones DMX.|  
  
##  <a name="bkmk_API"></a> Interfaces de programación de aplicaciones  
 Puede crear aplicaciones personalizadas que ejecuten consultas en modelos de minería de datos mediante distintos lenguajes de programación, junto con protocolos de servidor como OLE DB o el cliente ADOMD de Analysis Services. Para más información, vea [Programación de minería de datos](../../analysis-services/data-mining-programming.md).  
  
 Sin embargo, XMLA constituye el formato del mensaje subyacente para todas las interacciones con un servidor de Analysis Services. En un mensaje XMLA, las consultas se representan de forma diferente dependiendo de si se envía una consulta de predicción basada en DMX, una consulta de contenido o una consulta que recupera metadatos del modelo mediante los conjuntos de filas de esquema de minería de datos.  
  
-   El texto de las **consultas de predicción** (y el resto de las instrucciones DMX) se envían en XMLA con el [método Execute &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md), con la consulta DMX colocada como texto en el [elemento Statement &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) del [elemento Command &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md).  
  
-   Para recuperar el **contenido del modelo** y los **metadatos del modelo**, como el número de clústeres, los atributos usados en los árboles de decisión, la fecha en que se procesó el modelo por última vez y los parámetros del algoritmo que se usaron al crear el modelo, puede usar el método [Discover &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md) y especificar uno de los conjuntos de filas del esquema de minería de datos en el encabezado del [elemento RequestType &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md). Para restringir el ámbito de la consulta, escriba los criterios como restricciones en el [elemento RestrictionList &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/restrictionlist-element-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de minería de datos &#40; DMX &#41; Referencia](../../dmx/data-mining-extensions-dmx-reference.md)   
 [Soluciones de minería de datos](../../analysis-services/data-mining/data-mining-solutions.md)   
 [Descripción de la instrucción Select de DMX](../../dmx/understanding-the-dmx-select-statement.md)   
 [Estructura y el uso de consultas de predicción DMX](../../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Crear una consulta de predicción mediante el generador de consultas de predicción](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)   
 [Crear una consulta DMX en SQL Server Management Studio](../../analysis-services/data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
  
