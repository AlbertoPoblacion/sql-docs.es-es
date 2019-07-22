---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b89aab7a129aec5fcae840086b140f6975a8c99
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043509"
---
# <a name="mssqlserver3961"></a>MSSQLSERVER_3961
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|3961|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|XACT_METADATA_INVALID|  
|Texto del mensaje|Error de la transacción de aislamiento de instantánea en la base de datos '%. * ls' porque el objeto al que tuvo acceso la instrucción ha sido modificado por una instrucción DDL de otra transacción simultánea desde el inicio de esta transacción.  No se permite porque los metadatos no tienen control de versiones. Una actualización simultánea de los metadatos puede dar lugar a incoherencias si se combina con aislamiento de instantánea.|  
  
## <a name="explanation"></a>Explicación  
Este error se produce al consultar metadatos bajo aislamiento de instantánea y existe una instrucción DDL simultánea que actualiza los metadatos a los que se obtiene acceso bajo el aislamiento de instantánea. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no permite controlar las versiones de los metadatos. Por ello, existen restricciones en cuanto a las operaciones de DDL que se pueden realizar en una transacción explícita que se está ejecutando bajo el aislamiento de instantánea. Una transacción implícita, por definición, es una instrucción única que permite aplicar la semántica del aislamiento de instantánea, incluso con instrucciones de DDL. No se permiten las siguientes instrucciones DDL en el aislamiento de instantánea después de una instrucción BEGIN TRANSACTION: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME o cualquier instrucción de DDL de Common Language Runtime (CLR). Estas instrucciones se admiten si se está utilizando el aislamiento de instantánea dentro de transacciones implícitas. Una transacción implícita, por definición, es una instrucción única que permite aplicar la semántica del aislamiento de instantánea, incluso con instrucciones de DDL.  
  
## <a name="user-action"></a>Acción del usuario  
Antes de consultar los metadatos, cambie el nivel de aislamiento a un nivel que no sea de aislamiento como, por ejemplo, lectura confirmada.  
  
