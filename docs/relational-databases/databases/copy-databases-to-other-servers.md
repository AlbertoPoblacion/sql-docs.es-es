---
title: Copia de bases de datos en otros servidores | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ab6019a97e97f916173aeed53586376a7e76f543
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="copy-databases-to-other-servers"></a>Copiar bases de datos en otros servidores
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En ocasiones, resulta útil copiar una base de datos de un equipo a otro para realizar pruebas, comprobar la coherencia, desarrollar software, ejecutar informes, crear una base de datos reflejada o, quizás, poner la base de datos a disposición de las actividades de oficinas remotas.  
  
 Hay varias maneras de copiar una base de datos:  
  
-   Usar el Asistente para copiar bases de datos  
  
     Puede usar el Asistente para copiar bases de datos con el fin de copiar o mover bases de datos entre los servidores o actualizar una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a una versión posterior. Para más información, consulte [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
-   Restaurar una copia de seguridad de una base de datos  
  
     Para copiar una base de datos completa, puede utilizar las instrucciones BACKUP y RESTORE de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Normalmente, la restauración de una copia de seguridad completa de una base de datos se utiliza para copiar la base de datos de un equipo a otro por varios motivos. Para obtener más información sobre el uso de copias de seguridad y restauración para copiar una base de datos, vea [Copiar bases de datos con Copias de seguridad y restauración](../../relational-databases/databases/copy-databases-with-backup-and-restore.md).  
  
    > [!NOTE]  
    >  Para configurar una base de datos reflejada para la creación de reflejo de la base de datos, debe restaurar la base de datos en el servidor reflejado mediante RESTORE DATABASE *<nombre_de_base_de_datos>* WITH NORECOVERY. Para obtener más información, vea [Preparar una base de datos reflejada para la creación de reflejo &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Utilizar el asistente Generar scripts para publicar bases de datos  
  
     Puede utilizar el asistente Generar scripts para transferir una base de datos de un equipo local a un proveedor de hospedaje web. Para obtener más información, vea [Asistente Generar y publicar scripts](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md).  
  
  
