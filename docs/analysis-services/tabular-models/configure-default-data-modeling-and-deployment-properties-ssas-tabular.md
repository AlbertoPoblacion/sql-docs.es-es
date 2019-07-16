---
title: Configurar datos de Analysis Services predeterminada de implementación y modelado propiedades | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 938ef21a83a6e08336c9e9c53a95e3886ab24dab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163088"
---
# <a name="configure-default-data-modeling-and-deployment-properties"></a>Configurar las propiedades predeterminadas de modelado de datos y de implementación 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  En este artículo se describe cómo configurar el nivel de compatibilidad predeterminado, implementación y configuración de propiedad de base de datos del área de trabajo, que se puede predefinir, para cada nuevo modelo tabular de proyecto cree en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Después de crear un proyecto nuevo, estas propiedades se pueden cambiar en función de sus necesidades específicas.  
  
#### <a name="to-configure-the-default-compatibility-level-property-setting-for-new-model-projects"></a>Para configurar el valor predeterminado de la propiedad Nivel de compatibilidad para los nuevos proyectos de modelos  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], haga clic en el menú **Herramientas** y, a continuación, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , expanda **Diseñadores tabulares de Analysis Services**y, a continuación, haga clic en **Nivel de compatibilidad**.  
  
3.  Configure los valores de las propiedades siguientes:  
  
    |Property|Valor predeterminado|Descripción|  
    |--------------|---------------------|-----------------|  
    |**Nivel de compatibilidad predeterminado para los nuevos proyectos**|SQL Server 2016 (1200)|Este valor especifica el nivel de compatibilidad predeterminado que se usará al crear un nuevo proyecto de modelo tabular. Puede elegir SQL Server 2012 (1100) si va a realizar la implementación en una instancia de Analysis Services sin SP1 aplicado o SQL Server 2012 SP1 o posterior si la instancia de implementación tiene aplicado SP1. Para más información, vea [Nivel de compatibilidad para modelos tabulares de Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
    |**Opciones de nivel compatibilidad**|Todas activadas|Especifica opciones de nivel de compatibilidad para los nuevos proyectos de modelos tabulares y al implementar en otra instancia de Analysis Services.|  
  
#### <a name="to-configure-the-default-deployment-server-property-setting-for-new-model-projects"></a>Para configurar el valor de propiedad de servidor de implementación predeterminado para los nuevos proyectos de modelos  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], haga clic en el menú **Herramientas** y, a continuación, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , expanda **Diseñadores tabulares de Analysis Services**y, a continuación, haga clic en **Implementación**.  
  
3.  Configure los valores de las propiedades siguientes:  
  
    |Property|Valor predeterminado|Descripción|  
    |--------------|---------------------|-----------------|  
    |**Servidor de implementación predeterminado**|localhost|Esta opción especifica el servidor predeterminado que debe usarse para implementar un modelo. Puede hacer clic en la flecha abajo para buscar en la red local los servidores de Analysis Services que puede utilizar o puede escribir el nombre de un servidor remoto.|  
  
    > [!NOTE]  
    >  Los cambios realizados en la configuración de la propiedad de servidor de implementación predeterminado no afectarán a los proyectos existentes creados antes de los cambios.  
  
###  <a name="bkmk_conf_default"></a> Para configurar el valor de propiedad de base de datos del área de trabajo predeterminada para los nuevos proyectos de modelos  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], haga clic en el menú **Herramientas** y, a continuación, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , expanda **Diseñadores tabulares de Analysis Services**y, a continuación, haga clic en **Base de datos del área de trabajo**.  
  
3.  Configure los valores de las propiedades siguientes:  
  
    |Property|Valor predeterminado|Descripción|  
    |--------------|---------------------|-----------------|  
    |**Servidor del área de trabajo predeterminado**|**localhost**|Esta propiedad especifica el servidor predeterminado que se usará para hospedar la base de datos del área de trabajo mientras se crea el modelo en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Todas las instancias disponibles de Analysis Services que se ejecutan en el equipo local se incluyen en el cuadro de lista.<br /><br /> <br /><br /> Nota: Se recomienda que especifique siempre un servidor de Analysis Services local como el servidor del área de trabajo. Para las bases de datos del área de trabajo de un servidor remoto, la importación de datos desde [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no se admite, no se pueden realizar copias de seguridad de los datos localmente y la interfaz de usuario puede experimentar latencia durante las consultas.|  
    |**Retención de la base de datos del área de trabajo después de cerrar el modelo**|**Mantener las bases de datos del área de trabajo en disco pero descargarlas de la memoria**|Especifica cómo se conserva una base de datos del área de trabajo después de que se cierre un modelo. Una base de datos del área de trabajo incluye los metadatos del modelo, los datos importados en un modelo y las credenciales de suplantación (cifradas). En algunos casos, la base de datos del área de trabajo puede ser muy grande y usar una cantidad significativa de memoria. De forma predeterminada, las bases de datos del área de trabajo se quitan de la memoria. Al cambiar este valor, es importante tener en cuenta los recursos de memoria disponibles así como la frecuencia con que se piensa trabajar en el modelo. El valor de esta propiedad tiene las opciones siguientes:<br /><br /> **Mantener el área de trabajo en memoria** : especifica que se mantengan en memoria las áreas de trabajo después de cerrar un modelo. Esta opción usará más memoria; sin embargo, al abrir un modelo en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]se usan menos recursos y el área de trabajo se cargará más rápido.<br /><br /> **Mantener las bases de datos del área de trabajo en disco, pero descargarlas de la memoria** : especifica que se mantenga la base de datos del área de trabajo en el disco (pero no en la memoria) después de cerrar un modelo. Esta opción usa menos memoria; sin embargo, al abrir un modelo en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]se usan recursos adicionales y el modelo se cargará más lentamente que cuando la base de datos del área de trabajo se mantiene en la memoria. Use esta opción cuando los recursos de memoria sean limitados o cuando trabaje en una base de datos de área de trabajo remota.<br /><br /> **Eliminar área de trabajo** : especifica que se elimine la base de datos del área de trabajo de la memoria y que no se mantenga en el disco después de cerrar el modelo. Aunque esta opción usa menos memoria y espacio de almacenamiento, al abrir un modelo en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], se usan recursos adicionales y el modelo se cargará con mayor lentitud que cuando la base de datos del área de trabajo se mantiene en la memoria o en el disco. Use esta opción cuando solo trabaje ocasionalmente con modelos.|  
    |**Copia de seguridad de datos**|**Mantener copias de seguridad de los datos en disco**|Especifica si se mantiene una copia de seguridad de los datos del modelo en un archivo de copia de seguridad. El valor de esta propiedad tiene las opciones siguientes:<br /><br /> **Mantener copia de seguridad de los datos en disco:** especifica que se mantenga una copia de seguridad de los datos del modelo en el disco. Cuando se guarda el modelo, los datos también se guardarán en el archivo de copia de seguridad (ABF). La selección de esta opción puede hacer que se alarguen los tiempos empleados para cargar y guardar modelos.<br /><br /> **No hacer copia de seguridad de los datos en disco** : especifica que no se mantenga una copia de seguridad de los datos del modelo en el disco. Esta opción minimizará el tiempo necesario para guardar y cargar el modelo.|  
  
> [!NOTE]  
>  Los cambios en las propiedades predeterminadas del modelo no afectarán a las propiedades de los modelos existentes creados antes de los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades del proyecto](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)   
 [Propiedades del modelo](../../analysis-services/tabular-models/model-properties-ssas-tabular.md)   
 [Nivel de compatibilidad](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
