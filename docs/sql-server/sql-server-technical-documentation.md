---
title: Documentación de SQL Server | Microsoft Docs
ms.date: 02/28/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: sql-non-specified
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.portal.f1
helpviewer_keywords:
- documentation [SQL Server], home page
- Help [SQL Server]
- SQL Server, documentation
- home page [SQL Server]
- Help [SQL Server], documentation home page
- Books Online [SQL Server], home page
- portal page [SQL Server]
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: ''
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 8868bbce17a31e72d55cbdca3e7badb00e66666e
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="sql-server-documentation"></a>Documentación de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server es una pieza fundamental de la plataforma de datos de Microsoft. SQL Server es líder del sector de sistemas de administración de bases de datos operativas (ODBMS). Esta documentación ayuda a instalar, configurar y usar SQL Server. El contenido incluye ejemplos descentralizados, ejemplos de código y vídeos. Para temas sobre el lenguaje de SQL Server, consulte [Referencia del lenguaje](../t-sql/language-reference.md).

|Novedades  | Notas de la versión  |
|---------|---------|
|[Novedades de SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)     | [Notas de la versión de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)        |
|[Novedades de SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)     | [Notas de la versión de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)        |
|[Novedades de SQL Server 2014](https://msdn.microsoft.com/library/bb500435(v=sql.120).aspx)     | [SQL Server 2014 Release Notes](../sql-server/sql-server-2014-release-notes.md)        |


**Probar SQL Server**
> [![Descargar desde el Centro de evaluación](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [Descargar SQL Server](http://go.microsoft.com/fwlink/?LinkID=829477)
>
> [![Descargar desde el Centro de evaluación](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [Descargar SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
>
> [![Descargar desde el Centro de evaluación](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [Descargar SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
>
> [![Creación de una máquina virtual](../includes/media/azure-vm.png)](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) [Obtener una máquina virtual con SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)

## <a name="sql-server-technologies"></a>Tecnologías de SQL Server


|||
|-|-|    
|![Motor de base de datos de SQL](../sql-server/media/sql-database-engine.png "Motor de base de datos de SQL")|**[Motor de base de datos](../database-engine/sql-server-database-engine-overview.md)**<br /><br /> El Motor de base de datos es el servicio principal para almacenar, procesar y proteger datos. El Motor de base de datos proporciona acceso controlado y procesamiento rápido de transacciones para cumplir los requisitos de las aplicaciones consumidoras de datos más exigentes de su empresa. El Motor de base de datos también proporciona una completa compatibilidad para mantener una gran disponibilidad.|
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] es una plataforma para generar soluciones de integración de datos de alto rendimiento, lo que incluye paquetes que proporcionan procesamiento de extracción, transformación y carga (ETL) para almacenamiento de datos.|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] es una plataforma y un conjunto de herramientas de datos analíticos para Business Intelligence en un entorno personal, de equipo o empresa. Los servidores y los diseñadores de cliente admiten soluciones OLAP tradicionales, nuevas soluciones de modelado tabular y análisis y colaboración de autoservicio mediante [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], Excel y un entorno de SharePoint Server. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] también incluye minería de datos para permitir descubrir las relaciones y los patrones ocultos en grandes volúmenes de datos.|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services ofrece funcionalidad empresarial de informes habilitados para web.  Puede crear informes que extraigan contenido a partir de diversos orígenes de datos, publicar informes con distintos formatos y administrar la seguridad y las suscripciones de forma centralizada.|
|![R Server](../sql-server/media/r-server.png "R Server")|**[Machine Learning Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> A través de los lenguajes populares R y Python, Microsoft Machine Learning Services integra el aprendizaje automático con los flujos de trabajo empresariales.<br /><br /> Machine Learning Services (en base de datos) integra R y Python con SQL Server, lo que simplifica la compilación, el reciclaje y los modelos de puntuación llamando a procedimientos almacenados.  Asimismo, proporciona una compatibilidad de escala empresarial con R y Python sin necesidad de utilizar SQL Server.|
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) proporciona una solución de limpieza de datos controlada por conocimiento. DQS permite generar una base de conocimiento y usarla para realizar tareas de corrección de datos y eliminación de datos duplicados, usando medios asistidos por ordenador e interactivos. Puede usar servicios de consulta de datos basados en la nube y puede generar una solución de administración de datos que integra DQS con SQL Server Integration Services y Master Data Services.|
|![Servicios de replicación](../sql-server/media/replication-services.png "Servicios de replicación")|**[Replicación](../relational-databases/replication/sql-server-replication.md)**<br /><br /> La replicación es un conjunto de tecnologías destinadas a la copia y distribución de datos y objetos de base de datos de una base de datos a otra, para luego sincronizar ambas bases de datos con el fin de mantener su coherencia. La replicación permite distribuir datos a diferentes ubicaciones y a usuarios remotos o móviles mediante redes de área local y de área extensa, conexiones de acceso telefónico, conexiones inalámbricas e Internet.|
|![Master Data Services](../sql-server/media/master-data-services.png)|**[Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] es la solución de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para la administración de datos maestros. Una solución basada en [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ayuda a asegurarse de que los informes y los análisis se basan en la información correcta. Con [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], se crea un repositorio central de los datos maestros y se mantiene un registro auditable y protegible de los mismos a medida que van cambiando con el tiempo.|

## <a name="migrate-and-move-data"></a>Migrar y mover los datos

- [Importar y exportar datos con el Asistente para importación y exportación de SQL Server](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)
- [Microsoft Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)
- [Migración de su base de datos SQL Server a Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

## <a name="earlier-sql-server-versions"></a>Versiones anteriores de SQL Server

- [Vínculos e información del Centro de actualizaciones de SQL Server sobre todas las versiones compatibles](https://msdn.microsoft.com/library/ff803383.aspx)
- [Documentación de SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
- [Documentación de SQL Server 2012](https://technet.microsoft.com/library/bb418433(v=sql.10).aspx)
- [Documentación de SQL Server 2008 R2](https://msdn.microsoft.com/library/hh278298(v=sql.10).aspx)
- [Documentación de SQL Server 2008](https://msdn.microsoft.com/library/hh994727(v=sql.10).aspx)
- [Documentación archivada de SQL Server 2005](https://msdn.microsoft.com/library/hh278313(v=sql.10).aspx)

## <a name="samples"></a>Ejemplos

- [Base de datos de ejemplo de Wide World Importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx)
- [Bases de datos de ejemplo y scripts de AdventureWorks para SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=49502) 
- [Ejemplos de SQL Server en GitHub](https://github.com/Microsoft/sql-server-samples)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]