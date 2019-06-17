---
title: Cambiar la cuenta de Proxy para la recopilación de la utilidad se establece en una instancia administrada de SQL Server (utilidad de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: efa4af0c12379abaab2d810fd39ce6d7a3b0afef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62806329"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a>Cambiar la cuenta de proxy para el conjunto de recopilación de la utilidad en una instancia administrada de SQL Server (utilidad de SQL Server)
  En este tema se describe cómo cambiar la cuenta de proxy para el conjunto de recopilación de utilidades en una instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>Para cambiar la cuenta de proxy para el conjunto de recopilación de utilidades en una instancia administrada de SQL Server  
  
1.  Quite la instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   En **Explorador de la utilidad** de SSMS, haga clic en el nodo **Instancias administradas** .  
  
    -   En la vista de lista del **Explorador de la utilidad**, haga clic con el botón derecho en el nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y seleccione **Quitar instancia administrada...** . Para obtener más información, vea [Quitar una instancia de SQL Server de la Utilidad de SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Vuelva a inscribir la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   En el **Explorador de la utilidad** de SSMS, haga clic con el botón derecho en el nodo **Instancias administradas** y seleccione **Agregar instancia administrada...** .  
  
    -   Siga las indicaciones para completar el asistente y especifique la nueva cuenta de proxy.  
  
## <a name="see-also"></a>Vea también  
 [Características y tareas de la utilidad de SQL Server](sql-server-utility-features-and-tasks.md)   
 [Solucionar problemas de la Utilidad de SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
