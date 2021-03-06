---
title: "Detectar y solucionar conflictos de replicación de mezcla | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
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
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67147bca1980bb0ff8e53faf8ff51147ec4ab1de
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="advanced-merge-replication---resolve-merge-replication-conflicts"></a>Replicación de mezcla avanzada: resolver conflictos de replicación de mezcla
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cuando un publicador y un suscriptor se conectan y se produce la sincronización, el Agente de mezcla detecta si existen conflictos. Si se detectan conflictos, el Agente de mezcla utiliza un solucionador de conflictos para determinar qué datos se aceptarán y se propagarán a otros sitios.  
  
> [!NOTE]  
>  Aunque un suscriptor se sincronice con el publicador, suelen producirse conflictos entre las actualizaciones que se realizan en suscriptores diferentes, en vez de entre las actualizaciones que se realizan entre un suscriptor y el publicador.  
  
 La replicación de mezcla ofrece diversos métodos para detectar y solucionar conflictos. Para la mayoría de aplicaciones, el método predeterminado es el adecuado:  
  
-   Si se produce un conflicto entre un publicador y un suscriptor, el cambio del publicador se mantiene y el cambio en el suscriptor se descarta.  
  
-   Si se produce un conflicto entre dos suscriptores que utilizan suscripciones de cliente (el tipo predeterminado para las suscripciones de extracción), se mantiene el cambio del primer suscriptor que se sincronice con el publicador y se descarta el cambio del segundo suscriptor. Para obtener información sobre cómo especificar las suscripciones de cliente y servidor, consulte [Especificar un tipo de suscripción de mezcla y la prioridad de resolución de conflictos &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
-   Si se produce un conflicto entre dos suscriptores que utilizan suscripciones de servidor (el tipo predeterminado para las suscripciones de inserción), se mantiene el cambio del suscriptor con el valor de prioridad más alto y se descarta el cambio del segundo suscriptor. Si los valores de prioridad son iguales, se mantiene el cambio del primer suscriptor que se sincronice con el publicador.  
  
 Para obtener más información acerca de cómo detectar y solucionar conflictos en la replicación de mezcla, vea [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## <a name="see-also"></a>Ver también  
 [Opciones de artículo para la replicación de mezcla](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Suscribirse a publicaciones](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  
