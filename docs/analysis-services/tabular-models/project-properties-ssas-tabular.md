---
title: Propiedades del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.depservconfig.f1
- sql13.asvs.bidtoolset.semmodelprojprop.f1
ms.assetid: 333c1fc0-361c-415a-bd68-4e057f67bcb7
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c24ad4d059199fad6e59e1c3dafe070a523ce52d
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="project-properties"></a>Propiedades del proyecto 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Este artículo describen propiedades del proyecto de modelo. Todos los proyectos de modelos tabulares tienen propiedades de opciones de implementación y de servidor de implementación que especifican cómo se implementan el proyecto y el modelo. Por ejemplo, el servidor en el que se implementará el modelo y el nombre de la base de datos de modelo implementada. Estos valores son diferentes de las propiedades del modelo, que afectan a la base de datos del área de trabajo del modelo. Las propiedades del proyecto descritas a continuación se muestran en un cuadro de diálogo de propiedades de modo, que es diferente de la ventana de propiedades utilizada para mostrar otros tipos de propiedades. Para ver las propiedades del proyecto modal, en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y luego haga clic en **Propiedades**.  
  
 Secciones de este tema:  
  
-   [Propiedades de proyecto](#bkmk_proj_properties)  
  
-   [Configurar las propiedades predeterminadas de modelado de datos y de implementación (SSAS tabular)](#bkmk_conf_proj_settings)  
  
##  <a name="bkmk_proj_properties"></a> Propiedades del proyecto  
 **Opciones de implementación**  
  
|Propiedad|Valor predeterminado|Description|  
|--------------|---------------------|-----------------|  
|**Opción de procesamiento**|**Valor de DB-Library**|De manera predeterminada, Analysis Services determinará el tipo de procesamiento necesario cuando se implementen los cambios en los objetos. Eso se suele traducir en el tiempo de implementación más breve. Sin embargo, también puede elegir un procesamiento completo o ningún procesamiento durante cada implementación.|  
|**Implementación transaccional**|**False**|Especifica si la implementación del modelo es o no transaccional. De manera predeterminada, la implementación de todos los objetos modificados no es transaccional con el procesamiento de dichos objetos implementados. La implementación puede ser correcta y persistir aunque se produzca un error de procesamiento. Puede cambiar este comportamiento para incluir la implementación y el procesamiento en una sola transacción.|  
|**Modo de consulta**|**In-Memory**|Especifica el origen desde el que se devuelven los resultados de la consulta. Para obtener más información, consulte [Directquerymode](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md).|  
  
 **Servidor de implementación**  
  
|Propiedad|Valor predeterminado|Description|  
|--------------|---------------------|-----------------|  
|**Server**|**localhost**|Especifica una instancia de Analysis Services. De forma predeterminada, los modelos se implementan en la instancia predeterminada de Analysis Services del equipo local. Puede cambiar este valor para especificar una instancia con nombre del equipo local o cualquier instancia de cualquier equipo remoto en que tenga permiso para crear objetos de Analysis Services. Normalmente, serán permisos de administrador.<br /><br /> El valor predeterminado de esta propiedad se puede modificar mediante la propiedad Servidor de implementación predeterminado de la página Implementación de la configuración de Analysis Server en el cuadro de diálogo Herramientas\Opciones. Para obtener más información, consulte [configurar las propiedades de implementación y de modelado de datos predeterminadas](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).|  
|**Edición**|**Desarrollador**|Especifica la edición del servidor de Analysis Services en la que se implementará el modelo. La edición del servidor define varias características que se pueden incorporar al proyecto.|  
|**Base de datos**|**Modelo**|Especifica el nombre de la base de datos de Analysis Services en la que se crearán instancias de los objetos de modelo durante la implementación. Este nombre se especificará en una conexión de datos o en un archivo de conexión de datos .rsds. Se recomienda que el nombre refleje el tipo de análisis que se realizará usando el modelo, por ejemplo, AdventureWorksSalesModel.<br /><br /> Con objeto de evitar los nombres duplicados en los modelos implementados, cambie el valor del nombre de la propiedad **Base de datos** para que refleje el propósito del modelo. Cuando los usuarios se conecten al modelo como origen de datos, este es el nombre que verán.|  
|**Nombre del cubo**|**Modelo**|Especifica el nombre del cubo de base de datos tal como se muestra en una conexión de datos del cliente de informes.|  
|**Versión**|**13.0**|Versión de la instancia de Analysis Services en la que se implementará el proyecto.|  
  
 **Opciones de DirectQuery**  
  
|Propiedad|Valor predeterminado|Description|  
|--------------|---------------------|-----------------|  
|**Configuración de suplantación**|**Valor de DB-Library**|Especifica las credenciales utilizadas para conectar a los orígenes de datos de un modelo que se ejecuta en el modo DirectQuery. Estas credenciales son diferentes de las credenciales de suplantación que se usan en el modo In-Memory predeterminado. Para obtener más información, consulte [suplantación](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).|  
  
##  <a name="bkmk_conf_proj_settings"></a> Configurar las propiedades predeterminadas de modelado de datos y de implementación (SSAS tabular)  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y, luego, haga clic en **Propiedades**.  
  
2.  En la ventana **Propiedades** , haga clic en una propiedad y, a continuación, escriba un valor o haga clic en la flecha abajo para seleccionar una opción de configuración.  
  
## <a name="see-also"></a>Vea también  
 [Configurar las propiedades de implementación y de modelado de datos predeterminadas](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [Propiedades del modelo](../../analysis-services/tabular-models/model-properties-ssas-tabular.md)   
 [Implementación de soluciones de modelos tabulares](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
  
