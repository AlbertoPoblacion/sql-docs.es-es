---
title: Acerca de SQL Server Analysis Services | Microsoft Docs
ms.date: 12/05/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: overview
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2cd892ad41beba2b5715b3a7186ae5e44bb7911
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63206359"
---
# <a name="about-sql-server-analysis-services"></a>Acerca de SQL Server Analysis Services

Analysis Services es un motor de datos analíticos que se usa en la toma de decisiones y el análisis de negocios. Proporciona modelos de datos semánticos de nivel empresarial para informes de negocios y aplicaciones cliente como Power BI, Excel, Reporting Services y otras herramientas de visualización de datos.

Un flujo de trabajo típico incluye la creación de un proyecto de modelo de datos tabular o multidimensional en Visual Studio, la implementación del modelo como una base de datos en una instancia del servidor, la configuración del procesamiento de datos periódico y la asignación de permisos para que los usuarios finales puedan acceder a los datos. Cuando esté listo, las aplicaciones cliente que admitan Analysis Services como origen de datos podrán acceder al modelo de datos semánticos.

Analysis Services está disponible en dos plataformas diferentes:

**Azure Analysis Services**: es compatible con los modelos tabulares en los niveles de compatibilidad 1200 y superiores. Se admiten DirectQuery, las particiones, la seguridad de nivel de fila, las relaciones bidireccionales y las traducciones. Para obtener más información, vea [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).

**SQL Server Analysis Services**: es compatible con los modelos tabulares en todos los niveles de compatibilidad, los modelos multidimensionales, la minería de datos y PowerPivot para SharePoint.

## <a name="documentation-by-area"></a>Documentación por área

En general, [documentación de Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/) se incluye con la documentación de Azure. Si le interesa que los modelos tabulares en la nube, es mejor empezar por ahí. Este artículo y la documentación de esta sección es principalmente para SQL Server Analysis Services. Sin embargo, al menos para los modelos tabulares, cómo crear e implementar sus proyectos de modelo tabular es igual, independientemente de la plataforma que está usando. Consulte las siguientes secciones para obtener más información:

- [Comparación de soluciones tabulares y multidimensionales](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)
- [Instalar SQL Server Analysis Services](../analysis-services/instances/install-windows/install-analysis-services.md)
- [Modelos tabulares](../analysis-services/tabular-models/tabular-models-ssas.md)
- [Modelos multidimensionales](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)
- [Minería de datos](../analysis-services/data-mining/data-mining-ssas.md)
- [Power Pivot para SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)
- [Tutoriales](../analysis-services/analysis-services-tutorials-ssas.md)
- [Administración del servidor](../analysis-services/instances/analysis-services-instance-management.md)
- [Documentación para desarrolladores](analysis-services-developer-documentation.md)
- [Referencia técnica](https://docs.microsoft.com/bi-reference/)

#### <a name="see-also"></a>Vea también

[Documentación de Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)
[documentación de SQL Server](../sql-server/sql-server-technical-documentation.md)
