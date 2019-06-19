---
title: Evaluación del estado del grupo de disponibilidad mediante directivas de grupo
description: Obtenga información sobre cómo ver las directivas del sistema de grupos que se usan en el panel Always On para proporcionar información sobre el estado del grupo de disponibilidad.
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
manager: jroth
ms.openlocfilehash: 2f8fb49b90a0da28a4961806c7ace46bcb10f5db
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789446"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>Evaluación del estado del grupo de disponibilidad Always On mediante directivas de grupo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  En el panel Always On se usan las directivas del sistema de grupos de disponibilidad Always On para proporcionar información sobre el mantenimiento del grupo de disponibilidad para el usuario. Son muy útiles para solucionar los problemas de funcionamiento iniciales de un grupo de disponibilidad. Estas directivas se pueden ampliar y usar para personalizar el panel Always On o se pueden ejecutar al instante para notificar la información de mantenimiento deseada.  
  
 Hay 14 directivas del sistema para los grupos de disponibilidad. Para obtener información sobre cada directiva, consulte [Directivas de Always On para problemas operativos - Grupos de disponibilidad Always On (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>Ver o evaluar las directivas de sistema de los grupos de disponibilidad  
 Para ver o ejecutar las directivas de sistema de los grupos de disponibilidad en SQL Server Management Studio (SSMS), haga lo siguiente:  
  
1.  En el **Explorador de objetos**, expanda **Administración**, **Administración de directivas**, **Directivas** y después **Directivas del sistema**.  
  
2.  Haga clic en una de las directivas y haga clic en **Evaluar**. Si quiere evaluar la directiva que ha seleccionado, ya ha terminado. Puede hacer clic en **Vista**, en el cuadro **Detalles del destino**, para ver los detalles de los resultados de evaluación.  
  
3.  Para consultar todas las directivas de sistema delos grupos de disponibilidad, en el panel **Seleccionar una página**, haga clic en **Selección de directiva**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [The Always On health model, part 2: Extending the health model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (El modelo de estado de Always On, parte 2: extensión del modelo de estado).   
  
  
