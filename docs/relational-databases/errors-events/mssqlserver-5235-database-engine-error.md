---
title: MSSQLSERVER_5235 | Microsoft Docs
ms.custom: 
ms.date: 09/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b786414c1fdd53d21148ff7b682f0b030362afe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5235"></a>MSSQLSERVER_5235
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|5235|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION|  
|Texto del mensaje|[EMERGENCY] DBCC DBCC_COMMAND_DETAILS ejecutado por USER_NAME finalizó de forma anómala debido a un estado de error ERROR_STATE. Tiempo transcurrido: HOURS horas MINUTES minutos SECONDS segundos.|  
  
## <a name="explanation"></a>Explicación  
Este es el mensaje de resumen que DBCC imprime en el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cuando se produce una finalización inesperada mientras se ejecuta el comando. El estado de error notificado en el mensaje define el tipo de finalización inesperada.  
  
En la siguiente tabla se muestran y se definen los estados de error.  
  
|Estado de error|Definición|  
|---------------|--------------|  
|State 1|La instrucción finalizó debido a un daño grave de los metadatos. Este mensaje va acompañado de una o varias instancias de error 8930.|  
|State 2|La instrucción finalizó debido a un error interno de comprobación. Este mensaje va acompañado de una o varias instancias de error 8967.|  
|State 3|Error en las comprobaciones básicas de las tablas del sistema del motor de almacenamiento principal. Este mensaje va acompañado de una o varias instancias de error [7984](../../relational-databases/errors-events/mssqlserver-7984-database-engine-error.md), 7985, [7986](~/relational-databases/errors-events/mssqlserver-7986-database-engine-error.md), [7987](~/relational-databases/errors-events/mssqlserver-7987-database-engine-error.md) o [7988](~/relational-databases/errors-events/mssqlserver-7988-database-engine-error.md).|  
|State 4|Error en la reparación del modo de emergencia DBCC debido a que la base de datos no pudo iniciarse después de volver a generar el registro de transacciones. Este mensaje va acompañado del error 7909.|  
|Estado 5|Se produjo un error de aserción o infracción de acceso durante la ejecución del comando.|  
|Estado 6|Se produjo un error desconocido que canceló inesperadamente el comando DBCC.|  
|Estado 7|Una finalización anormal debido al error en la réplica (AlwaysOn).|  
  
## <a name="user-action"></a>Acción del usuario  
En la siguiente tabla se muestra la acción apropiada que debe llevar a cabo el usuario para el estado de error especificado.  
  
|Estado de error|Acción del usuario|  
|---------------|---------------|  
|State 1|Restaure mediante la copia de seguridad.|  
|State 2|Póngase en contacto con el Servicio de atención al cliente y soporte técnico (CSS) de [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|State 3|Restaure mediante la copia de seguridad.|  
|State 4|Restaure mediante la copia de seguridad.|  
|State 4|Póngase en contacto con el CSS.|  
|Estado 6|Vuelva a ejecutar el comando. Si el problema persiste, póngase en contacto con el CSS.|  
  
## <a name="see-also"></a>Vea también  
[DBCC &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-transact-sql.md)  
  
