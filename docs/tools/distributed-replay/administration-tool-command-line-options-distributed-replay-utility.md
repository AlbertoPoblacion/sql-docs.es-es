---
title: "Opciones de línea de comandos (utilidad Distributed Replay) de la herramienta de administración | Documentos de Microsoft"
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
caps.latest.revision: "35"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac0fe5fe3686e60ef16d95899c69ecd72742e850
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Opciones de línea de comandos de la herramienta de administración (utilidad Distributed Replay)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]El [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herramienta de administración de Distributed Replay, **DReplay.exe**, es una herramienta de línea de comandos para comunicarse con el controlador de reproducción distribuida. Utilice la herramienta de administración para iniciar, supervisar y cancelar operaciones en el controlador.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "icono de vínculo de tema") para obtener más información sobre las convenciones de sintaxis que se usan con la sintaxis de la herramienta de administración, consulte [convenciones de sintaxis de Transact-SQL & #40; Transact-SQL & #41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>Comentarios  
 Puede emitir las siguientes opciones de línea de comandos con **DReplay.exe**:  
  
 **preprocess**  
 Inicia la fase de preprocesamiento. El controlador prepara la información de seguimiento de entrada, que se capturó en el entorno de producción, para la reproducción en el servidor de destino.  
  
 **reproducir**  
 Inicia la fase de reproducción de eventos. El controlador envía los datos de la reproducción a los clientes especificados, inicia la reproducción distribuida y sincroniza los clientes. Opcionalmente, cada cliente que se ha seleccionado registra la actividad de reproducción y guarda los archivos de seguimiento del resultado localmente.  
  
 **status**  
 Consulta el controlador y muestra el estado actual.  
  
 **cancel**  
 Cancela la operación que se está ejecutando actualmente en el controlador.  
  
 Para obtener información de la sintaxis detallada que incluye los argumentos de comando y ejemplos, vea los siguientes temas:  
  
-   [Preprocesar opción & #40; herramienta de administración de Distributed Replay & #41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Opción Replay & #40; herramienta de administración de Distributed Replay & #41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [Opción Status & #40; herramienta de administración de Distributed Replay & #41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [Opción Cancel & #40; herramienta de administración de Distributed Replay & #41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 Las RPC se reproducen como RPC y no como eventos de lenguaje.  
  
## <a name="permissions"></a>Permisos  
 Debe ejecutar la herramienta de administración como un usuario interactivo, como un usuario local o una cuenta de usuario de dominio. Para utilizar una cuenta de usuario local, la herramienta de administración y el controlador se deben estar ejecutando en el mismo equipo.  
  
 Para más información, consulte [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Vea también  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
