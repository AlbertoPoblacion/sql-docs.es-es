---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8efc64cc421506aab080b0bf4aaefd0ad1c29de4
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550940"
---
# <a name="mssqlserver_844"></a>MSSQLSERVER_844
    
## <a name="details"></a>Detalles  
  
|Atributo|Value|  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|844|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|BUFLATCH_TIMEOUT_CONTINUE|  
|Texto del mensaje|Tiempo de espera agotado mientras se esperaba el bloqueo temporal del búfer -- tipo %d, bp %p, página %d:%d, stat %#x, id. de base de datos: %d, id. de unidad de asignación: %I64d%ls, tarea 0x%p : %d, tiempo de espera %d, marcas 0x%I64x, tarea propietaria 0x%p.  Esperando.|  
  
## <a name="explanation"></a>Explicación  
 Un proceso está esperando para adquirir un bloqueo temporal. Este problema puede estar causado por una operación de E/S que está tardando mucho en llevarse a cabo. Normalmente, este tipo de error es el resultado de que otras tareas estén bloqueando los procesos del sistema. En algunos casos, este error puede ser el resultado de un error de hardware.  
  
## <a name="user-action"></a>Acción del usuario  
 Para evitar que ocurra este error, intente lo siguiente:  
  
-   Reduzca la carga de trabajo.  
  
-   Busque errores de E/S asociados en el registro de errores o el registro de eventos. Normalmente, los errores de E/S indican un funcionamiento incorrecto del disco.  
  
-   Compruebe el registro de errores para ver si hay tareas que no rinden y otros errores críticos.  
  
-   Si se producen frecuentemente errores críticos, como aserciones, solucione estos problemas.  
  
 Si el error persiste, póngase en contacto con el servicio de Soporte técnico y Atención al cliente de Microsoft.  
  
  
