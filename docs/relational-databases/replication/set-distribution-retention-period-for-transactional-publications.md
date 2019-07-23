---
title: Establecer el período de retención de distribución para las publicaciones transaccionales | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e39be7010f24f33ae7f31217c7eba8c5b467654
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051711"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Establecer el período de retención de distribución para las publicaciones transaccionales
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Especifique el período mínimo y máximo de retención de distribución en el cuadro de diálogo **Propiedades de la base de datos de distribución - \<baseDeDatosDeDistribución>** . Está disponible en la página **General** del cuadro de diálogo **Propiedades del distribuidor - \<distribuidor>** . Para más información acerca de cómo obtener acceso a este cuadro de diálogo, [Ver y modificar las propiedades del distribuidor y del publicador](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Para especificar el período de retención de distribución  
  
1.  En la página **General** del cuadro de diálogo **Propiedades del distribuidor - \<distribuidor>** , haga clic en el botón de propiedades ( **...** ) de la base de datos de distribución.  
  
2.  Para especificar el período mínimo de retención de distribución, escriba un valor en el cuadro **Al menos** ; para especificar el período máximo de retención de distribución, escriba un valor en el cuadro **Pero no más de** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="see-also"></a>Consulte también  
 [Configurar distribución](../../relational-databases/replication/configure-distribution.md)   
 [Desactivación y expiración de la suscripción](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
