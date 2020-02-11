---
title: Scripting y PowerShell con Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1cbb7d07835b63509ecd854788ce21e382141728
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099639"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Secuencias de comandos y PowerShell con Reporting Services
  
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] admite una amplia gama de escenarios de desarrollo y administración a través de script, incluida la utilidad de línea de comandos rs.exe, cmdlets de PowerShell para servidores de informes de modo de SharePoint y aprovechando el [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] modelo de objetos de PowerShell para los modos nativo y SharePoint.  
  
-   Los administradores pueden escribir un script [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] en para automatizar el modo en que implementan y administran una instalación del servidor de informes. Los administradores también pueden generar y ejecutar scripts de [!INCLUDE[tsql](../../includes/tsql-md.md)] que crean, configurar y actualizan una base de datos del servidor de informes. Los administradores también pueden usar las características de script de reproducción y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] registro en para automatizar las tareas de mantenimiento rutinarias.  
  
-   Los programadores pueden crear aplicaciones personalizadas que incluyen el script. Puede ejecutar un script que realiza llamadas al servicio web del servidor de informes. Casi cualquier operación que puede escribir en código administrado también se puede escribir en script.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]admite [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] el script de .net como el lenguaje de script que puede ser procesado por la utilidad RS. exe, un host de script que se ejecuta en el servidor de informes.  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Ejemplos y cmdlets de PowerShell del modo SharePoint de Reporting Services  
 ![Contenido relacionado con PowerShell](../media/rs-powershellicon.jpg "Contenido relacionado con PowerShell")  
  
 
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] El modo SharePoint incluye [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlets para la administración del servidor de informes.  
  
-   [Cmdlets de PowerShell para el modo de SharePoint de Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Incluye los ejemplos siguientes:  
  
    -   Crear una aplicación de servicio y un proxy  
  
    -   Revisar y actualizar una extensión de entrega  
  
    -   Obtener y establecer propiedades de la base de datos de la aplicación Reporting Services; por ejemplo, el tiempo de espera de la base de datos  
  
    -   Extensiones de datos de lista  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Ejemplos de Powershell y modelo de objetos de Reporting Services  
 ![Contenido relacionado con PowerShell](../media/rs-powershellicon.jpg "Contenido relacionado con PowerShell")  
  
 PowerShell realiza la llamada al núcleo del modelo de objetos y para la mayor parte válida para los modos SharePoint y nativo; por ejemplo, el trabajo de migración, el trabajo de suscripción y más ejemplos relacionados para las suscripciones funcionan en SQL15.  
  
-   [Use PowerShell para cambiar y enumerar Reporting Services propietarios de suscripciones y ejecutar una suscripción](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
-   [Use PowerShell para crear una máquina virtual de Azure con un servidor de informes en modo nativo](https://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   Vea la sección "Obtener acceso a las clases WMI mediante PowerShell" en [Obtener acceso al proveedor WMI de Reporting Services](access-the-reporting-services-wmi-provider.md).  
  
-   [Cómo administrar SSRS con PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/). Scripten  
  
## <a name="rsexe-scripting-samples"></a>Ejemplos de secuencias de comandos de RS.exe  
  
-   [Ejemplo Reporting Services script RS. exe para migrar contenido entre servidores de informes](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Consulte [Muestras de producto de SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889)para obtener más ejemplos de secuencias de comandos, aplicaciones y extensiones.  
  
## <a name="see-also"></a>Consulte también  
 [Utilidad RS. exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [Crear script de tareas administrativas y de implementación](script-deployment-and-administrative-tasks.md)   
 [Script con la utilidad rs.exe y el servicio Web](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  
