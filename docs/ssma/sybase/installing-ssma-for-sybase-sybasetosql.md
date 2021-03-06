---
title: "Instalación de SSMA para SAP ASE (SybaseToSQL) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/29/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 508af2c209711c6063ee58243a29066323b641f8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Instalación de SSMA para SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) para SAP Adaptive Server Enterprise (ASE) consta de una aplicación de cliente que usa para realizar una migración de SAP ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o base de datos de SQL Azure. También contiene un módulo de extensión que admite la migración de datos y el uso de funciones del sistema ASE en las bases de datos migrados.  
  
Instale la aplicación cliente en el equipo desde el que va a realizar los pasos de migración. Instalar los archivos del módulo de extensión en el equipo que está ejecutando [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en que se hospedará las bases de datos migrados.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Actualización de SSMA para SAP ASE  
Si desea actualizar a una versión posterior de SSMA para SAP ASE, primero debe desinstalar el cliente y el paquete de extensión de servidor. A continuación, instale la versión más reciente.  
  
Si abre un proyecto desde una versión anterior de SSMA para SAP ASE, SSMA le pregunta si desea convertir el proyecto a la versión más reciente. Haga clic en **Sí** para trabajar con el proyecto en la versión más reciente de SSMA.  
  
## <a name="contents"></a>Contenido  
  
|Artículo|Description|  
|---------|---------------|  
|[Instalación de SSMA para SAP ASE cliente &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Proporciona información sobre e instrucciones para la instalación de SSMA para cliente de SAP ASE.|  
|[Instalar componentes SSMA de SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Proporciona información sobre e instrucciones para instalar el módulo de extensión en las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Eliminación de SSMA para componentes SAP ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Proporciona instrucciones para desinstalar al cliente de paquete de programa y la extensión.|  
  
## <a name="see-also"></a>Vea también  
[Migrar SAP ASE bases de datos a SQL Server: base de datos de SQL de Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
