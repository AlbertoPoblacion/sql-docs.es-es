---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 015a01f849bb00dd0db4c2f060447d63a2f96bc6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914077"
---
# <a name="mssqlserver41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|41030|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|OPEN_CLUSTER_SUB_KEY|  
|Texto del mensaje|No se pudo abrir la subclave del Registro '%.*ls' de clústeres de conmutación por error de Windows Server (WSFC) (código de error %d).  La clave principal del clúster es la clave raíz del clúster.  Puede que el servicio WSFC no se esté ejecutando o no esté accesible en su estado actual, o que los argumentos especificados no sean válidos. Si el grupo de disponibilidad correspondiente se ha quitado, este error es previsible. Para obtener más información sobre este código de error, vea "Códigos de error del sistema” en la documentación de Desarrollo en Windows.|  
  
## <a name="explanation"></a>Explicación  
 Si se destruye un clúster de WSFC, quita todas las claves del Registro relacionadas con [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
## <a name="user-action"></a>Acción del usuario  
 Después de volver crear un clúster de WSFC, deshabilite y vuelva a habilitar AlwaysOn en todos los nodos del clúster en los que haya una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] habilitada para AlwaysOn. Puede usar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para realizar esta tarea.  
  
## <a name="see-also"></a>Vea también  
 [Habilitar y deshabilitar grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [Clústeres de conmutación por error de Windows Server &#40;WSFC&#41; con SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
