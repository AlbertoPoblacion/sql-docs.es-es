---
title: Motor de SQL Server Extended Events | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: extended-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
- xevents
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 505a35bf0fcc76a79af933b75d3a26ec2de0329f
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2018
---
# <a name="sql-server-extended-events-engine"></a>Motor de SQL Server Extended Events
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  El motor de Extended Events [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es una colección de servicios y objetos que:  
  
-   Habilita la definición de eventos.  
  
-   Habilita el procesamiento de los datos de eventos.  
  
-   Administra los objetos y servicios de Extended Events en el sistema.  
  
-   Mantiene una lista de las sesiones de Extended Events y administra el acceso a dicha lista.  
  
 El motor de Extended Events no proporciona eventos o acciones que se van a llevar a cabo cuando se activa un evento. Los procesos que utiliza el motor de Extended Events definen la interacción con el motor. Estos procesos agregan los puntos de evento y proporcionan las acciones que se van a llevar a cabo en respuesta a la activación de eventos.  
  
 La ilustración siguiente muestra una vista simplificada de una sesión de Extended Events. Para más información, consulte [SQL Server Extended Events Sessions](../../relational-databases/extended-events/sql-server-extended-events-sessions.md).  
  
 ![Arquitectura de eventos extendidos detallada](../../relational-databases/extended-events/media/xearchitecturedetailed.gif "Arquitectura de eventos extendidos detallada")  
  
 Observe lo siguiente:  
  
-   Cada proceso de Windows puede tener uno o más módulos (**proceso Win32**, **módulo Win32**). También se les conoce como módulos *binarios* o *ejecutables*.  
  
-   Cada uno de los módulos de los procesos de Windows puede contener uno o varios paquetes de eventos extendidos (**Paquete**), que contienen uno o más objetos de eventos extendidos (**Tipo**, **Destino**, **Acción**, **Asignación**, **Predicado**y **Evento**).  
  
-   Dentro de un proceso de host solo puede haber una instancia del motor de eventos extendidos (**motor de eventos extendidos**) que:  
  
    -   Administra algunos aspectos de la sesión (por ejemplo, enumerar las sesiones).  
  
    -   Administra el envío (**Distribuidor**). Es similar a un grupo de subprocesos.  
  
    -   Administra los búferes de la memoria (**Búfer**) para los eventos. Cuando se llenan los búferes, los búferes se envían a los destinos.  
  
-   Una vez que se crea una sesión y, opcionalmente, los eventos se enlazan a la sesión (**Contexto de la sesión**):  
  
    -   Las instancias de los destinos (**Instancia de destino**) también pueden crearse y agregarse a la sesión.  
  
    -   Cuando se llenan los búferes, dichos búferes se envían a los destinos.  
  
## <a name="see-also"></a>Ver también  
 [Eventos extendidos](../../relational-databases/extended-events/extended-events.md)  
  
  
