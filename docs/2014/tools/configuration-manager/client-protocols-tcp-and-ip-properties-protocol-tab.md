---
title: 'Protocolos de cliente: propiedades de TCP y IP (pestaña protocolo) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ec3c433c1ce16e35f064910083e7ab9959e4c3bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "63253792"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a>Protocolos de cliente y Propiedades de TCP/IP (pestaña Protocolo)
  En el Administrador de configuración de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use la pestaña **Protocolo** del cuadro de diálogo **Propiedades de TCP/IP** para ver o especificar las siguientes opciones. Para conectar a un puerto diferente, escriba el número de puerto en el cuadro **Puerto predeterminado** . Para obtener más información sobre cadenas de conexión, vea [Crear una cadena de conexión válida con TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).  
  
## <a name="options"></a>Opciones  
 **Puerto predeterminado**  
 Especifica el puerto que la biblioteca de red de TCP/IP utilizará para intentar conectarse a la instancia de destino de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El puerto predeterminado es 1433.  
  
 Al conectar a una instancia predeterminada del [!INCLUDE[ssDE](../../includes/ssde-md.md)], el cliente utiliza este valor. Si se ha configurado una instancia predeterminada para que escuche en un puerto diferente, cambie este valor a dicho número de puerto.  
  
 Al conectar a una instancia con nombre del [!INCLUDE[ssDE](../../includes/ssde-md.md)], el cliente intentará obtener el número de puerto desde el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecuta en el servidor. Si el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se está ejecutando, se debe proporcionar el número de puerto mediante esta configuración o como parte de la cadena de conexión.  
  
 **Enabled**  
 Los valores posibles son **Yes** y **No**.  
  
 **Keep Alive**  
 Este parámetro (en milisegundos) controla la frecuencia con la que TCP intenta comprobar que una conexión inactiva sigue intacta mediante el envío de un paquete **KEEPALIVE** . El valor predeterminado es 30000 milisegundos.  
  
 **Intervalo de mantenimiento de conexión**  
 Este parámetro (en milisegundos) determina el intervalo que separa las retransmisiones **KEEPALIVE** hasta que se recibe una respuesta. El valor predeterminado es 1000 milisegundos.  
  
## <a name="see-also"></a>Consulte también  
 [Elegir un protocolo de red](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Nuevo alias &#40;pestaña alias&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)   
 [&#60;las propiedades de&#62; alias &#40;pestaña alias&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
