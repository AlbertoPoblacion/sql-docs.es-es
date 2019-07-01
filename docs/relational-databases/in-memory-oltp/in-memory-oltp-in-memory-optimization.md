---
title: OLTP en memoria (optimización en memoria) | Microsoft Docs
ms.custom: ''
ms.date: 06/24/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8ebb953132e28a3ea0766f7d9d7cd40f3f620659
ms.sourcegitcommit: 20d24654e056561fc33cadc25eca8b4e7f214b1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351664"
---
# <a name="in-memory-oltp-in-memory-optimization"></a>OLTP en memoria (optimización en memoria)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] puede mejorar considerablemente el rendimiento de escenarios de datos transitorios, carga de datos, ingesta de datos y procesamiento de transacciones.  Para saltar al código básico y al conocimiento que necesita para probar rápidamente su propia tabla optimizada para memoria y procedimiento almacenado con compilación nativa, consulte
 -  [Inicio rápido 1: Tecnologías de OLTP en memoria para acelerar el rendimiento de Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md).  
 
Un vídeo de 17 minutos que explica OLTP en memoria y muestra las ventajas de rendimiento:

-  [OLTP en memoria en SQL Server 2016](https://www.youtube.com/watch?v=l5l5eophmK4).

Para descargar la demostración de rendimiento de OLTP en memoria usada en el vídeo: 

- [Demostración de rendimiento de OLTP en memoria v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

Para información más detallada de OLTP en memoria y una revisión de los escenarios que ven beneficios de rendimiento gracias a la tecnología:

- [Información general y escenarios de uso](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)
 
 Cabe decir que [!INCLUDE[hek_2](../../includes/hek-2-md.md)] es la tecnología de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la que se mejora el rendimiento del procesamiento de transacciones. Para obtener más información sobre la tecnología de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la que se mejora el rendimiento de las consultas analíticas y de los informes, vea la [Guía de índices de almacén de columnas](../../relational-databases/indexes/columnstore-indexes-overview.md).
  
 Se han realizado varias mejoras de OLTP en memoria de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] y [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)], además de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. El área expuesta de Transact-SQL aumentó para facilitar la migración de aplicaciones de base de datos. Se agregó compatibilidad para realizar operaciones ALTER para tablas optimizadas para memoria y procedimientos almacenados con compilación nativa, con el fin de facilitar el mantenimiento de las aplicaciones.
  
> [!NOTE]  
>  **Pruébelo**  
>   
>  OLTP en memoria está disponible en las bases de datos Azure SQL en el nivel Premium y crítico para la empresa y en grupos elásticos. Para una introducción a OLTP en memoria y al Almacén de columnas en Azure SQL Database, consulte [Optimizar el rendimiento con las tecnologías In-Memory en SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  

## <a name="in-this-section"></a>En esta sección  
 Esta sección proporciona los temas siguientes:  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Inicio rápido 1: Tecnologías de OLTP en memoria para acelerar el rendimiento de Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)|Profundice en OLTP en memoria|
|[Información general y escenarios de uso](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)|Información general sobre OLTP en memoria y cuáles son los escenarios que verán beneficios en el rendimiento.|
|[Requisitos para usar tablas con optimización para memoria](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)|Describe los requisitos de hardware y software y las instrucciones para utilizar tablas optimizadas para memoria.|  
|[Ejemplos de código de OLTP en memoria](../../relational-databases/in-memory-oltp/in-memory-oltp-code-samples.md)|Contiene ejemplos de código en los que se muestra cómo crear y utilizar una tabla optimizada para memoria.|  
|[Memory-Optimized Tables](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Presenta las tablas optimizadas para memoria.|  
|[Variables de tabla con optimización para memoria](https://msdn.microsoft.com/library/bd102e95-53e2-4da6-9b8b-0e4f02d286d3)|Ejemplo de código que muestra cómo utilizar una variable de tabla optimizada para memoria en lugar de una variable de tabla tradicional para reducir el uso de tempdb.|  
|[Índices de las tablas con optimización para memoria](https://msdn.microsoft.com/library/86805eeb-6972-45d8-8369-16ededc535c7)|Presenta los índices optimizados para memoria.|  
|[Procedimientos almacenados compilados de forma nativa](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)|Presenta los procedimientos almacenados compilados de forma nativa.|  
|[Administrar memoria para OLTP en memoria](https://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)|Descripción y administración del uso de memoria en el sistema.|  
|[Crear y administrar el almacenamiento de objetos con optimización para memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)|Describe los archivos delta y de datos, que almacenan información sobre las transacciones en tablas optimizadas para memoria.|  
|[Hacer copia de seguridad, restaurar y recuperar tablas con optimización para memoria](https://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)|Describe las copias de seguridad, las restauraciones y las recuperaciones para tablas optimizadas para memoria.|  
|[Compatibilidad de Transact-SQL con OLTP en memoria](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)|Describe la compatibilidad de [!INCLUDE[tsql](../../includes/tsql-md.md)] para [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Compatibilidad con alta disponibilidad para bases de datos de OLTP en memoria](../../relational-databases/in-memory-oltp/high-availability-support-for-in-memory-oltp-databases.md)|Describe los grupos de disponibilidad y los clústeres de conmutación por error en [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Compatibilidad de SQL Server con OLTP en memoria](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)|Enumera la sintaxis nueva y la actualizada, y las características que admiten tablas optimizadas para memoria.|  
|[Migrar a OLTP en memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)|Describe cómo migrar las tablas basadas en disco a tablas optimizadas para memoria.|  
  
 Encontrará más información acerca de [!INCLUDE[hek_2](../../includes/hek-2-md.md)] en:  

- [Vídeo que explica OLTP en memoria y muestra las ventajas de rendimiento](https://www.youtube.com/watch?v=l5l5eophmK4).

- [Demostración de rendimiento de OLTP en memoria v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

-   [Notas del producto sobre características internas de OLTP en memoria de SQL Server](https://msdn.microsoft.com/library/mt764316.aspx)  

-   [Comparación de características de almacén de columnas y OLTP en memoria de SQL Server](https://download.microsoft.com/download/D/0/0/D0075580-6D72-403D-8B4D-C3BD88D58CE4/SQL_Server_2016_In_Memory_OLTP_and_Columnstore_Comparison_White_Paper.pdf)

-   Novedades de OLTP en memoria en SQL Server 2016, [parte 1](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/11/12/in-memory-oltp-whats-new-in-sql2016-ctp3/) y [parte 2](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/25/whats-new-for-in-memory-oltp-in-sql-server-2016-since-ctp3/)
  
-   [OLTP en memoria y los patrones de carga de trabajo comunes y consideraciones para la migración](https://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [Blog de OLTP en memoria](https://go.microsoft.com/fwlink/?LinkId=311696)  
  
## <a name="see-also"></a>Consulte también  
 [Características de la base de datos](../../relational-databases/database-features.md)  
  
  
