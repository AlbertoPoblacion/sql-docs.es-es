---
title: Usar un reenviador DNS para resolver nombres DNS no sea de dispositivo (APS)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 123d8a83-b7fd-4dc9-90d4-fa01af2d629d
caps.latest.revision: "21"
ms.openlocfilehash: 6538ec32f141592b6cf21a325b74f3e451e73092
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names"></a>Usar un reenviador DNS para resolver nombres DNS no sea de dispositivo
Un reenviador DNS se puede configurar en los nodos de los servicios de dominio de Active Directory (***appliance_domain*-AD01** y  ***appliance_domain*-AD02**) de su dispositivo de sistema de la plataforma de análisis para permitir que las secuencias de comandos y las aplicaciones de software para tener acceso a servidores externos.  
  
## <a name="ResolveDNS"></a>Usar un reenviador DNS  
El dispositivo de sistema de la plataforma de análisis está configurado para impedir la resolución de nombres DNS de los servidores que no están en el dispositivo. Algunos procesos, como Windows Software Update Services (WSUS), necesitará acceso a los servidores fuera de la aplicación. Para admitir este escenario de uso del sistema de plataforma de análisis de DNS puede configurarse para admitir un reenviador de nombre externo que le permitirá hosts de sistema de la plataforma de análisis y máquinas virtuales (VM) para usar servidores DNS externos para resolver nombres fuera de la aplicación. No se admite la configuración personalizada de sufijos DNS, lo que significa que debe usar nombres de dominio completo para resolver un nombre de servidor no sea de dispositivo.  
  
**Para crear un reenviador DNS con la GUI de DNS**  
  
1.  Inicie sesión en el  ***appliance_domain*-AD01** nodo.  
  
2.  Abra el Administrador de DNS (**dnsmgmt.msc**).  
  
3.  Haga clic en el nombre del servidor y, a continuación, haga clic en **propiedades**.  
  
4.  En el **avanzadas** ficha, anule la selección de la **Deshabilitar recursividad (deshabilitar también los reenviadores)** opción y, a continuación, haga clic en **aplicar**.)  
  
5.  Haga clic en el **reenviadores** ficha y, a continuación, haga clic en **editar**.  
  
6.  Escriba la dirección IP para el servidor DNS externo que proporcionará la resolución de nombres. Las máquinas virtuales y servidores (hosts) en el dispositivo se conectarán a servidores externos mediante el uso de nombres de dominio completo.  
  
7.  Repita los pasos 1 a 6 en el  ***appliance_domain*-AD02** nodo  
  
**Para crear un reenviador DNS mediante Windows PowerShell**  
  
1.  Inicie sesión en el  ***appliance_domain*-AD01**nodo.  
  
2.  Ejecute el siguiente script de Windows PowerShell desde la  ***appliance_domain*-AD01** nodo. Antes de ejecutar el script de Windows PowerShell, reemplazan las direcciones IP con las direcciones IP de los servidores DNS.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Ejecutar el mismo comando en el  ***appliance_domain*-AD02** nodo.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Configurar la resolución de DNS para WSUS  
PDW de SQL Server 2012 proporciona funcionalidad de la aplicación de revisiones y mantenimiento integrada. PDW de SQL Server usa Microsoft Update y otra tecnologías de servicio de Microsoft. Para habilitar las actualizaciones, el dispositivo debe ser capaz o conectarse a un repositorio WSUS corporativo o en el repositorio WSUS público de Microsoft.  
  
Para los clientes que optar por configurar el dispositivo para buscar actualizaciones en el repositorio WSUS público de Microsoft, las siguientes instrucciones establezca los detalles de la configuración apropiada en el dispositivo.  
  
> [!NOTE]  
> El Administrador de red de cliente debe proporcionar la dirección IP para un servidor DNS corporativo que pueda resolver nombres en **Microsoft.com**.  
  
1.  Utilizar Escritorio remoto, inicie sesión en VM de VMM (<fabric domain>- VMM) con la cuenta de administrador de dominio de tejido.  
  
2.  Abra el Panel de Control, haga clic en **red e Internet**y, a continuación, haga clic en **centro de redes y recursos compartidos**.  
  
3.  En la lista de conexiones, haga clic en **VMSEthernet**y, a continuación, haga clic en **propiedades**.  
  
4.  Seleccione **protocolo de Internet versión 4 (TCP/IPv4)**y, a continuación, haga clic en **propiedades**.  
  
5.  En el **servidor DNS alternativo** , agregue la dirección IP proporcionada por el Administrador de red de cliente.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
