---
title: Proyectos (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 17b95a12462178a887431defa8c465fd4dca1edd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102882"
---
# <a name="projects-sql-server-management-studio"></a>Proyectos (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Un proyecto de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] es una colección de scripts y archivos relacionados lógicamente que se pueden guardar juntos para la administración y el desarrollo de bases de datos.  
  
## <a name="script-project-overview"></a>Información general del proyecto de script  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aparecen en el Explorador de soluciones de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Un proyecto de script puede contener cero o varios archivos de proyecto. Puede agregar un proyecto a una solución o combinar más de un proyecto en una solución.  
  
Entre los proyectos se pueden incluir los siguientes:  
  
-   **Conexiones**. Una conexión, conservada en un proyecto, contendrá información lógica, el nombre del servidor, la base de datos predeterminada, el protocolo preferido, el tipo de autenticación y las propiedades de conexión. La información de conexión puede almacenarse opcionalmente con un script (vea a continuación).  
  
-   **SQLScripts**. Scripts SQL usados frecuentemente por el usuario. Si hace doble clic en un archivo .sql del proyecto, el Editor SQL abrirá el script seleccionado.  
  
-   **Scripts MDX, DMX y XMLA**. Scripts MDX usados frecuentemente por el usuario. Si hace doble clic en un archivo .mdx del proyecto, el Editor abrirá el script seleccionado.  
  
-   **Varios**. Esta carpeta se puede usar para los archivos que no encajan en ninguno de los otros tipos de nodos predeterminados, como un archivo de texto que contenga los objetivos del proyecto.  
  
Los proyectos también pueden estar integrados en un sistema de control de código fuente.  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a>Conectar a una instancia de SQL Server desde un proyecto de script  
Un proyecto de script puede contener conexiones a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede conectar a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un proyecto si hace clic en la conexión. Así se abrirá una ventana de script SQL conectada a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definida en la conexión seleccionada. Si abre un script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o MDX con una conexión que use autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , se le solicitará la contraseña mediante el cuadro de diálogo **Conectar con el servidor SQL Server** una vez que el editor se haya abierto y el script se haya cargado.  
  
La conexión se cerrará una vez que se cierre la ventana correspondiente.  
  
Para modificar información sobre una conexión, use la ventana de propiedades de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="project-tasks"></a>Tareas de proyecto  
  
|Descripción de la tarea|Tema|  
|--------------------|---------|  
|Describe cómo crear un nuevo proyecto en una solución.|[Crear un proyecto](../../ssms/solution/create-a-project.md)|  
|Describe cómo agregar un proyecto existente a una solución.|[Agregar un proyecto existente a una solución](../../ssms/solution/add-an-existing-project-to-a-solution.md)|  
|Describe cómo cambiar la ubicación predeterminada donde se guardan los archivos de proyecto.|[Cambiar la ubicación predeterminada de los proyectos](../../ssms/solution/change-the-default-location-for-projects.md)|  
|Describe cómo ver las propiedades actuales de un proyecto.|[Ver las propiedades de un proyecto](../../ssms/solution/view-project-properties.md)|  
|Describe cómo agregar nuevos elementos, como conexiones o archivos de script, un proyecto.|[Agregar nuevos elementos a un proyecto](../../ssms/solution/add-new-items-to-a-project.md)|  
|Describe cómo establecer la información de conexión para una consulta.|[Asociar una consulta a una conexión de un proyecto](../../ssms/solution/associate-a-query-with-a-connection-in-a-project.md)|  
|Describe cómo cambiar la información de conexión para una consulta.|[Cambiar la conexión asociada a una consulta](../../ssms/solution/change-the-connection-associated-with-a-query.md)|  
|Describe cómo cambiar las propiedades de conexión.|[Ver o cambiar las propiedades de una conexión en un proyecto](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a>Consulte también  
[Explorador de soluciones](../../ssms/solution/solution-explorer.md)  
[Soluciones &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Control de código fuente del Explorador de soluciones](https://msdn.microsoft.com/library/ms173879.aspx)  
  
