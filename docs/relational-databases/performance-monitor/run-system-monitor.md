---
title: Ejecutar Monitor de sistema | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: de2b4facacb6066763ff6673fd9dcb48ee81299d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787415"
---
# <a name="run-system-monitor"></a>Ejecutar Monitor de sistema
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  El Monitor del sistema utiliza llamadas a procedimiento remoto (RPC) para recopilar información de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cualquier usuario que disponga de permisos de Microsoft Windows para ejecutar el Monitor del sistema puede utilizarlo para supervisar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Cuando utilice el Monitor del sistema o el Monitor de rendimiento, no podrá conectarse a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecute en Windows 98.  
  
 Al igual que con todas las herramientas para la supervisión del rendimiento, es normal que se produzca una disminución del rendimiento al supervisar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]con el Monitor del sistema. La sobrecarga real en una instancia específica dependerá de la plataforma de hardware, el número de contadores y el intervalo de actualización seleccionado. No obstante, la integración del Monitor del sistema con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está diseñada para que la disminución del rendimiento sea la mínima.  
  
> [!NOTE]  
>  Si ha seleccionado los contadores de rendimiento de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la supervisión en el complemento Monitor del sistema, los contadores estarán presentes aunque no se ejecute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Para obtener información sobre cómo iniciar el Monitor del sistema, vea [Iniciar el Monitor de sistema &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  
