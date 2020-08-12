---
title: Configurar Reporting Services para usar un nombre alternativo del asunto | Microsoft Docs
description: Aprenda a configurar SQL Server Reporting Services para usar un SAN mediante la modificación del archivo rsreportserver.config y la herramienta Netsh.exe.
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ecb4b0be06731070c0852f23375fafea0eed4434
ms.sourcegitcommit: 66a0672e47415dbd5cfd8d19075102c8c3973e70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2020
ms.locfileid: "83767065"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>Configurar Reporting Services para usar un nombre alternativo del asunto

En este tema se explica cómo configurar Reporting Services (SSRS) para usar un nombre alternativo del asunto (SAN) modificando el archivo rsreportserver.config y usando la herramienta Netsh.exe.

Las instrucciones son válidas para la dirección URL del servicio de generación de informes y para la dirección URL del servicio web.

Para utilizar el SAN, el certificado TLS/SSL debe estar registrado en el servidor y firmado y tener la clave privada. No puede utilizar un certificado autofirmado  
  
 Las direcciones URL en Reporting Services se pueden configurar para usar un certificado TLS/SSL. Normalmente, un certificado solo tiene un nombre de asunto, que permite solo una dirección URL para una sesión de Seguridad de la capa de transporte (TLS), conocida anteriormente como Capa de sockets seguros (SSL). El SAN es un campo adicional del certificado que permite a un servicio TLS escuchar varias direcciones URL y compartir el puerto TLS con otras aplicaciones. El SAN tiene un aspecto similar a `www.s2.com`.  
  
 Para más información sobre la configuración de TLS para Reporting Services, vea [Configuración de conexiones TLS en un servidor de informes en modo nativo](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>Configurar SSRS para usar un nombre alternativo del asunto para la dirección URL del servicio web
  
1.  Inicie el Administrador de configuración de Reporting Services.  
  
     Para obtener más información, vea [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  En la página **Dirección URL del servicio web**, seleccione un puerto TLS/SSL y un certificado TLS/SSL.  
  
     ![Administrador de configuración de Reporting Services](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Administrador de configuración de Reporting Services")  
  
     El administrador de configuración registra el certificado TLS/SSL para el puerto.  
  
3.  Abra el archivo rsreportserver.config.  
  
     Para el modo nativo de SSRS, el archivo se encuentra de manera predeterminada en la carpeta siguiente:  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  Copie la sección de la URL para la aplicación de servicios web del servidor de informes.  
  
     Por ejemplo, la siguiente sección de dirección URL es:  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     La sección de dirección URL modificada siguiente es:
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  Guarde el archivo rsreportserver.config.  
  
6.  Inicie un símbolo del sistema como administrador y ejecute la herramienta Netsh.exe.  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  Cambie al contexto http escribiendo lo siguiente.  
  
    ```  
    Netsh>http  
    ```  
  
8.  Muestre las urlacl existentes escribiendo lo siguiente:
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     Aparece una entrada como la siguiente.  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     Una urlacl es una DACL (lista de control de acceso discrecional) para una dirección URL reservada.  
  
9. Cree una nueva entrada para el nombre alternativo del asunto, con el mismo usuario y SDDL que la entrada existente, escribiendo lo siguiente.  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. En la página **Estado del servidor de informes** del Administrador de configuración de Reporting Services, haga clic en **Detener** y, a continuación, haga clic en **Iniciar** para reiniciar el servidor de informes.  
  
## <a name="see-also"></a>Consulte también

 [Archivo de configuración RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Administrador de configuración de Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Modificar un archivo de configuración de Reporting Services](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [Configurar las direcciones URL del servidor de informes](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
