---
title: Información general sobre la programación de Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services, programming
- architecture [Integration Services]
- assemblies [Integration Services]
- SSIS, programming
- SQL Server Integration Services, programming
- run-time engine [Integration Services]
- packages [Integration Services], programming
- data flow engine [Integration Services]
- languages [Integration Services]
ms.assetid: 262babc6-eea5-4609-bc65-07d64cbcfee9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f540278d8f27eb091d4818f838d069c82a61159c
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296214"
---
# <a name="integration-services-programming-overview"></a>Información general sobre la programación de Integration Services

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tiene una arquitectura que separa el movimiento y la transformación de datos del flujo de control y la administración de paquetes. Existen dos motores distintos que definen esta arquitectura y que se pueden automatizar y extender al programar [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. El motor en tiempo de ejecución implementa la infraestructura de administración de flujo de control y paquetes que permite a los programadores controlar el flujo de ejecución y establecer opciones de para registro, controladores de eventos y variables. El motor de flujo de datos es un motor especializado de alto rendimiento que se dedica exclusivamente a extraer, transformar y cargar datos. Al programar [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], estará programando en estos dos motores.  
  
 La imagen siguiente describe la arquitectura de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 ![Arquitectura de Integration Services](../integration-services/media/mw-dts-01.gif "Integration Services architecture")  
  
## <a name="integration-services-run-time-engine"></a>Motor en tiempo de ejecución de Integration Services  
 El motor en tiempo de ejecución de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] controla la administración y ejecución de paquetes, implementando la infraestructura que habilita el orden de ejecución, el registro, las variables y el control de eventos. La programación del motor en tiempo de ejecución de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] permite a los programadores automatizar la creación, configuración y ejecución de paquetes, así como crear tareas personalizadas y otras extensiones.  
  
 Para obtener más información, consulte [Extender el paquete con la tarea Script](../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md), [Desarrollar una tarea personalizada](../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md) y [Building Packages Programmatically](../integration-services/building-packages-programmatically/building-packages-programmatically.md) (Crear paquetes mediante programación).  
  
## <a name="integration-services-data-flow-engine"></a>Motor de flujo de datos de Integration Services  
 El motor de flujo de datos administra la tarea de flujo de datos, una tarea especializada de alto rendimiento dedicada a mover y transformar datos de diferentes orígenes. A diferencia de otras tareas, la tarea de flujo de datos contiene objetos adicionales denominados componentes de flujo de datos, que pueden ser orígenes, transformaciones o destinos. Estos componentes son las partes móviles básicas de la tarea. Definen el movimiento y la transformación de los datos. La programación del motor de flujo de datos permite a los programadores automatizar la creación y configuración de los componentes en una tarea de flujo de datos, así como crear componentes personalizados.  
  
 Para obtener más información, consulte [Ampliar el flujo de datos con el componente de script](../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md), [Desarrollar un componente de flujo de datos personalizado](../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) y [Building Packages Programmatically](../integration-services/building-packages-programmatically/building-packages-programmatically.md) (Crear paquetes mediante programación).  
  
## <a name="supported-languages"></a>Idiomas admitidos  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] es totalmente compatible con [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Esto permite a los programadores programar [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en su opción de lenguajes .NET compatibles. Aunque el motor en tiempo de ejecución y el motor de flujo de datos se escriben en código nativo, ambos están disponibles a través de un modelo de objetos totalmente administrado.  
  
 Puede programar paquetes, tareas personalizadas y componentes de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o en otro editor de código o de texto. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ofrece al desarrollador muchas herramientas y características para simplificar y acelerar los ciclos iterativos de codificación, depuración y prueba. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] también simplifica la implementación. Sin embargo, no necesita [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para compilar y generar proyectos de código de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK incluye los compiladores [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../includes/csprcs-md.md)] y herramientas relacionadas.  
  
> [!IMPORTANT]  
>  De forma predeterminada, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] se instala con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], a diferencia de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Los vínculos al contenido de SDK de esta sección solo funcionarán si el SDK está instalado en el equipo y su documentación está incluida en la colección de Libros en pantalla. Después de instalar el SDK de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], puede agregar la documentación del SDK a la colección y la tabla de contenido de Libros en pantalla si sigue las instrucciones de [Agregar o quitar la documentación del producto para SQL Server](https://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052).  
  
 Tanto la tarea Script como el componente de script de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] usan [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) como entorno de scripting incrustado. VSTA es compatible con [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic y [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
> [!NOTE]  
>  Las interfaces de programación de aplicaciones de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] son incompatibles con lenguajes de scripting basados en COM como VBScript.  
  
## <a name="locating-assemblies"></a>Buscar ensamblados  
 En [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], los ensamblados de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] se actualizaron a .NET 4.0. Hay una memoria caché global de ensamblados diferente para .NET 4, que se encuentra en *\<unidad>* :\Windows\Microsoft.NET\assembly. Puede buscar todos los ensamblados de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bajo esta ruta de acceso, normalmente en la carpeta GAC_MSIL.  
  
 Como ocurre en versiones anteriores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], los archivos básicos de extensibilidad .dll de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] también se encuentran en *\<unidad>* :\Archivos de programa\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="commonly-used-assemblies"></a>Ensamblados de uso frecuente  
 En la tabla siguiente se enumeran los ensamblados que se suelen usar al programar [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] con [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
|Ensamblado|Descripción|  
|--------------|-----------------|  
|Microsoft.SqlServer.ManagedDTS.dll|Contiene el motor en tiempo de ejecución administrado.|  
|Microsoft.SqlServer.RuntimeWrapper.dll|Contiene el ensamblado de interoperabilidad primario (PIA), o contenedor, para el motor en tiempo de ejecución nativo.|  
|Microsoft.SqlServer.PipelineHost.dll|Contiene el motor de flujo de datos administrado.|  
|Microsoft.SqlServer.PipelineWrapper.dll|Contiene el ensamblado de interoperabilidad primario (PIA), o contenedor, para el motor de flujo de datos nativo.|  
  
  
