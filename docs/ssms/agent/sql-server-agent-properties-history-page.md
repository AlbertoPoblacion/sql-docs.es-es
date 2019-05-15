---
title: Propiedades de Agente SQL Server (página Historial) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 30426daee4c801ae0e8e338a88020434acda602d
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089623"
---
# <a name="sql-server-agent-properties-history-page"></a>Propiedades de Agente SQL Server (página Historial)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Utilice esta página para ver y modificar los valores de configuración para administrar el registro del historial de servicios del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
**Limitar tamaño del registro de historial de trabajos**  
Establece los límites para la cantidad de información del historial de trabajos que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserva en el registro.  
  
**Tamaño máximo del registro de historial de trabajos (filas)**  
Establece el número máximo de filas que conserva el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cuando el registro crece para contener este número de filas, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elimina las filas más antiguas del registro a medida que se van incluyendo filas nuevas.  
  
**Máximo de filas de historial de trabajos por trabajo**  
Establece el número máximo de filas que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserva por trabajo. Cuando el historial para un trabajo determinado crece para contener este número de filas, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quita las filas más antiguas del registro a medida que se van incluyendo filas nuevas.  
  
**Quitar historial del agente**  
Especifica que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quitará las entradas que han permanecido en el registro más tiempo que el especificado. Es una ejecución única para quitar el historial. Si es necesaria la repetición de un trabajo, cree y programe un plan de mantenimiento con un trabajo de limpieza.  
  
**Anterior a**  
Establece el tiempo que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conservará las entradas.  
  
## <a name="see-also"></a>Consulte también  
[Registro de errores del Agente SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
