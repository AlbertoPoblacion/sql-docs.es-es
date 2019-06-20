---
title: 'Lección 1: Creación de Windows de cuentas para la replicación | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: a1457a6d407b2b20c28e93c0ed681ab1dc8109d4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721161"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Lección 1: Creación de Windows de cuentas para la replicación
  En esta lección creará cuentas de Windows para ejecutar agentes de replicación. Creará distintas cuentas de Windows en el servidor local para los siguientes agentes:  
  
|Agente|Location|Nombre de cuenta|  
|-----------|--------------|------------------|  
|Agente de instantáneas|publicador|\<*nombreDeEquipo*>\repl_snapshot|  
|Agente de registro del LOG|publicador|\<*nombreDeEquipo*>\repl_logreader|  
|Agente de distribución|Publicador y suscriptor|\<*nombreDeEquipo*>\repl_distribution|  
|Agente de mezcla|Publicador y suscriptor|\<*nombreDeEquipo*>\repl_merge|  
  
> [!NOTE]  
>  En los tutoriales de replicación, el publicador y el distribuidor comparten la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El publicador y el suscriptor pueden compartir la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aunque no es necesario. Si el publicador y el suscriptor comparten la misma instancia, no se requieren los pasos que se utilizan para crear las cuentas en el suscriptor.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Para crear cuentas locales de Windows para agentes de replicación en el publicador  
  
1.  En el publicador, vaya al Panel de control y abra **Administración de equipos** en **Herramientas administrativas** .  
  
2.  En **Herramientas del sistema**, expanda **Usuarios y grupos locales**.  
  
3.  Haga clic con el botón derecho en **Usuarios** y después haga clic en **Usuario nuevo**.  
  
4.  Escriba `repl_snapshot` en el **nombre de usuario** cuadro, proporcione la contraseña y otra información relevante y, a continuación, haga clic en **crear** para crear la cuenta repl_snapshot.  
  
5.  Repita el paso anterior para crear las cuentas repl_logreader, repl_distribution y repl_merge.  
  
6.  Haga clic en **Cerrar**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Para crear cuentas locales de Windows para agentes de replicación en el suscriptor  
  
1.  En el suscriptor, vaya al Panel de control y abra **Administración de equipos** en **Herramientas administrativas** .  
  
2.  En **Herramientas del sistema**, expanda **Usuarios y grupos locales**.  
  
3.  Haga clic con el botón derecho en **Usuarios** y después haga clic en **Usuario nuevo**.  
  
4.  Escriba `repl_distribution` en el **nombre de usuario** cuadro, proporcione la contraseña y otra información relevante y, a continuación, haga clic en **crear** para crear la cuenta repl_distribution.  
  
5.  Repita el paso anterior para crear la cuenta repl_merge.  
  
6.  Haga clic en **Cerrar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ha creado correctamente cuentas de Windows para agentes de replicación. A continuación, configurará la carpeta de instantáneas. Consulte [Lección 2: Preparación de la carpeta de instantáneas](lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre los agentes de replicación](agents/replication-agents-overview.md)  
  
  
