---
title: "Configuración del publicador | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
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
f1_keywords:
- sql13.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8acc8b765decae1137c3fe79d0471b59e5a527f
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="publisher-settings"></a>Configuración del publicador
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El cuadro de diálogo **Configuración del publicador** permite cambiar la configuración de los publicadores que se han agregado al panel izquierdo del Monitor de replicación.  
  
## <a name="options"></a>.  
 **Conexión del publicador**  
 Haga clic para abrir el cuadro de diálogo **Conectar al servidor** , que permite ver y cambiar las propiedades de la conexión y las credenciales que utiliza el Monitor de replicación para conectarse a un publicador.  
  
 **Conexión del distribuidor**  
 Solo se muestra si el publicador utiliza un distribuidor remoto. Haga clic para abrir el cuadro de diálogo **Conectar al servidor** , que permite ver y cambiar las propiedades de la conexión y las credenciales que utiliza el Monitor de replicación para conectarse a un distribuidor remoto.  
  
 **Conectar automáticamente cuando se inicia el Monitor de replicación**  
 Active esta casilla para permitir que el Monitor de replicación se conecte automáticamente con el distribuidor y recupere información de estado para el publicador seleccionado en la cuadrícula de la parte superior del cuadro de diálogo. Si esta casilla está desactivada, debe conectarse manualmente después de iniciar el Monitor de replicación: haga clic con el botón secundario en el publicador en el panel izquierdo del Monitor de replicación y, a continuación, haga clic en **Conectar**.  
  
 **Actualizar automáticamente el estado de este publicador y sus publicaciones**  
 Active esta casilla para permitir que el Monitor de replicación actualice automáticamente el estado del publicador seleccionado en la cuadrícula de la parte superior del cuadro de diálogo. Si esta opción está activada, el Monitor de replicación sondea el distribuidor buscando información de estado en el publicador y sus publicaciones. El intervalo de sondeo se establece mediante la opción **Frecuencia de actualización** . Para obtener más información sobre la actualización en el Monitor de replicación, vea [Almacenamiento en caché, actualización y rendimiento del Monitor de replicación](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Frecuencia de actualización**  
 Escriba un valor (en segundos) para especificar la frecuencia con la que el Monitor de replicación debe sondear el distribuidor en búsqueda de información de estado. Los valores más bajos producen un sondeo más frecuente, lo que puede afectar al rendimiento del distribuidor si se supervisa un gran número de publicadores. Se recomienda probar el sistema para determinar un valor adecuado. El valor **Frecuencia de actualización** también se utiliza si se selecciona **Actualizar automáticamente** en cualquiera de las ventanas de detalle del Monitor de replicación.  
  
 **Mostrar estos publicadores en el siguiente grupo**  
 Seleccione un grupo de publicadores de la lista. El publicador se muestra en este grupo en el panel izquierdo. Los grupos proporcionan una forma de organizar los publicadores y no afectan al funcionamiento de la replicación.  
  
 **Nuevo grupo**  
 Haga clic aquí para crear un nuevo grupo de publicadores. Un grupo de publicadores proporciona una forma cómoda de organizar publicadores en el Monitor de replicación. Los grupos no afectan a la replicación de datos ni a la relación entre los servidores de una topología de replicación.  
  
## <a name="see-also"></a>Ver también  
 [Iniciar el Monitor de replicación](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Supervisar la replicación](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
