---
title: Usar SQL Server Profiler para supervisar Analysis Services | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 190ae82b43f7a4f311d358ea9597a10cd5cc39dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181211"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Usar SQL Server Profiler para supervisar Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] realiza un seguimiento de los eventos de procesos del motor, como el inicio de un lote o una transacción, y captura datos sobre estos eventos, lo que permite supervisar la actividad del servidor y de la base de datos (por ejemplo, consultas del usuario o actividad de inicio de sesión). Puede capturar datos del [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] en un archivo o una tabla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para su análisis posterior y también reproducir los eventos capturados en la misma instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o en otra, para ver qué sucedió exactamente. Puede reproducir eventos en tiempo real o paso a paso. También resulta útil ejecutar los eventos de seguimiento junto con los contadores de Rendimiento en el mismo equipo. El analizador puede correlacionar los dos basándose en el tiempo y mostrarlos juntos en una misma línea temporal. Los eventos de seguimiento proporcionan más detalles, mientras que los contadores de Rendimiento ofrecen una vista agregada. Para obtener información sobre cómo crear y ejecutar seguimientos, vea [Crear seguimientos del generador de perfiles para su reproducción &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md).  
  
 En la tabla siguiente se describen los temas de esta sección.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Introducción a Supervisar Analysis Services con SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Describe cómo utilizar el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para supervisar una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Crear seguimientos del generador de perfiles para su reproducción &#40;Analysis Services&#41;](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)|Describe los requisitos para crear un seguimiento para la reproducción mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Eventos de seguimiento de Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|Describe las clases de evento de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Estas clases de evento se asignan a las acciones generadas por [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y se utilizan para las reproducciones de seguimientos.|  
  

  
  
