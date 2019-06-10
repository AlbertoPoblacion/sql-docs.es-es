---
title: Actualizar ensamblados de SQLCLR después de actualizar .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
author: lrtoyou1223
ms.author: lle
manager: jroth
ms.openlocfilehash: de109d4b02d203c6b3bbac5f1ee7d7ccb5cd8753
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776272"
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a>Actualizar ensamblados de SQLCLR después de actualizar .NET Framework

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) es una colección de rutinas de Common Language Runtime de SQL (SQLCR) que hacen referencia a los ensamblados de Microsoft .NET Framework 4. Al instalar actualizaciones de .NET Framework en el equipo que afecten al ensamblado de .NET Framework al que hacen referencia, se producirá un cambio en el identificador de versión de módulos (MVID) del ensamblado en la memoria caché de ensamblados global (GAC). Esto produce una incoherencia entre los MVID del ensamblado al que se hace referencia en la GAC y el ensamblado de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si la actualización de .NET Framework requiere reiniciar el equipo [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , los ensamblados SQLCLR afectados se actualizan automáticamente para corregir el problema de discrepancia de MVID en el reinicio del equipo [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Sin embargo, para las actualizaciones de .NET Framework que no necesitan reiniciar el equipo con [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , se produce un error debido a una discrepancia en los MVID de los ensamblados al intentar conectarse a un [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] mediante un [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]:  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe -upgradedlls.  
```  
  
 Para corregir este problema, deben actualizarse los ensamblados SQLCLR afectados en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Puede hacerlo ejecutando el archivo DQSInstaller.exe con el parámetro de línea de comandos **upgradedlls** para omitir la reconstrucción de las bases de datos de DQS y actualizar solo los ensamblados afectados. Esto garantiza que se conserven las bases de conocimiento, los proyectos de calidad de datos y otros datos de DQS.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Debe haber iniciado sesión como miembro del grupo Administradores en el equipo con [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   La cuenta de usuario de Windows debe ser miembro del rol fijo de servidor sysadmin en la instancia de SQL Server donde está instalado [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
### <a name="to-upgrade-sqlclr-assemblies"></a>Para actualizar ensamblados de SQLCLR  
  
1.  Inicie el símbolo del sistema.  
  
2.  En el símbolo del sistema, cambie el directorio a la ubicación donde DQSInstaller.exe esté disponible. Si instaló la instancia predeterminada de SQL Server, el archivo DQSInstaller.exe estará disponible en C:\Archivos de programa\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  En el símbolo del sistema, escriba el siguiente comando y presione ENTRAR:  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  Todos los demás pasos son los mismos que los pasos 2 a 6 de la sección [Ejecutar DQSInstaller.exe desde la pantalla Inicio, el menú Inicio o el Explorador de Windows](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) de [Ejecutar DQSInstaller.exe para completar la instalación del servidor de calidad de datos](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
## <a name="see-also"></a>Vea también  
 [Instalar Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Actualizar el esquema de las bases de datos DQS tras instalar la actualización de SQL Server](../../data-quality-services/install-windows/upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
