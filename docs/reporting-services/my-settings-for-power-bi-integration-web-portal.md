---
title: Mi configuración para la integración de Power BI (portal web) | Microsoft Docs
description: Obtenga información sobre la página Mi configuración del portal web de Reporting Services y cómo la utilizan los usuarios para administrar su inicio de sesión con Power BI.
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f25ab8f848c642de95f1ba62eaca15bbb8b7e7d9
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248583"
---
# <a name="my-settings-for-power-bi-integration-web-portal"></a>La configuración de la integración de Power BI (portal web)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Los usuarios individuales usan la página **Mi configuración** de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] para administrar sus inicios de sesión con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Al seguir los pasos para anclar un elemento de informe, automáticamente se le pedirá que inicie sesión.  Pero puede usar la página **My Settings** (Mi configuración) si necesita iniciar sesión manualmente o si necesita cerrarla.  Si no ve la opción de menú **My Settings** (Mi configuración), se deberá a que el servidor de informes aún no se ha integrado con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Para más información, vea [Integración del servidor de informes de Power BI &#40;Administrador de configuración&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>Por qué iniciar sesión

 Al iniciar la sesión, establece una relación entre la cuenta de usuario de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] y la cuenta de [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  El inicio de sesión crea un token de seguridad que preserva un buen estado durante 90 días. Si el token expira y tiene elementos anclados a Power BI, verá una notificación.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
Los iconos de los paneles de [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] no se actualizarán hasta que vuelva a iniciar sesión a través de la página **My Settings**(Mi configuración).  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Una vez que haya iniciado sesión, se creará un token de seguridad.  Los iconos del panel empezarán a actualizarse en los programas configurados anteriormente.  

## <a name="next-steps"></a>Pasos siguientes

[Integración de Power BI Report Server](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Pin Reporting Services items to Power BI Dashboards (Anclar elementos de Reporting Services en paneles de Power BI)](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Paneles en Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[Portal web](../reporting-services/web-portal-ssrs-native-mode.md)  

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
