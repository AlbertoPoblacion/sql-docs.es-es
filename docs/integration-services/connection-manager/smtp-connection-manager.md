---
title: Administrador de conexiones SMTP | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.smtpconnection.f1
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 11de8cccd124fb8de58ca9ba5aa7aceebb3a12a7
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58273931"
---
# <a name="smtp-connection-manager"></a>Administrador de conexiones SMTP
  Un administrador de conexiones SMTP permite a un paquete conectarse a un servidor de Protocolo simple de transferencia de correo (SMTP). La tarea Enviar correo que incluye [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa un administrador de conexiones SMTP.  
  
 Si utiliza Microsoft Exchange como servidor SMTP, es posible que necesite configurar el administrador de conexiones SMTP para que utilice la autenticación de Windows. Es posible que los servidores Exchange estén configurados para no permitir conexiones SMTP no autenticadas.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Configuración del administrador de conexiones SMTP  
 Cuando agrega un administrador de conexiones SMTP a un paquete, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea un administrador de conexiones que se resuelve como una conexión SMTP en tiempo de ejecución, establece las propiedades del administrador de conexiones y agrega el administrador de conexiones a la colección **Conexiones** del paquete. La propiedad **ConnectionManagerType** del administrador de conexiones se establece en **SMTP**.  
  
 Puede configurar el administrador de conexiones SMTP de las maneras siguientes:  
  
-   Proporcionar una cadena de conexión.  
  
-   Especificar el nombre de un servidor SMTP.  
  
-   Especificar el método de autenticación que se va a utilizar.  
  
    > [!IMPORTANT]  
    >  El administrador de conexiones SMTP solo es compatible con la autenticación anónima y la autenticación de Windows. No admite la autenticación básica.  
  
-   Especificar si la comunicación se cifrará mediante SSL (Capa de sockets seguros) al enviar mensajes de correo electrónico.  
  
 Puede establecer propiedades a través del Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] o mediante programación.  
  
 Para obtener más información sobre las propiedades que puede configurar en el Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vea [Editor del administrador de conexiones SMTP](../../integration-services/connection-manager/smtp-connection-manager-editor.md).  
  
 Para obtener información sobre la configuración de un administrador de conexiones mediante programación, vea <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> y [Agregar conexiones mediante programación](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="smtp-connection-manager-editor"></a>Editor del administrador de conexiones SMTP
  Use el cuadro de diálogo **Editor del administrador de conexiones SMTP** para especificar un servidor de protocolo simple de transferencia de correo (SMTP).  
  
 Para obtener más información acerca del administrador de conexiones SMTP, vea [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
### <a name="options"></a>Opciones  
 **Nombre**  
 Proporcione un nombre único para el administrador de conexiones.  
  
 **Descripción**  
 Describa el administrador de conexiones. Como método recomendado, describa el administrador de conexiones desde el punto de vista de su propósito, para que los paquetes estén autodocumentados y sean más fáciles de mantener.  
  
 **Servidor SMTP**  
 Proporcione el nombre del servidor SMTP.  
  
 **Utilizar autenticación de Windows**  
 Seleccione esta opción para enviar correo electrónico mediante un servidor SMTP que utiliza Autenticación de Windows para autenticar el acceso al servidor.  
  
> [!IMPORTANT]  
>  El administrador de conexiones SMTP solo es compatible con la autenticación anónima y la autenticación de Windows. No admite la autenticación básica.  
  
> [!NOTE]  
>  Cuando utilice Microsoft Exchange como servidor SMTP, es posible que deba establecer **Utilizar autenticación de Windows** en **True**. Es posible que los servidores Exchange estén configurados para no permitir conexiones SMTP no autenticadas.  
  
 **Habilitar capa de sockets seguros (SSL)**  
 Seleccione esta opción para cifrar comunicación mediante Capa de sockets seguros (SSL) al enviar mensajes de correo electrónico.  
  
