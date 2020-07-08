---
title: Aislamiento de problemas de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a7b73900dc88ba6e0f5af7dd71f781b5816bda67
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715217"
---
# <a name="isolate-performance-problems"></a>Aislar problemas de rendimiento
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Suele ser más efectivo usar conjuntamente varias herramientas de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Microsoft Windows para aislar los problemas de rendimiento de una base de datos que usar solo una herramienta cada vez. Por ejemplo, la característica Plan de ejecución gráfico, denominada también plan de presentación, le ayuda a reconocer los interbloqueos en una sola consulta. Sin embargo, puede reconocer más fácilmente otros problemas de rendimiento si utiliza conjuntamente las características de supervisión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y Windows.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] puede usarse para supervisar y solucionar problemas de Transact-SQL o problemas relacionados con las aplicaciones. Asimismo, puede utilizar el Monitor de sistema para supervisar problemas relativos al hardware y otros problemas relacionados con el sistema.  
  
 Puede supervisar las siguientes áreas para solucionar problemas:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o lotes de instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] enviadas por aplicaciones de usuarios.  
  
-   Actividad de los usuarios, como bloqueos o interbloqueos.  
  
-   Actividad del hardware, como el uso de los discos.  
  
 Algunos problemas posibles son:  
  
-   Errores de programación de aplicaciones debidos a instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] escritas incorrectamente.  
  
-   Errores de hardware, como los relativos a discos o a la red.  
  
-   Bloqueo excesivo debido a un diseño incorrecto de la base de datos.  
  
## <a name="tools-for-common-performance-problems"></a>Herramientas para solucionar problemas comunes de rendimiento  
 Igual de importante es la correcta selección del problema de rendimiento que desea que cada herramienta supervise u optimice. La herramienta y la utilidad dependen del tipo de problema de rendimiento que desee resolver.  
  
 En los temas siguientes se describen diversas herramientas de supervisión y optimización y los problemas que ayudan a solucionar.  
  
 [Identificar los cuellos de botella](../../relational-databases/performance/identify-bottlenecks.md)  
  
 [Supervisar el uso de la memoria](../../relational-databases/performance-monitor/monitor-memory-usage.md)  
  
  
