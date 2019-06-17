---
title: Servicio Servidor de informes de Windows (MSSQLServer) 107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7751fdc3e04f25b80b4f95dfc26abb8a0844a92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66099297"
---
# <a name="report-server-windows-service-mssqlserver-107"></a>Servicio Servidor de informes de Windows (MSSQLServer) 107
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|107|  
|Origen del evento|Servicio Servidor de informes de Windows|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texto del mensaje|El servicio Servidor de informes de Windows (MSSQLSERVER) no se puede conectar a la base de datos del servidor de informes.|  
  
## <a name="explanation"></a>Explicación  
 El servicio del Servidor de informes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no puede establecer conexión con la base de datos del servidor de informes. Este error se produce durante una reiniciación del servicio si no se puede establecer una conexión con la base de datos del servidor de informes. Entre las condiciones en que se produce este error se incluyen las siguientes:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] no se está ejecutando cuando se inicia el servicio del Servidor de informes.  
  
-   La conexión con el servicio de [!INCLUDE[ssDE](../../includes/ssde-md.md)] sufre un error porque no están habilitadas las conexiones remotas o el protocolo TCP/IP.  
  
-   La base de datos del servidor de informes no está configurada correctamente.  
  
-   La cuenta del servicio no está configurada correctamente o dicha cuenta ya no tiene permisos para la base de datos del servidor de informes. Esto puede producirse si no se utiliza la herramienta de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para configurar la cuenta o la base de datos del servidor de informes.  
  
## <a name="user-action"></a>Acción del usuario  
 Inicie el servicio de [!INCLUDE[ssDE](../../includes/ssde-md.md)] si no se está ejecutando y compruebe que las conexiones remotas están habilitadas para el protocolo TCP/IP.  
  
 Use la herramienta de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para configurar la cuenta del servicio y la base de datos del servidor de informes.  
  
## <a name="internal-only"></a>Solo para uso interno  
  
## <a name="see-also"></a>Vea también  
 [Configurar la cuenta de servicio del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Iniciar y detener el servicio del servidor de informes](../report-server/start-and-stop-the-report-server-service.md)  
  
  
