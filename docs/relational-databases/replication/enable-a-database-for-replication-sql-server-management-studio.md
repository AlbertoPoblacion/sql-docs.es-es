---
title: "Habilitar una base de datos para replicación (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6f729536b8f538c4b19ea76b7454b2899e2ffdfc
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Habilitar una base de datos para replicación (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Una base de datos se habilita de forma implícita para replicación cuando un miembro del rol fijo de servidor **sysadmin** crea una publicación con el Asistente para nueva publicación. Un miembro del rol fijo de servidor **sysadmin** también puede habilitar una base de datos para replicación de forma explícita, de manera que un miembro del rol fijo de base de datos **db_owner** pueda crear una o varias publicaciones en esa base de datos. Para habilitar una base de datos de forma explícita, utilice la página **Bases de datos de publicación** del cuadro de diálogo **Propiedades del publicador: \<Publicador>**. Para obtener más información sobre el acceso a este cuadro de diálogo, vea [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Para habilitar una base de datos para replicación  
  
1.  En la página **Bases de datos de publicación** del cuadro de diálogo **Propiedades del publicador: \<Publicador>**, active las casillas **Transaccional** y/o **Mezclar** para cada una de las bases de datos que desee replicar. Active la casilla **Transaccional** para habilitar la base de datos para replicación de instantáneas.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
