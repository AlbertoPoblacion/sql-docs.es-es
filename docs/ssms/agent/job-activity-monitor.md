---
title: Monitor de actividad de trabajo | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.jobactivitymonitor.alljobs.f1
- SQL13.SWB.ACTIVITYMON.F1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c928b0ea88d129e5ccbb7bf514d43e4d99ae327f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="job-activity-monitor"></a>Monitor de actividad de trabajo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Use esta página para ver la actividad actual de los trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Haga clic en **Filtro** para limitar el número de trabajos mostrados. La cuadrícula **Actividad de trabajo del agente** es de solo lectura. Haga clic en los encabezados de columna para ordenar la cuadrícula. Si desea modificar un trabajo, haga doble clic en el trabajo para abrir el cuadro de diálogo **Propiedades del trabajo** . Haga clic con el botón secundario en un trabajo de la cuadrícula para que comiencen a ejecutarse todos los pasos del trabajo, para iniciar un paso del trabajo determinado, deshabilitar o habilitar el trabajo, actualizarlo, eliminarlo, ver su historial o ver sus propiedades. Haga clic en **Actualizar** para actualizar la cuadrícula con información actual.  
  
## <a name="options"></a>.  
**Nombre**  
Nombre del trabajo.  
  
**Enabled**  
Indica si el trabajo está habilitado (**sí**) o no (**no**).  
  
**Estado***  
Estado actual del trabajo.  
  
**Resultado de la última ejecución**  
Estado del trabajo cuando se ejecutó por última vez.  
  
**Última ejecución**  
Fecha y hora en que se ejecutó el trabajo por última vez con la fecha y hora locales del servidor.  
  
**Siguiente ejecución***  
Fecha y hora en que se ha programado la próxima ejecución del trabajo con la fecha y hora locales del servidor.  
  
**Categoría**  
Categoría asignada al trabajo.  
  
**Ejecutable**  
**Sí** si el trabajo puede ejecutarse; **No** si el trabajo no puede ejecutarse. No puede ejecutarse un trabajo que no disponga de pasos o de un servidor de destino.  
  
**Programado**  
**Sí** si se ha asignado el trabajo a una programación de trabajo; **No** si el trabajo no tiene ninguna programación.  
  
*Solo los miembros con el rol fijo de servidor sysadmin de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] y el grupo de administradores del servidor puede ser los valores de esta columna. Los miembros del rol SQLAgentOperatorRole no pueden ver los valores en esta columna.  
  
#### <a name="to-open-the-job-activity-monitor"></a>Para abrir el Monitor de actividad de trabajo  
  
-   En el **Explorador de objetos**, expanda su servidor, expanda **Agente SQL Server**, haga clic con el botón derecho en **Monitor de actividad de trabajo**y, luego, haga clic en **Ver actividad de trabajo**.  
  
## <a name="see-also"></a>Ver también  
[Actividad de trabajos de monitor](../../ssms/agent/monitor-job-activity.md)  
  
