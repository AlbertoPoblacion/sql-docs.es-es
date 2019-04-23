---
title: Creación de procedimientos almacenados | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7beb77adf595b055a6c1e4a7543b428a06ce7640
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158551"
---
# <a name="creating-stored-procedures"></a>Creación de procedimientos almacenados
  Todos los procedimientos almacenados deben asociarse a una clase de Common Language Runtime (CLR) o Modelo de objetos componentes (COM) para poder usarse. La clase debe estar instalada en el servidor - normalmente en forma de un [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® dinámicos (DLL): biblioteca de vínculos y registrado como un ensamblado en el servidor o en un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de datos.  
  
 Los procedimientos almacenados se registran en un servidor o en una base de datos. Se puede llamar a los procedimientos almacenados del servidor desde cualquier contexto de consulta. Solo se puede tener acceso a los procedimientos almacenados de base de datos si el contexto de base de datos es la base de datos bajo la cual se define el procedimiento almacenado. Si las funciones de un ensamblado llaman a las funciones en otro ensamblado, debe registrar ambos ensamblados en el mismo contexto (servidor o base de datos). Para un servidor o una implementada [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de datos en un servidor, puede usar [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para registrar un ensamblado. Para un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], puede usar el Diseñador de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para registrar un ensamblado en el proyecto.  
  
> [!IMPORTANT]  
>  Los ensamblados COM pueden suponer un riesgo para la seguridad. Debido a esto y a otras consideraciones, los ensamblados COM están en desuso en [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]. Es posible que este tipo de ensamblados no esté disponible en versiones futuras.  
  
## <a name="registering-a-server-assembly"></a>Registro de un ensamblado de servidor  
 En el Explorador de objetos de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], los ensamblados de servidor aparecen en la carpeta Ensamblados bajo una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Los ensamblados de servidor pueden contener ensamblados .NET (CLR) y bibliotecas COM.  
  
### <a name="to-create-a-server-assembly"></a>Para crear un ensamblado de servidor  
  
1.  Expanda la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el Explorador de objetos, haga clic en el **ensamblados** carpeta y, a continuación, haga clic en **nuevo ensamblado**. Esto muestra la **registrar ensamblado de servidor** cuadro de diálogo.  
  
2.  Para **tipo** especificar el tipo de ensamblado:  
  
    -   Para una DLL de código administrado (CLR), especifique Ensamblado .NET.  
  
    -   Para código nativo (COM) DLL, especifique DLL COM.  
  
3.  Para **nombre de archivo**, especifique el archivo DLL que contiene los procedimientos almacenados.  
  
4.  Para **nombre del ensamblado**, especifique un nombre para el ensamblado.  
  
5.  Si se trata de una compilación de depuración de la biblioteca que se va a usar para depurar procedimientos almacenados, seleccione el **incluir información de depuración** casilla de verificación. Para obtener más información sobre cómo depurar procedimientos almacenados, vea [depurar procedimientos almacenados](debugging-stored-procedures.md).  
  
6.  Puede hacer clic en **Aceptar** para registrar el ensamblado de inmediato o, en la barra de herramientas del cuadro de diálogo, puede hacer clic en un comando en el **Script** menú para generar el script de la acción de registro en una ventana de consulta, un archivo o el Portapapeles.  
  
 Después de registrar un ensamblado de servidor, puede configurarlo haciendo clic en el ensamblado en el Explorador de objetos y, a continuación, haga clic en **propiedades**.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Registrar un ensamblado de base de datos en el servidor  
 En el Explorador de objetos de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], los ensamblados de base de datos aparecen en la carpeta Ensamblados bajo una base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Los ensamblados de base de datos pueden contener ensamblados .NET (CLR) y bibliotecas COM.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>Para crear un ensamblado de base de datos en un servidor  
  
1.  Expanda la instancia de la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el Explorador de objetos de base de datos, haga clic en el **ensamblados** carpeta y, a continuación, haga clic en **nuevo ensamblado**. Esto muestra la **registrar ensamblado de base de datos** cuadro de diálogo.  
  
2.  Para **tipo** especificar el tipo de ensamblado:  
  
    -   Para una DLL de código administrado (CLR), especifique Ensamblado .NET.  
  
    -   Para una DLL de código nativo (COM), especifique DLL COM.  
  
3.  Para **nombre de archivo**, especifique el archivo DLL que contiene los procedimientos almacenados.  
  
4.  Para **nombre del ensamblado**, especifique un nombre para el ensamblado.  
  
5.  Si se trata de una compilación de depuración de la biblioteca que se va a usar para depurar procedimientos almacenados, seleccione el **incluir información de depuración** casilla de verificación. Para obtener más información sobre cómo depurar procedimientos almacenados, vea [depurar procedimientos almacenados](debugging-stored-procedures.md).  
  
6.  Puede hacer clic en **Aceptar** para registrar el ensamblado de inmediato o, en la barra de herramientas del cuadro de diálogo, puede hacer clic en un comando en el **Script** menú para generar el script de la acción de registro en una ventana de consulta, un archivo o el Portapapeles.  
  
 Después de registrar un ensamblado de la base de datos, puede configurarlo haciendo clic en el ensamblado en el Explorador de objetos y, a continuación, haga clic en **propiedades**.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Registrar un ensamblado de base de datos en un proyecto  
 En el Explorador de soluciones de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], los ensamblados de base de datos aparecen en la carpeta Ensamblados bajo un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Los ensamblados de base de datos pueden contener ensamblados .NET (CLR) y bibliotecas COM.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Para crear un ensamblado de base de datos en un proyecto de Analysis Service  
  
1.  Expanda la instancia de la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el Explorador de objetos de base de datos, haga clic en el **ensamblados** carpeta y, a continuación, haga clic en **nueva referencia de ensamblado**. Esto muestra la **Agregar referencia** cuadro de diálogo. El **.NET** pestaña de la **Agregar referencia** cuadro de diálogo enumera los ensamblados .NET (CLR) existentes, mientras que el **proyectos** ficha enumera los proyectos.  
  
2.  Puede hacer clic de un componente existente o un proyecto y, a continuación, haga clic en **agregar** para agregarlo a la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proyecto. Para agregar una referencia a un archivo DLL de COM, haga clic en el **examinar** ficha para buscar el archivo. El **proyectos y componentes seleccionados** lista muestra el nombre, tipo, versión y la ubicación de cada componente que se va a agregar al proyecto.  
  
3.  Cuando haya terminado de seleccionar los componentes para agregar, haga clic en **Aceptar** para agregarlos a la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proyecto.  
  
## <a name="script-format-for-an-assembly"></a>Formato de script para un ensamblado  
 Registrar un ensamblado .NET es bastante sencillo. Un ensamblado .NET se agrega a una base de datos en formato binario con el siguiente formato:  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración de los ensamblados de modelos multidimensionales](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definición de procedimientos almacenados](defining-stored-procedures.md)  
  
  
