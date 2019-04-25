---
title: Configurar el almacenamiento de datos paralelos para copias de la tabla remota | Microsoft Docs
description: Describe cómo configurar el almacenamiento de datos paralelos para usar la característica de copia de la tabla remota para copiar tablas de bases de datos de SQL Server de SMP en servidores que no sea de dispositivo.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: fdac0b6ed211e223c3fad7ba15ac79a282c61303
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62509527"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Configurar el almacenamiento de datos paralelos para copias de la tabla remota
Describe cómo configurar SQL Server PDW para usar la característica de copia de la tabla remota para copiar tablas de bases de datos de SQL Server de SMP en servidores que no sea de dispositivo.  
  
Este tema describe uno de los pasos de configuración para configurar la copia de la tabla remota. Para obtener una lista de todos los pasos de configuración, consulte [copia remota de la tabla](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Antes de empezar  
Para configurar SQL Server PDW para usar la copia de la tabla remota, debe:  
  
-   Tener una cuenta de administrador de Analytics Platform System con la capacidad de iniciar sesión directamente en el  <strong>*appliance_domain*-AD01</strong> y  <strong>*appliance_domain*-AD02</strong> nodos.  
  
-   Conocer el nombre de host o IP del servidor de destino.  
  
## <a name="HowToPDW"></a>Configurar SQL Server PDW para copia de la tabla remota: Actualizar los nombres de Host en DNS  
El **CREATE REMOTE TABLE** instrucción, que se utiliza para las copias de la tabla remota, especifica el servidor de destino mediante el uso de la dirección IP o el nombre IP del sistema de Windows de SMP. Para usar el nombre IP, deberá agregar entradas para la resolución de nombres correcta para el servidor DNS.  
  
Los siguientes pasos describen cómo actualizar el servidor DNS.  
  
1.  Inicie sesión en el nodo activo de AD (normalmente  <strong>*appliance_domain*-AD01</strong>).  
  
2.  Abra el Administrador de DNS. Esto se encuentra en **herramientas administrativas** en el **iniciar** menú.  
  
3.  Use el Administrador de DNS para agregar el nombre IP.  
  
## <a name="see-also"></a>Vea también  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Usar un reenviador DNS para resolver nombres DNS que no sea de dispositivo](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
