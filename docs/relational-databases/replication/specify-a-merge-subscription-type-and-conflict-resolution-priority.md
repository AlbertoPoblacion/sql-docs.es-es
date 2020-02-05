---
title: Especificación del tipo y la prioridad de resolución de conflictos (combinación)
description: Obtenga información sobre cómo especificar el tipo y la directiva de resolución de conflictos usada por una suscripción de combinación para SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a988935a1d0a614f1b7b336cc95ed82ce2a36214
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "75321742"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Especificar un tipo de suscripción de mezcla y la prioridad de resolución de conflictos
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Especifique un tipo de suscripción de mezcla y la prioridad de resolución de conflictos en la página **Tipo de suscripción** del Asistente para nuevas suscripciones. Para obtener más información sobre cómo utilizar este asistente, vea [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) y [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 El tipo de suscripción no se puede modificar después de crear la suscripción, pero se puede modificar la prioridad del tipo de suscripción de servidor en el cuadro de diálogo **Propiedades de suscripción - \<Publicador>: \<baseDeDatosDePublicación>** . Para obtener más información acerca de cómo obtener acceso a este cuadro de diálogo, vea [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) y [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Para especificar un tipo de suscripción de mezcla y la prioridad de resolución de conflictos  
  
1.  En la página **Tipo de suscripción** del Asistente para nuevas suscripciones, seleccione **Cliente** o **Servidor** en la opción **Tipo de suscripción** .  
  
2.  Si selecciona el tipo de suscripción **Servidor**, escriba también un valor (de 0,00 a 99,99) en la opción **Prioridad para la resolución de conflictos** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Para modificar la prioridad de resolución de conflictos  
  
1.  En **Propiedades de suscripción - \<Publicador>: \<baseDeDatosDePublicación>** , en el publicador, escriba un valor (de 0,00 a 99,99) para la opción **Prioridad**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Detección y resolución de conflictos de replicación de mezcla avanzada](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Suscribirse a publicaciones](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
