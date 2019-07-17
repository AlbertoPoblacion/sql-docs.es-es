---
title: Diseñador de modelos tabulares de Analysis Services en SQL Server Data Tools | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8be4f1f78b444933cc1ad7f4ec4fb71b28bfae1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207475"
---
# <a name="tabular-model-designer"></a>Diseñador de modelos tabulares
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
El diseñador de modelos tabulares forma parte de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], integrado con Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], con plantillas adicionales de tipo de proyecto para el desarrollo específico de soluciones de modelos tabulares profesionales.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] se instala como una descarga web gratuita. Vea [Descargar SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md) para más información.    
  
##  <a name="bkmk_benefits"></a> Ventajas  
 Al instalar [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], se agregan nuevas plantillas de proyecto para crear modelos tabulares a los tipos de proyecto disponibles. Una vez creado un proyecto de modelo tabular mediante una de las plantillas, puede empezar a crear modelos mediante las herramientas y los asistentes del diseñador de modelos tabulares.  
  
 Además de las nuevas plantillas y herramientas para crear soluciones de modelos tabulares y multidimensionales profesionales, el entorno de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proporciona funciones para la depuración y el ciclo de vida de los proyectos que le permiten asegurarse de que crea las soluciones BI más eficaces para su organización. Para obtener más información sobre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vea [Introducción a Visual Studio](http://go.microsoft.com/fwlink/?LinkId=206389).  
  
##  <a name="bkmk_proj_temp"></a> Plantillas de proyecto  
 Al instalar [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], se agregan las siguientes plantillas de proyectos de modelos tabulares a los tipos de proyecto de Business Intelligence:  
  
 **Proyecto tabular de Analysis Services**  
 Esta plantilla se puede usar para crear un proyecto de modelo tabular en blanco. Los niveles de compatibilidad se especifican al crear el proyecto.
  
 **Importar del servidor (tabular)**  
 Esta plantilla se puede usar para crear un proyecto de modelo tabular extrayendo los metadatos de uno ya existente en Analysis Services.  
  
 Los modelos más antiguos tienen niveles de compatibilidad más antiguos. Puede actualizar al cambiar la propiedad de nivel de compatibilidad después de importar la definición del modelo.  
  
 **Importar desde [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**  
 Esta plantilla se usa para crear un proyecto de modelo tabular extrayendo los metadatos y los datos de un archivo de [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] .  
  
##  <a name="bkmk_wind_men"></a> Ventanas y menús  
 El entorno de creación de modelos tabulares de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] incluye lo siguiente:  
  
### <a name="designer-window"></a>Ventana del diseñador  
 La ventana del diseñador se usa para crear modelos tabulares y proporciona una representación visual del modelo. Cuando se abre el archivo Model.bim, el modelo se abre en la ventana del diseñador. Puede crear un modelo en la ventana del diseñador con dos modos de vista diferentes:  
  
 **Vista de datos**  
 La vista de datos muestra las tablas en un formato de cuadrícula tabular. También puede definir medidas con la cuadrícula de medidas, que se puede mostrar para cada tabla únicamente en la vista de datos.  
  
 **Vista de diagrama**  
 La vista de diagrama muestra las tablas, con las relaciones entre ellas, en un formato gráfico. Se pueden filtrar las columnas, las medidas, las jerarquías y los KPI, y se puede ver el modelo con una perspectiva definida.  
  
 La mayoría de las tareas de creación de modelos se pueden realizar en cualquiera de las dos vistas.  
  
### <a name="view-code-window"></a>Ver la ventana de código  
 Puede ver el código subyacente de un archivo Model.bim si hace clic con el botón derecho y selecciona **Ver código** en el archivo en el Explorador de soluciones. Para los modelos tabulares en el nivel de compatibilidad 1200 y versiones posterior, la definición del modelo se expresa en JSON.  
  
 Tenga en cuenta que necesitará una versión completa de Visual Studio que proporcione el editor de JSON. Puede descargar e instalar la [edición gratuita de Visual Studio Community](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) si no necesita las características adicionales de las ediciones comerciales.  
  
### <a name="solution-explorer"></a>Explorador de soluciones  
 La ventana del Explorador de soluciones presenta la solución activa como un contenedor lógico para un proyecto de modelo tabular y sus elementos asociados. El proyecto de modelos (.smproj) solo contiene un objeto References (vacío) y el archivo Model.bim. Desde esta vista, puede abrir directamente elementos de un proyecto para modificarlos o realizar otras tareas de administración.  
  
 Las soluciones del modelo tabular normalmente contienen un solo proyecto; sin embargo, una solución puede contener también otros proyectos; por ejemplo, un proyecto de Integration Services o de Reporting Services. También puede agregar cualquier número de archivos siempre y cuando no sean del mismo tipo que los archivos del proyecto de modelo tabular y la propiedad Acción de compilación esté establecida en Ninguna o la propiedad Copiar en el directorio de resultados esté establecida en No copiar.  
  
 Para ver el Explorador de soluciones, haga clic en el menú **Ver** y, a continuación, haga clic en **Explorador de soluciones**.  

### <a name="tabular-model-explorer"></a>Explorador de modelos tabulares
  Primera disponible en la versión de agosto de 2016 (14.0.60812.0) de [SQL Server Data Tools](https://msdn.microsoft.com/mt186501), Explorador de modelos tabulares le ayuda a navegar por los objetos de metadatos en los modelos tabulares.

 Para mostrar el Explorador de modelos tabulares, haga clic en **Ver** > **Otras ventanas**y, a continuación, en el **Explorador de modelos tabulares**.
   
  ![Explorador de modelos tabulares](../../analysis-services/tabular-models/media/tabular-model-explorer.png) 
  
 Explorador de modelos tabulares organiza los objetos de metadatos en una estructura de árbol que se parezca al esquema de un modelo tabular. Orígenes de datos, Perspectivas, Relaciones, Roles, Tablas y Traducciones corresponden a objetos de esquema de nivel superior. Existen algunas excepciones, específicamente los KPI y medidas, que técnicamente no son objetos de nivel superior, pero los objetos secundarios de las distintas tablas en el modelo. Sin embargo, tener contenedores de nivel superior consolidados para todos los KPI y Medidas facilita el trabajo con estos objetos, especialmente si el modelo incluye un número de tablas muy grande. Las Medidas también se enumeran en sus tablas primarias correspondientes para que tenga una visión clara de las relaciones de elementos primarios y secundarios reales. Si selecciona una medida en el contenedor Medidas de nivel superior, también se seleccionará la misma medida en la colección secundaria en su tabla y viceversa.  
 
 Los nodos de objeto del Explorador de modelos tabulares se vinculan a opciones de menú adecuadas que hasta ahora se ocultaban en los menús Modelo, Tabla y Columna en Visual Studio. Puede hacer clic con el botón derecho en un objeto a fin de explorar opciones para el tipo de objeto. No todos los tipos de nodo de objeto gozan ya de un menú contextual, pero mejoras y opciones adicionales llegarán en versiones posteriores. 

 El Explorador de modelos tabulares también ofrece una cómoda característica de búsqueda. Solo tiene que escribir una parte del nombre en el cuadro de búsqueda y el Explorador de modelos tabulares restringirá la vista de árbol a las coincidencias. 
  
### <a name="properties-window"></a>Ventana Propiedades  
 La ventana Propiedades enumera las propiedades del objeto seleccionado. Los objetos siguientes tienen propiedades que se pueden ver y modificar en la ventana Propiedades:  
  
-   Model.bim  
  
-   Tabla  
  
-   columna  
  
-   Measure  
  
 Propiedades del proyecto muestran sólo el nombre del proyecto y la carpeta de proyecto en la ventana Propiedades. Los proyectos también tienen valores de opciones de implementación y de servidor de implementación adicionales que se pueden establecer mediante un cuadro de diálogo de propiedades modales. Para ver estas propiedades, en el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **Propiedades**.  
  
 Los campos de la ventana Propiedades tienen incrustados controles que se abren al hacer clic en ellos. El tipo de control de edición depende de la propiedad concreta. Entre los controles se incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo personalizados. Las propiedades que aparecen atenuadas son de solo lectura.  
  
 Para ver la ventana **Propiedades** , haga clic en el menú **Ver** y, a continuación, haga clic en **Ventana de propiedades**.  
  
### <a name="error-list"></a>Lista de errores  
 La ventana Lista de errores contiene mensajes sobre el estado del modelo:  
  
-   Notificaciones sobre las prácticas recomendadas de seguridad.  
  
-   Requisitos del procesamiento de datos.  
  
-   Información sobre los errores semánticos para las columnas calculadas y las medidas, así como filtros de fila para los roles. En las columnas calculadas, puede hacer doble clic en el mensaje de error para desplazarse al origen del error.  
  
-   Errores de validación de DirectQuery.  
  
 De forma predeterminada, la **Lista de errores** no aparecerá a menos que se devuelva un error. No obstante, puede ver la ventana **Lista de errores** en cualquier momento. Para ver la ventana **Lista de errores** , haga clic en el menú **Ver** y, a continuación, haga clic en **Lista de errores**.  
  
### <a name="output"></a>Salida  
 En la ventana de **Salida** se muestra información sobre la generación e implementación (además del diálogo de progreso modal). Para ver la ventana **Salida** , haga clic en el menú **Ver** y, a continuación, haga clic en Salida.  
  
### <a name="menu-items"></a>Elementos de menú  
 Al instalar [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], se agregan a la barra de menús de Visual Studio elementos de menú adicionales específicos para la creación de modelos tabulares. El menú **Modelo** se puede utilizar para iniciar el Asistente para la importación de datos, ver las conexiones existentes, procesar los datos del área de trabajo y examinar el área de trabajo del modelo en [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. El menú **Tabla** se utiliza para crear y administrar las relaciones entre las tablas, crear y administrar medidas, especificar valores de tablas de datos, así como para especificar opciones de cálculo y otras propiedades de las tablas. En el menú **Columna** , puede agregar y eliminar columnas de una tabla, ocultar y mostrar columnas, y especificar otras propiedades de las columnas, como tipos de datos y filtros. En el menú **Compilar** , puede compilar e implementar soluciones de modelos tabulares. Las funciones de copiar y pegar se incluyen en el menú **Edición** .  
  
 Además de estos elementos de menú, se han agregado valores adicionales a las opciones de Analysis Services en los elementos del menú Herramientas.  
  
### <a name="toolbar"></a>Barra de herramientas  
 La barra de herramientas de Analysis Services proporciona un acceso rápido y fácil a los comandos de creación de modelos usados con más frecuencia.  
  
##  <a name="bkmk_vsint"></a> Integración de Visual Studio  
 **Control de código fuente**  
 Los proyectos de Analysis Services se integran con el complemento de control de código fuente seleccionado. Si ha configurado Visual Studio para usar el control de código fuente, puede usar las funciones de protección/desprotección desde el Explorador de soluciones. Para configurar el uso de Team Foundation Server, vea [Configurar Visual Studio con el control de versiones de Team Foundation](http://msdn.microsoft.com/library/ms253064.aspx). También se admiten muchos complementos de control de código fuente de terceros.  
  
 **Fuentes**  
 Los modelos tabulares usan la fuente del entorno de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para controlar las fuentes en la pantalla. Puede que sea necesario cambiar esta fuente si la fuente predeterminada de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no tiene todos los caracteres Unicode necesarios para su idioma. Para cambiar las fuentes, haga clic en el menú **Herramientas** , haga clic en **Opciones**y, a continuación, haga clic en **Fuentes y colores**.  
  
 **Métodos abreviados de teclado**  
 Los métodos abreviados de teclado de Analysis Services se pueden configurar/reasignar con el cuadro de diálogo Herramientas->Opciones->Teclado. Algunos métodos abreviados globales de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , como compilar, guardar, depurar, nuevo proyecto, etc. se admiten en el contexto del diseñador de modelos tabulares. Otros métodos abreviados específicos del diseñador de modelos tabulares se encuentran en el contexto de Analysis Services.  
  
## <a name="see-also"></a>Vea también  
 [Proyectos de modelos tabulares](../../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md)   
  
  
