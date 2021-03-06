---
title: "Definición de filtros | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
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
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4baa09c02936eb9e67bbcbcbf2b69d70253a4111
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="define-filters"></a>Definir filtros
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El cuadro de diálogo **Definir filtros** permite definir filtros que posteriormente se aplican a conflictos de datos para obtener un subconjunto de conflictos en la cuadrícula. Para definir un filtro, elija un operador del cuadro de lista desplegable **Operador** y, a continuación, especifique un valor. Por ejemplo, si desea mostrar solamente los conflictos en los que el perdedor del conflicto es el servidor **ReplTest1**, seleccione **Igual a** en el cuadro de lista desplegable **Operador** y especifique **ReplTest1** en la primera columna **Valor** .  
  
## <a name="options"></a>.  
 **Operador**  
 Seleccione un operador para el filtro, como por ejemplo **Menor o igual que**.  
  
 **Value**  
 Escriba un valor para el filtro. La mayoría de los operadores solo requiere un valor en la primera columna **Valor** ; sin embargo, los operadores **Entre** y **No entre** requieren un valor en las dos columnas **Valor** .  
  
 **Desactivar**  
 Haga clic en este botón para borrar todos los filtros previamente definidos.  
  
## <a name="see-also"></a>Ver también  
 [Visor de conflictos de replicación de Microsoft &#40;Replicación de mezcla&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Visor de conflictos de replicación de Microsoft &#40;Replicación transaccional&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
