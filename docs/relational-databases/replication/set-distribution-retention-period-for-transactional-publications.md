---
title: Definición del período de retención de distribución
description: Establezca el período de retención de los datos de la base de datos de distribución en SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: d699eb502d99818926e92ff07a8fc16248aeee3d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287212"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Establecer el período de retención de distribución para las publicaciones transaccionales
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Especifique el período mínimo y máximo de retención de distribución en el cuadro de diálogo **Propiedades de la base de datos de distribución - \<baseDeDatosDeDistribución>** . Está disponible en la página **General** del cuadro de diálogo **Propiedades del distribuidor - \<distribuidor>** . Para más información acerca de cómo obtener acceso a este cuadro de diálogo, [Ver y modificar las propiedades del distribuidor y del publicador](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Para especificar el período de retención de distribución  
  
1.  En la página **General** del cuadro de diálogo **Propiedades del distribuidor - \<distribuidor>** , haga clic en el botón de propiedades ( **...** ) de la base de datos de distribución.  
  
2.  Para especificar el período mínimo de retención de distribución, escriba un valor en el cuadro **Al menos** ; para especificar el período máximo de retención de distribución, escriba un valor en el cuadro **Pero no más de** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="see-also"></a>Consulte también  
 [Configurar distribución](../../relational-databases/replication/configure-distribution.md)   
 [Desactivación y expiración de la suscripción](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
