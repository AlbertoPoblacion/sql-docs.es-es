---
title: Propiedades de características de Analysis Services | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2ae8636ce7f7dc25a99fde8ade52ca58c7786395
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62509867"
---
# <a name="feature-properties"></a>Propiedades de características
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

  Las propiedades de características corresponden a las características del producto, la mayor parte de ellas avanzadas, incluidas las propiedades que controlan los vínculos entre las instancias de servidor.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] admite las propiedades de servidor enumeradas en la tabla siguiente. Para obtener más información sobre otras propiedades de servidor y cómo establecerlas, vea [Configurar las propiedades de servidor en Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Se aplica a:** Modo de servidor multidimensional únicamente  
  
## <a name="properties"></a>Propiedades  
  
|Property|Default|Descripción|  
|--------------|-------------|-----------------|  
|**ManagedCodeEnabled**|1|Una propiedad booleana que indica si los procedimientos de almacenamiento CLR están habilitados.|  
|**LinkInsideInstanceEnabled**|1|Una propiedad booleana que indica si se puede crear un objeto vinculado dentro de la misma instancia del servidor.|  
|**LinkToOtherInstanceEnabled**|0|Una propiedad booleana que indica si los objetos en servidores remotos se pueden vincular.|  
|**LinkFromOtherInstanceEnabled**|0|Una propiedad booleana que indica si los objetos se pueden vincular desde otras instancias del servidor.|  
|**ConnStringEncryptionEnabled**|1|Una propiedad booleana que indica si la cadena de conexión se cifra en el archivo de configuración del servidor.|  
|**UseCachedPageAllocators**|0|Una propiedad booleana que indica si los asignadores de páginas almacenados en caché están habilitados.|  
|**ComUdfEnabled**|0|Una propiedad booleana que indica si las funciones definidas por el usuario como objetos COM están habilitadas.|  
|**SQMSupportEnabled**|1|Una propiedad booleana que indica si se envían automáticamente informes de uso de características y de errores a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|  
|**ResourceMonitoringEnabled**|1|Una propiedad booleana que indica si los contadores de supervisión de recursos internos están habilitados. Esta propiedad está activada de forma predeterminada. Cuando se habilita, esta propiedad permite a los contadores recopilar datos de uso acerca de la actividad de la E/S, la memoria y la CPU.<br /><br /> Los contadores de supervisión de recursos internos se usan en las Vistas de administración dinámica (DVM) que informan de la utilización de los recursos. Si deshabilita esta propiedad, las consultas DMV siguen ejecutándose, pero el conjunto de resultados no será válido. Entre las consultas DMV que dependen de esta propiedad se incluyen las siguientes:<br /><br /> **Conjunto de filas DISCOVER_OBJECT_ACTIVITY**<br /><br /> **Conjunto de filas DISCOVER_COMMAND_OBJECTS**<br /><br /> **DISCOVER_SESSIONS** (para SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Nota: En un sistema de varios núcleos que usa la arquitectura NUMA, si se deshabilita esta propiedad, puede mejorar el rendimiento de las consultas, en particular para altas cargas de trabajo multi-usuario. Tendrá que ejecutar pruebas comparativas para determinar si el rendimiento de las consultas mejora al cambiar esta propiedad. Para obtener las prácticas recomendadas para realizar pruebas comparativas, como es borrar la memoria caché y evitar errores comunes, vea la [Guía de operaciones de SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>Vea también  
 [Configurar las propiedades de servidor en Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determinar el modo de servidor de una instancia de Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Usar vistas de administración dinámica &#40;DMV&#41; para supervisar Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
