---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92bb186e7b9a790d39c5e2ed7df69e77cb618e5f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|360|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DML_UPDATE_SPARSE_AND_COLSET|  
|Texto del mensaje|La lista de columnas de destino de una instrucción INSERT, UPDATE o MERGE no puede contener una columna dispersa y el conjunto de columnas que la contiene. Escriba de nuevo la instrucción para incluir la columna dispersa o el conjunto de columnas, pero no ambos.|  
  
## <a name="explanation"></a>Explicación  
Un conjunto de columnas es una representación XML sin tipo que combina algunas columnas de una tabla en una salida estructurada. Se ha intentado modificar tanto el conjunto de columnas como una columna incluida en dicho conjunto, produciendo dos referencias a la misma columna.  
  
## <a name="user-action"></a>Acción del usuario  
Vuelva a escribir la instrucción para incluir referencias a la columna o al conjunto de columnas, pero no incluya ambos en la instrucción.  
  
