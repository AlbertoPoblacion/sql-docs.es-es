---
title: Opción Status (herramienta de administración de Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 42e06144f35ab2db8f124dddff74fb836b6d9c4c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150353"
---
# <a name="status-option-distributed-replay-administration-tool"></a>Opción Status (herramienta de administración de Distributed Replay)
  El [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herramienta de administración de Distributed Replay, `DReplay.exe`, es una herramienta de línea de comandos que puede usar para comunicarse con distributed replay controller. En este tema se describe la opción del símbolo del sistema **status** y la sintaxis correspondiente.  
  
 La opción **status** consulta el controlador y muestra el estado actual.  
  
 ![Icono de vínculo de tema](../../database-engine/media/topic-link.gif "Icono de vínculo de tema") Para obtener más información sobre las convenciones de sintaxis que se usan con la sintaxis de la herramienta de administración, vea [Convenciones de sintaxis de Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dreplay status [-mcontroller] [-fstatus_interval]  
```  
  
#### <a name="parameters"></a>Parámetros  
 **-m** *controller*  
 Especifica el nombre del equipo que se va a controlar. Puede utilizar "`localhost`" o "`.`" para hacer referencia al equipo local.  
  
 Si no se especifica el parámetro **-m** , se usará el equipo local.  
  
 **-f** *status_interval*  
 Especifica la frecuencia (en segundos) con la que se muestra el estado.  
  
 Si no se especifica el parámetro **-f** , el intervalo predeterminado es de 30 segundos.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente, se muestra el estado actual cada 60 segundos. El valor `localhost` indica que el servicio del controlador se está ejecutando en el mismo equipo que la herramienta de administración.  
  
```  
dreplay status -m localhost -f 60  
```  
  
## <a name="permissions"></a>Permisos  
 Debe ejecutar la herramienta de administración como un usuario interactivo, como un usuario local o una cuenta de usuario de dominio. Para utilizar una cuenta de usuario local, la herramienta de administración y el controlador se deben estar ejecutando en el mismo equipo.  
  
 Para más información, consulte [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Vea también  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)   
 [Depurador de Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
