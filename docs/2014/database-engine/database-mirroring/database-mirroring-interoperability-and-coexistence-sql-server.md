---
title: 'Creación de reflejo de la base de datos: interoperabilidad y coexistencia (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 85b1f5eccc96e4ba1685a6e8d2ec8a5c428e2c8c
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934316"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>Creación de reflejo de la base de datos: interoperabilidad y coexistencia (SQL Server)
  La creación de reflejo de la base de datos se puede utilizar con las siguientes características o componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [Instancias de clúster de conmutación por error de AlwaysOn (clústeres de conmutación por error de SQL Server)](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [Captura de datos modificados (y seguimiento de cambios)](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [Instantáneas de base de datos](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [Catálogos de texto completo](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [Trasvase de registros](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [Replicación](database-mirroring-and-replication-sql-server.md)  
  
 La creación de reflejo de la base de datos no interopera con lo siguiente:  
  
-   Transacciones entre bases de datos y transacciones distribuidas  
  
     Si quiere saber por qué no se admiten estas transacciones, vea [Transacciones entre bases de datos no compatibles para la creación de reflejo de la base de datos o grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Creación de reflejo de la base de datos &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
