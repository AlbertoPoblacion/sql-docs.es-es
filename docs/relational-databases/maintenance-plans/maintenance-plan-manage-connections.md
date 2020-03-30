---
title: Plan de mantenimiento (Administrar conexiones) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a388792d24ce033dce0ffb4c6f0120a6ea341ae0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "68115961"
---
# <a name="maintenance-plan-manage-connections"></a>Plan de mantenimiento (Administrar conexiones)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilice el cuadro de diálogo **Administrar conexiones** para especificar las propiedades de las conexiones que utilizan los planes de mantenimiento. Cuando crea un plan de mantenimiento, se crea una conexión local al servidor donde se ha creado el plan. Utilice esta conexión para crear tareas que realicen trabajos en esta conexión local. Si es necesario, utilice el cuadro de diálogo **Administrar conexiones** para agregarlas. Cuando se configuran conexiones adicionales, éstas aparecen en el cuadro de conexiones de las tareas.  
  
## <a name="options"></a>Opciones  
 **Server**  
 Instancia del servidor.  
  
 **Autenticación**  
 Indica si la conexión se establece con autenticación de Windows o autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

> [!IMPORTANT]  
> El paquete está almacenado en la base de datos **msdb** con su **ProtectionLevel** establecido en **ServerStorage**, por lo que cuando se use la *autenticación de SQL Server*, la contraseña no se cifrará en **msdb**. Puede usar la *autenticación de SQL Server* mientras la base de datos **msdb** sea segura, aunque se recomienda usar la *autenticación de Windows*.

## <a name="see-also"></a>Consulte también  
 [Planes de mantenimiento](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
