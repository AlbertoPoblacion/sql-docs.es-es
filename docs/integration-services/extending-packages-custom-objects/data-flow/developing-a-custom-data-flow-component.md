---
title: Desarrollar un componente de flujo de datos personalizado | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4b60aeb599e14881f69f548bff235f62e578c125
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67908735"
---
# <a name="developing-a-custom-data-flow-component"></a>Desarrollar un componente de flujo de datos personalizado

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La tarea de flujo de datos consta de componentes que se conectan a varios orígenes de datos y, a continuación, transforman y enrutan esos datos a alta velocidad. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] proporciona un modelo de objetos extensible que permite que los desarrolladores creen orígenes, transformaciones y destinos personalizados que se pueden utilizar en [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] y en paquetes implementados. En esta sección se incluyen temas que le guiarán a la hora de desarrollar componentes de flujo de datos personalizados.  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear un componente de flujo de datos personalizado](../../../integration-services/extending-packages-custom-objects/data-flow/creating-a-custom-data-flow-component.md)  
 Describe los pasos iniciales para crear un componente de flujo de datos personalizado.  
  
 [Métodos en tiempo de diseño de un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/design-time-methods-of-a-data-flow-component.md)  
 Describe los métodos en tiempo de diseño que se implementan en un componente de flujo de datos personalizado.  
  
 [Métodos en tiempo de ejecución de un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/run-time-methods-of-a-data-flow-component.md)  
 Describe los métodos en tiempo de ejecución que se implementan en un componente de flujo de datos personalizado.  
  
 [Plan de ejecución y asignación de búfer](../../../integration-services/extending-packages-custom-objects/data-flow/execution-plan-and-buffer-allocation.md)  
 Describe el plan de ejecución de flujo de datos y la asignación de búferes de datos.  
  
 [Trabajar con tipos de datos del flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)  
 Explica cómo el flujo de datos asigna los tipos de datos de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] a los tipos de datos administrados de .NET Framework.  
  
 [Validar un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)  
 Explica los métodos que se usan para validar la configuración de componentes y reconfigurar los metadatos del componente.  
  
 [Implementar metadatos externos](../../../integration-services/extending-packages-custom-objects/data-flow/implementing-external-metadata.md)  
 Explica cómo utilizar las columnas de metadatos externas para la validación de datos.  
  
 [Provocar y definir eventos en un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/raising-and-defining-events-in-a-data-flow-component.md)  
 Explica cómo provocar eventos predefinidos y personalizados.  
  
 [Registrar y definir entradas de registro en un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/logging-and-defining-log-entries-in-a-data-flow-component.md)  
 Explica cómo crear y escribir en las entradas de registro personalizadas.  
  
 [Usar las salidas de error en un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)  
 Explica cómo redirigir las filas del error a una salida alternativa.  
  
 [Actualizar la versión de un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/upgrading-the-version-of-a-data-flow-component.md)  
 Explica cómo actualizar los metadatos del componente guardados cuando se utiliza primero una nueva versión de su componente.  
  
 [Desarrollar una interfaz de usuario para un componente de flujo de datos](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-user-interface-for-a-data-flow-component.md)  
 Explica cómo implementar un editor personalizado para un componente.  
  
 [Desarrollar tipos específicos de componentes de flujo de datos](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
 Contiene información acerca de cómo desarrollar los tres tipos de componentes de flujo de datos: orígenes, transformaciones y destinos.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Contiene las clases e interfaces que se utilizan para crear componentes de flujo de datos personalizados.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Contiene las clases e interfaces que constituyen el modelo de objetos de una tarea de flujo de datos y se utiliza para crear componentes de flujo de datos personalizados o generar una tarea de flujo de datos.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>  
 Contiene las clases e interfaces que se utilizan para crear la interfaz de usuario para los componentes de flujo de datos.  
  
 [Referencia de errores y mensajes de Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)  
 Muestra los códigos de error predefinidos de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] con sus nombres simbólicos y sus descripciones.  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
### <a name="information-common-to-all-custom-objects"></a>Información común a todos los objetos personalizados  
 Para obtener información común a todos los tipos de objetos personalizados que puede crear en [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], vea los temas siguientes:  
  
 [Desarrollar objetos personalizados para Integration Services](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Describe los pasos básicos para implementar todos los tipos de objetos personalizados para [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Conservar objetos personalizados](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 Describe la persistencia personalizada y explica cuándo es necesaria.  
  
 [Generar, implementar y depurar objetos personalizados](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Describe las técnicas para generar, firmar, implementar y depurar objetos personalizados.  
  
### <a name="information-about-other-custom-objects"></a>Información sobre otros objetos personalizados  
 Para obtener información sobre los demás tipos de objetos personalizados que puede crear en [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], vea los temas siguientes:  
  
 [Desarrollar una tarea personalizada](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 Describe cómo programar las tareas personalizadas.  
  
 [Desarrollar un administrador de conexiones personalizado](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Describe cómo programar los administradores de conexiones personalizados.  
  
 [Desarrollar un proveedor de registro personalizado](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Describe cómo programar los proveedores de registro personalizados.  
  
 [Desarrollar un enumerador ForEach personalizado](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Describe cómo programar los enumeradores personalizados.  
  
## <a name="see-also"></a>Consulte también  
 [Ampliar el flujo de datos con el componente de script](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
 [Comparar soluciones de scripting y objetos personalizados](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
