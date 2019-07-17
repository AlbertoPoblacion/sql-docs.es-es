---
title: Base de datos de área de trabajo de Analysis Services en SQL Server Data Tools | Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3f9d94d35d5aaa4ea86cf1f1d9dc845b67eaf4f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162356"
---
# <a name="workspace-database"></a>Base de datos del área de trabajo

[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  La base de datos del área del trabajo de modelos tabulares, utilizada durante la creación de modelos, se crea cuando se crea un nuevo proyecto de modelos tabulares en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].
  
## <a name="specifying-a-workspace-instance"></a>Especificar una instancia del área de trabajo  

  Al crear un proyecto de modelo tabular en SSDT, puede especificar una instancia de Analysis Services para usarla al crear el proyecto. A partir de la versión de septiembre de 2016 (14.0.60918.0) de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], se introducen dos modos para especificar una instancia del área de trabajo al crear un proyecto de modelo tabular. 

**Área de trabajo integrada** : recomendada. Utiliza la instancia de Analysis Services interno de SSDT. Use esta opción al crear un proyecto que se implementará en Azure Analysis Services.

**Servidor del área de trabajo** : se crea una base de datos del área de trabajo en una instancia explícita de Analysis Services, muchas veces en el mismo equipo de SSDT o en otro equipo de la misma red. Aunque es posible especificar un servidor de Azure Analysis Services, no se recomienda. 
  
### <a name="integrated-workspace"></a>Área de trabajo integrada

Con el área de trabajo integrada, se crea una base de datos de trabajo en memoria mediante la propia instancia implícita de Analysis Services de SSDT. Modo de área de trabajo integrada reduce considerablemente la complejidad de crear proyectos tabulares en SSDT, porque no se requiere un servidor de Analysis Services independiente explícito.

Con el modo de área de trabajo integrada, SSDT Tabular inicia su propia instancia interna de SSAS de forma dinámica y en segundo plano y, luego, carga la base de datos. Puede agregar y ver tablas, columnas y datos en el Diseñador de modelos. Si agrega otras tablas, columnas, relaciones, etc., modificará la base de datos del área de trabajo. El modo de área de trabajo integrada no cambia el funcionamiento de SSDT Tabular con un servidor y una base de datos de área de trabajo. Lo que cambia es la ubicación en la que SSDT Tabular hospeda la base de datos del área de trabajo.

Puede seleccionar el modo de área de trabajo integrada al crear un proyecto de modelo tabular en SSDT.

![Modo de área de trabajo integrada de SSAS](../../analysis-services/tabular-models/media/ssas-integrated-workspace-mode.png)

Mediante las propiedades de la Base de datos del área de trabajo y del Servidor del área de trabajo de model.bim, puede detectar el nombre de la base de datos temporal y el puerto TCP de la instancia interna de SSAS en la que SSDT Tabular hospeda la base de datos. Puede conectarse a la base de datos del área de trabajo con SSMS, siempre y cuando SSDT Tabular tenga cargada la base de datos. La opción Retención de área de trabajo especifica que SSDT Tabular mantiene la base de datos del área de trabajo en el disco, pero no la conserva en la memoria al cerrar un proyecto de modelos. De esta forma se garantiza que se consuma menos memoria que si el modelo se mantuviera en memoria en todo momento. Si quiere controlar esta opción, establezca la propiedad Modo de área de trabajo integrada en False y proporcione un servidor explícito del área de trabajo. Un servidor de área de trabajo explícito también hacer sentidos si los datos que se va a importar en un modelo superan la capacidad de memoria de la estación de trabajo SSDT.

> [!NOTE]  
>  Cuando se usa el modo de área de trabajo integrada, la instancia local de Analysis Services es 64 bits, mientras que SSDT se ejecuta en el entorno de 32 bits de Visual Studio. Si se conecta a orígenes de datos especiales, asegúrese de instalar en la estación de trabajo las versiones de 32 y 64 bits de los proveedores de datos correspondientes. El proveedor de 64 bits es necesario para la instancia de Analysis Services de 64 bits y la versión de 32 bits es necesaria para el Asistente para importación de tablas en SSDT.

###  <a name="bkmk_overview"></a> Servidor del área de trabajo


 La base de datos del área de trabajo se crea en la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , especificada en la propiedad Servidor del área de trabajo, cuando se crea un proyecto de Business Intelligence usando una de las plantillas de proyectos de modelos tabulares de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Cada proyecto de modelos tabulares tendrá su propia base de datos del área de trabajo. Puede usar [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para ver la base de datos del área de trabajo en el servidor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . El nombre de la base de datos del área de trabajo incluye el nombre del proyecto seguido de un carácter de subrayado, el nombre de usuario, otro carácter de subrayado y un GUID.  
  
 La base de datos del área de trabajo reside en memoria mientras el proyecto de modelos tabulares está abierto en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Cuando se cierra el proyecto, la base de datos del área de trabajo, bien permanece en memoria, se almacena en disco y se quita de la memoria (valor predeterminado), o se quita de la memoria y no se almacena en disco, según lo que determine la propiedad Retención de área de trabajo. Para obtener más información sobre la propiedad Retención de área de trabajo, vea [Propiedades de la base de datos del área de trabajo](#bkmk_ws_prop) más adelante en este tema.  
  
 Cuando se ven tablas, columnas y datos en el Diseñador de modelos después de haber agregado datos a un proyecto de modelos mediante el uso del Asistente para la importación de tablas o con copiar y pegar, lo que se ve en realidad es la base de datos del área de trabajo. Si agrega otras tablas, columnas, relaciones, etc., cambiará la base de datos del área de trabajo.  
  
 Cuando se implementa un proyecto de modelos tabulares, la base de datos del modelo implementada, que es básicamente una copia de la base de datos del área de trabajo, se crea en la instancia del servidor de Analysis Services especificada en la propiedad Servidor de implementación. Para obtener más información acerca de la propiedad de servidor de implementación, consulte [las propiedades del proyecto](../../analysis-services/tabular-models/project-properties-ssas-tabular.md).  
  
 La base de datos del área de trabajo del modelo reside normalmente en un host local o en una instancia local con nombre de un servidor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si lo desea, puede usar una instancia remota de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para hospedar la base de datos del área de trabajo; sin embargo, no se recomienda usar esta configuración debido a la latencia que se produce durante las consultas de datos y otras restricciones. En condiciones óptimas, la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que hospedará la base de datos del área de trabajo se encuentra en el mismo equipo que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Crear proyectos de modelos en el mismo equipo en que se encuentra la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que hospeda la base de datos del área de trabajo puede mejorar el rendimiento.  
  
 Las bases de datos de área de trabajo remotas tienen las restricciones siguientes:  
  
-   Una latencia potencial durante las consultas.  
  
-   La propiedad Copia de seguridad de datos no se puede establecer en **Hacer copia de seguridad en disco**.  
  
-   No se pueden importar datos de un libro [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cuando se crea un nuevo proyecto de modelo tabular mediante la plantilla de proyecto Importar desde [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
  > [!IMPORTANT]  
>  El nivel de compatibilidad del modelo y el servidor del área de trabajo deben corresponderse.
  
> [!NOTE]  
>  Si alguna de las tablas del modelo contiene un gran número de filas, considere importar únicamente un subconjunto de los datos durante la creación del modelo. Si importa un subconjunto de los datos, puede reducir el tiempo de procesamiento y el consumo de recursos de servidor de bases de datos del área de trabajo.  
  
> [!NOTE]  
>  La ventana de vista previa de la página Seleccionar tablas y vistas del Asistente para la importación de tablas, el cuadro de diálogo Editar propiedades de tabla y el cuadro de diálogo Administrador de particiones muestran tablas, columnas y filas del origen de datos, pero es posible que no sean las mismas tablas, columnas y filas que las que muestra la base de datos del área de trabajo.  
  
  
##  <a name="bkmk_ws_prop"></a> Propiedades de la base de datos del área de trabajo  
 Las propiedades de la base de datos del área de trabajo están incluidas entre las propiedades del modelo. Para ver las propiedades del modelo, en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], en el **Explorador de soluciones**, haga clic en el archivo **Model.bim** . Las propiedades del modelo se pueden configurar usando la ventana **Propiedades** . Entre las propiedades específicas de la base de datos del área de trabajo se encuentran:  
  
> [!NOTE]  
>  Las propiedades **Modo de área de trabajo integrada**, **Servidor del área de trabajo**, **Retención del área de trabajo** y **Copia de seguridad de datos** tienen valores predeterminados que se aplican al crear un proyecto de modelos. Puede cambiar la configuración predeterminada de los nuevos proyectos de modelos en la página **Modelado de datos** de la configuración de **Analysis Server** del cuadro de diálogo Herramientas\Opciones. Estas propiedades, junto con otras, también se pueden establecer para cada proyecto de modelos en la ventana **Propiedades** . Si se cambia la configuración predeterminada, la nueva configuración no se aplicará a los proyectos de modelos creados previamente. Para obtener más información, consulte [configurar propiedades de implementación y modelado de datos predeterminada](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
|Property|Valor predeterminado|Descripción|  
|--------------|---------------------|-----------------|  
|**Modo de área de trabajo integrada**|True, False|Si se selecciona el modo de área de trabajo integrada para la base de datos del área de trabajo al crear el proyecto, esta propiedad será True. Si el modo **Servidor del área de trabajo** está seleccionado al crear el proyecto, esta propiedad será False. | 
|**Base de datos del área de trabajo**|Name|El nombre de la base de datos del área de trabajo. Esta propiedad no se puede editar si **Modo de área de trabajo integrada** es **True**.|  
|**Retención de área de trabajo**|Descargar de la memoria|Especifica cómo se conserva una base de datos del área de trabajo después de cerrar un proyecto de modelos. Una base de datos del área de trabajo incluye los metadatos del modelo y los datos importados. En algunos casos, la base de datos del área de trabajo puede ser muy grande y usar una gran cantidad de memoria. De forma predeterminada, cuando se cierra un proyecto de modelos en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], la base de datos del área de trabajo se descarga de la memoria. Si se cambia este valor, es importante tener en cuenta los recursos de memoria disponibles, así como la frecuencia con que se piensa trabajar en el proyecto de modelos. El valor de esta propiedad tiene las opciones siguientes:<br /><br /> **Mantener en memoria** : especifica que, después de cerrar un proyecto de modelos, es necesario mantener en memoria la base de datos del área de trabajo. Esta opción usará más memoria; sin embargo, al abrir un proyecto de modelos en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], se usan menos recursos y la base de datos del área de trabajo se cargará más rápido.<br /><br /> **Descargar de la memoria** : especifica que, después de cerrar un proyecto de modelos, es necesario conservar en el disco la base de datos del área de trabajo, pero no en memoria. Aunque esta opción usa menos memoria, al abrir un proyecto de modelos en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], es necesario volver a adjuntar la base de datos del área de trabajo, con lo que se usan recursos adicionales y el proyecto de modelos se carga más lentamente que cuando la base de datos del área de trabajo se mantiene en memoria. Use esta opción cuando los recursos de memoria sean limitados o cuando trabaje en una base de datos de área de trabajo remota.<br /><br /> **Eliminar área de trabajo** : especifica que es necesario eliminar de la memoria la base de datos del área de trabajo y que no hay que mantenerla en el disco después de cerrar el proyecto de modelos. Aunque esta opción usa menos memoria y espacio de almacenamiento, al abrir un proyecto de modelos en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], se usan recursos adicionales y el proyecto de modelos se cargará con mayor lentitud que cuando la base de datos del área de trabajo se mantiene en memoria o en disco. Utilice esta opción cuando solo trabaje ocasionalmente con proyectos de modelos.<br /><br /> La configuración predeterminada de esta propiedad se puede cambiar en la página **Modelado de datos** , en la configuración de **Analysis Server** del cuadro de diálogo Herramientas\Opciones. Esta propiedad no se puede editar si **Modo de área de trabajo integrada** es **True**.|  
|**Workspace Server**|localhost|Esta propiedad especifica el servidor predeterminado que se usará para hospedar la base de datos del área de trabajo mientras se crea el proyecto de modelos en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Todas las instancias disponibles de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que se ejecutan en el equipo local se incluyen en el cuadro de lista.<br /><br /> Para especificar un servidor diferente de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (que se ejecute en modo tabular), escriba su nombre. El usuario que ha iniciado sesión debe ser administrador del servidor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> Tenga en cuenta que se recomienda especificar un servidor local de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] como servidor del área de trabajo. Para las bases de datos del área de trabajo de un servidor remoto, la importación desde [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no se admite, no se pueden realizar copias de seguridad de los datos localmente y la interfaz de usuario puede experimentar latencia durante las consultas.<br /><br /> La configuración predeterminada de esta propiedad se puede cambiar en la página Modelado de datos, en la configuración de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] del cuadro de diálogo Herramientas\Opciones. Esta propiedad no se puede editar si **Modo de área de trabajo integrada** es **True**.|  
  
##  <a name="bkmk_use_ssms"></a> Usar SSMS para administrar la base de datos del área de trabajo  
 Puede usar SQL Server Management Studio (SSMS) para conectarse a un servidor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que hospeda una base de datos del área de trabajo. Por lo general, no es necesaria ninguna administración de la base de datos del área de trabajo; la excepción es cuando hay que separar o eliminar una base de datos del área de trabajo, operación que debe realizarse desde [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. No utilice [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para administrar la base de datos del área de trabajo mientras el proyecto está abierto en el diseñador de modelos. Si lo hace, podría provocar la pérdida de datos.
   
## <a name="see-also"></a>Vea también  
[Propiedades de modelo](../../analysis-services/tabular-models/model-properties-ssas-tabular.md) 
  
  
