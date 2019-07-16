---
title: Requisitos de aplicaciones web (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 02/13/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
keywords:
- master data services
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 763695a4fe00b2bb5f50113b5c9c2ba65ddd9417
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944885"
---
# <a name="web-application-requirements-master-data-services"></a>Requisitos de la aplicación web (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] es una aplicación web hospedada por Internet Information Services (IIS). [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] funciona únicamente en Internet Explorer (IE) 9 o posterior. No se admiten IE 8 ni versiones anteriores, así como tampoco Microsoft Edge ni Chrome.  

**Para obtener instrucciones sobre cómo instalar y configurar IIS**, vea [Instalación y configuración de IIS](../../master-data-services/master-data-services-installation-and-configuration.md#InstallIIS).
  
 Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] para crear y configurar la aplicación web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] configura IIS en el equipo local, de modo que es lo mejor para las tareas iniciales de configuración web. Por ejemplo, configure un entorno de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] con una aplicación web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] única, o bien configure la primera aplicación web en una implementación escalada de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Utilice las herramientas de IIS para realizar tareas más complejas, como configurar varios servidores web en una implementación escalada.  
  
> [!NOTE]  
>  Cualquier equipo en el que instale los componentes de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] debe tener las licencias pertinentes. Para obtener más información, consulte el Contrato de licencia para el usuario final (CLUF).  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="operating-system"></a>Sistema operativo  
 Antes de instalar [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], revise los siguientes requisitos:    
    
-   [Requisitos de hardware y software para instalar SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)    
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 Para trabajar en la aplicación web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , Silverlight 5 debe estar instalado en el equipo cliente. Si no tiene la versión necesaria de Silverlight, se le pedirá que la instale cuando navegue a un área de la aplicación web que la necesite. Puede instalar Silverlight 5 desde [aquí](https://go.microsoft.com/fwlink/?LinkId=243096).  
  
### <a name="role-and-role-services"></a>Rol y servicios del rol  
 En Windows Server 2012 o Windows Server 2012 R2, puede usar el **Administrador del servidor**, que está disponible en Microsoft Management Console (MMC), para instalar el rol **Servidor web (IIS)** y los servicios de rol necesarios.  
 
 
> [!IMPORTANT]  
>La**compresión de contenido dinámico** está habilitada de forma predeterminada. Esto disminuye considerablemente el tamaño de la respuesta xml y reduce la E/S de red, aunque el uso de CPU aumenta.  Para obtener más información, vea **[CTP 2.0] Rendimiento mejorado** en [Novedades en Master Data Services &#40;MDS&#41;](../../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
||  
|-|  
|Internet Information Services<br /><br /> Herramientas de administración web<br /><br /> Consola de administración de IIS<br /><br /> Servicios de World Wide Web<br /><br /> Desarrollo de aplicaciones<br /><br /> Extensibilidad de .NET<br /><br /> Extensibilidad de .NET 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> Extensiones ISAPI<br /><br /> Filtros ISAPI<br /><br /> Características HTTP comunes<br /><br /> Documento predeterminado<br /><br /> Examen de directorios<br /><br /> Errores HTTP<br /><br /> Contenido estático<br /><br /> [Nota: No instale publicación en WebDAV]<br /><br /> Estado y diagnóstico<br /><br /> Registrar HTTP<br /><br /> Monitor de solicitudes<br /><br /> Rendimiento<br /><br /> Compresión de contenido estático<br /><br /> Seguridad<br /><br /> Filtro de solicitudes<br /><br /> Autenticación de Windows|  
  
### <a name="features"></a>Características 
 En Windows Server 2012 y Windows Server 2012 R2, puede usar **Administrador del servidor** para instalar las siguientes características necesarias.  
  
||  
|-|  
|.NET Framework 3.5 (incluye .NET 2.0 y 3.0)<br /><br /> Servicios avanzados de .NET Framework 4.5<br /><br /> ASP.NET 4.5<br /><br /> WCF Services<br /><br /> Activación HTTP [Nota: Esto es necesario.]<br /><br /> Uso compartido de puertos TCP<br /><br /> Servicio WAS (Windows Process Activation Service)<br /><br /> Modelo de proceso<br /><br /> Entorno .NET<br /><br /> API de configuración<br/><br/>compresión de contenido dinámico|  
  
 Este es un script de PowerShell de ejemplo que sirve para agregar características y roles de servidor necesarios. Las características y roles de servidor necesarios varían en función del entorno.  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature -Restart  
```  
  
 Para obtener más información sobre el comando de PowerShell, vea [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature).  
  
### <a name="accounts-and-permissions"></a>Cuentas y permisos  
  
|Type|Descripción|  
|----------|-----------------|  
|Cuenta de Windows|Debe iniciar sesión en el equipo servidor web con una cuenta de Windows que tenga permiso para configurar roles de Windows, servicios de rol y características, y para crear y administrar grupos de aplicaciones, sitios web y aplicaciones web en IIS, en el equipo local.|  
|Cuenta de servicio|Cuando cree la aplicación web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] en [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], debe especificar una identidad para el grupo de aplicaciones en el que se ejecute la aplicación. Esta cuenta puede ser diferente de la cuenta de servicio que se especificó cuando se creó la base de datos de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .<br /><br /> Esta identidad debe ser una cuenta de usuario de dominio y se agrega al rol de la base de datos mds_exec en la base de datos de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] para tener acceso a las bases de datos. Para más información, vea [Inicios de sesión, usuarios y roles en bases de datos &#40;Master Data Services&#41;](../../master-data-services/database-logins-users-and-roles-master-data-services.md). Esta cuenta también se agrega a un grupo de Windows [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , **MDS_ServiceAccounts**, que es el permiso concedido al directorio de compilación temporal, **MDSTempDir**, en el sistema de archivos. Para obtener más información, vea [Permisos de carpetas y archivos&#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md).|  
  
## <a name="see-also"></a>Vea también  
 [Instalar Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
      
 [Crear una aplicación web de Master Data Manager &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [Página Configuración web &#40;Administrador de configuración de Master Data Services&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  
