---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b3bc344e3e23ce965a2057628e4662ebe41508d2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990930"
---
# <a name="localdberrorinstanceexistswithlowerversion"></a>LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|258|  
|Origen del evento|SQL Server Local Database Runtime 12.0|  
|Componente|API de Local Database Runtime|  
|Texto del mensaje|No se puede crear la instancia de Local Database con la versión especificada. Ya existe una instancia con el mismo nombre, pero tiene una versión anterior a la versión especificada.|  
  
## <a name="explanation"></a>Explicación  
 La instancia especificada ya existe pero la versión es anterior a la solicitada.  
  
## <a name="user-action"></a>Acción del usuario  
 Elimine la instancia existente e intente de nuevo la operación.  
  
  
