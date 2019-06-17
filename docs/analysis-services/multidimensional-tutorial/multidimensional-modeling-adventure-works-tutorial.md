---
title: Multidimensional de modelado (Tutorial de Adventure Works) | Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98e995a89f9993a54736c4966639fd583e2391b6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403727"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a>Creación de modelos multidimensionales (tutorial de Adventure Works)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Este es el Tutorial de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. En este tutorial se describe cómo usar [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] para desarrollar e implementar un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , usando la empresa ficticia [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] para todos los ejemplos.  
  
## <a name="what-you-learn"></a>¿Qué aprenderá  
En este tutorial, aprenderá a:  
  
-   Definir orígenes de datos, vistas del origen de datos, dimensiones, atributos, relaciones de atributo, jerarquías y cubos en un proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
-   Ver los datos de dimensiones y cubos implementando el proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]y a procesar los objetos implementados para rellenarlos con datos del origen de datos subyacente.  
  
-   Modificar las medidas, las dimensiones, las jerarquías, los atributos y los grupos de medida del proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , así como a implementar cambios incrementales en el cubo implementado en el servidor de desarrollo.  
  
-   Definir cálculos, indicadores de claves de rendimiento (KPI), acciones, perspectivas, traducciones y roles de seguridad en un cubo.  
  
Este tutorial va acompañado de una descripción del escenario para poder entender mejor el contexto de estas lecciones. Para obtener más información, consulte [Escenario de Tutorial de Analysis Services](analysis-services-tutorial-scenario.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
Necesitará datos de ejemplo, archivos del proyecto de ejemplo y software para completar todas las lecciones de este tutorial. Para obtener instrucciones sobre cómo encontrar e instalar los requisitos previos para este tutorial, consulte [Instalar los datos y proyectos de ejemplo para el tutorial de modelado multidimensional de Analysis Services](install-sample-data-and-projects.md).  
  
Además, los permisos siguientes deben existir para realizar correctamente este tutorial:  
  
-   Debe ser miembro del grupo local Administradores del equipo con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o ser miembro del rol de administración del servidor de la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Deben tener permisos de lectura en el **AdventureWorksDW** base de datos de ejemplo. Esta base de datos de ejemplo es válida para la versión de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
## <a name="lessons"></a>Lecciones  
Este tutorial incluye las siguientes lecciones.  
  
|Lección|Tiempo estimado para completar la lección|  
|----------|------------------------------|  
|[Lección 1: Definir una vista del origen de datos dentro de un análisis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|15 minutos|  
|[Lección 2: Definir e implementar un cubo](lesson-2-defining-and-deploying-a-cube.md)|30 minutos|  
|[Lección 3: Modificar medidas, atributos y jerarquías](lesson-3-modifying-measures-attributes-and-hierarchies.md)|45 minutos|  
|[Lección 4: Definir propiedades de dimensión y atributos avanzados](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|120 minutos|  
|[Lección 5: Definir relaciones entre dimensiones y grupos de medida](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|45 minutos|  
|[Lección 6: Definir cálculos](lesson-6-defining-calculations.md)|45 minutos|  
|[Lección 7: Definir indicadores clave de rendimiento &#40;KPI&#41;](lesson-7-defining-key-performance-indicators-kpis.md)|30 minutos|  
|[Lección 8: Definir acciones](lesson-8-defining-actions.md)|30 minutos|  
|[Lección 9: Definir perspectivas y traducciones](lesson-9-defining-perspectives-and-translations.md)|30 minutos|  
|[Lección 10: Definir Roles administrativos](lesson-10-defining-administrative-roles.md)|15 minutos|  
  
> [!NOTE]  
> La base de datos de cubo que creará en este tutorial es una versión simplificada de la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] proyecto de modelos multidimensionales que forma parte de las bases de datos de ejemplo Adventure Works disponibles para su descarga en GitHub. La versión del tutorial de la base de datos multidimensional de Adventure Works se ha simplificado para centrarse en los conocimientos específicos que le interesará dominar inmediatamente. Después de completar el tutorial, considere la posibilidad de explorar el proyecto de modelo multidimensional por su cuenta para entender mejor el modelado multidimensional de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="next-step"></a>Paso siguiente  
Para comenzar el tutorial, vaya a la primera lección: [Lección 1: Definir una vista del origen de datos dentro de un análisis Services proyecto](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).  
  
  
  
