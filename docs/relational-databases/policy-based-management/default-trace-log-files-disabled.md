---
title: Archivos de registro de seguimiento predeterminados deshabilitados | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1407f55e2edab15768fb10288b78dd59ff93ddd1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "67940499"
---
# <a name="default-trace-log-files-disabled"></a>Archivos de registro de seguimiento predeterminados deshabilitados
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Esta regla comprueba el valor de la opción de procedimiento almacenado sp_configure default trace enabled para determinar si el seguimiento predeterminado está establecido en ON (1) o en OFF (0). Cuando esta opción está habilitada, el seguimiento predeterminado proporciona información sobre la configuración y los cambios de DDL de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. En algunos casos, esta información puede ser útil para los clientes y el Servicio de atención al cliente y soporte técnico de [!INCLUDE[msCoName](../../includes/msconame-md.md)] al solucionar problemas con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Prácticas recomendadas  
 Utilice el procedimiento almacenado sp_configure para habilitar el seguimiento estableciendo el valor de default trace enabled en 1.  
  
## <a name="for-more-information"></a>Para obtener más información  
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar y aplicar las prácticas recomendadas usando la administración basada en directivas](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
