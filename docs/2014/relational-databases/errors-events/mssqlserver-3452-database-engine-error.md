---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e811d36160cf0a4477452acec336c61bf52e793
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868072"
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|3452|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|REC_CHECKIDENTITY|  
|Texto del mensaje|En la recuperación de la base de datos '%.*ls' (%d) se detectó una posible incoherencia de valores de identidad en la tabla con id. %d. Ejecute DBCC CHECKIDENT ("%.\*ls").|  
  
## <a name="explanation"></a>Explicación  
Durante la actualización a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], el proceso de recuperación de los valores de identidad de la base de datos detectó una incoherencia en los metadatos.  
  
## <a name="user-action"></a>Acción del usuario  
Ejecute DBCC CHECKIDENT.  
  
