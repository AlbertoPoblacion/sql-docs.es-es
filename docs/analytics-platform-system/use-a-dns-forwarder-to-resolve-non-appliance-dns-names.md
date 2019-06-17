---
title: Usar un reenviador DNS en Analytics Platform System | Microsoft Docs"
description: Usar un reenviador DNS para resolver los nombres DNS que no sea de dispositivo en Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6ce978d7b05382b1a02018f3d5022b0f8bfaf585
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63243792"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Usar un reenviador DNS para resolver nombres DNS que no sea de dispositivo de Analytics Platform System
Se puede configurar un reenviador DNS en los nodos de Active Directory Domain Services ( **_dispositivo\_dominio_-AD01** y  **_dispositivo\_ dominio_-AD02**) de la aplicación Analytics Platform System para permitir que los scripts y aplicaciones de software para tener acceso a servidores externos.  
  
## <a name="ResolveDNS"></a>Usar un reenviador DNS  
La aplicación Analytics Platform System está configurada para evitar la resolución de nombres DNS de los servidores que no están en el dispositivo. Algunos procesos, como Windows Software Update Services (WSUS), deberá tener acceso a servidores fuera de la aplicación. Para admitir este escenario de uso el sistema de plataforma de análisis de DNS puede configurarse para admitir un reenviador de nombre externo que permitirá a los hosts de Analytics Platform System y máquinas virtuales (VM) usar servidores DNS externos para resolver nombres fuera de la aplicación. No se admite la configuración personalizada de sufijos DNS, lo que significa que debe usar nombres de dominio completo para resolver un nombre de servidor que no sea de dispositivo.  
  
**Para crear un reenviador DNS con la GUI de DNS**  
  
1.  Inicie sesión en el  **_dispositivo\_dominio_-AD01** nodo.  
  
2.  Abra el Administrador de DNS (**dnsmgmt.msc**).  
  
3.  Haga clic en el nombre del servidor y, a continuación, haga clic en **propiedades**.  
  
4.  En el **avanzadas** pestaña, anule la selección del **Deshabilitar recursividad (deshabilitar también los reenviadores)** opción y, a continuación, haga clic en **aplicar**.)  
  
5.  Haga clic en el **reenviadores** pestaña y, a continuación, haga clic en **editar**.  
  
6.  Escriba la dirección IP para el servidor DNS externo que proporcionará la resolución de nombres. Las máquinas virtuales y servidores (hosts) en el dispositivo se conectarán a servidores externos mediante el uso de nombres de dominio completo.  
  
7.  Repita los pasos del 1 al 6 en el  **_dispositivo\_dominio_-AD02** nodo  
  
**Para crear un reenviador DNS mediante Windows PowerShell**  
  
1.  Inicie sesión en el  **_dispositivo\_dominio_-AD01**nodo.  
  
2.  Ejecute el siguiente script de Windows PowerShell desde la  **_dispositivo\_dominio_-AD01** nodo. Antes de ejecutar el script de Windows PowerShell, reemplace las direcciones IP con las direcciones IP de los servidores DNS que no sea de dispositivo.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Ejecutar el mismo comando en el  **_dispositivo\_dominio_-AD02** nodo.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Configuración de la resolución DNS para WSUS  
PDW de SQL Server 2012 proporciona el servicio y las revisiones funcionalidad integrada. PDW de SQL Server usa Microsoft Update y otra tecnologías de mantenimiento de Microsoft. Para habilitar las actualizaciones, el dispositivo debe ser capaz de conectarse a un repositorio WSUS corporativo o en el repositorio público de WSUS de Microsoft.  
  
Para clientes que optar por configurar el dispositivo para buscar actualizaciones en el repositorio WSUS público de Microsoft, las instrucciones siguientes establecen los detalles de la configuración correcta en el dispositivo.  
  
> [!NOTE]  
> El Administrador de red de cliente debe proporcionar la dirección IP para un servidor DNS corporativo que pueda resolver nombres en **Microsoft.com**.  
  
1.  Uso de escritorio remoto, inicie sesión en la VM de VMM (<fabric domain>- VMM) con la cuenta de administrador de dominio de fabric.  
  
2.  Abra el Panel de Control, haga clic en **red e Internet**y, a continuación, haga clic en **centro de redes y recursos compartidos**.  
  
3.  En la lista de conexiones, haga clic en **VMSEthernet**y, a continuación, haga clic en **propiedades**.  
  
4.  Seleccione **protocolo de Internet versión 4 (TCP/IPv4)** y, a continuación, haga clic en **propiedades**.  
  
5.  En el **servidor DNS alternativo** , agregue la dirección IP proporcionada por el Administrador de red de cliente.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
