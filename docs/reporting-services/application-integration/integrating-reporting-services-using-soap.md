---
title: Integración mediante SOAP
description: La API de SOAP de Reporting Services proporciona varios puntos de conexión de servicio web para desarrollar soluciones de informes personalizadas.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c19676b59b2de393f7d68a6660ec33db50c29e09
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "74796959"
---
# <a name="integrating-reporting-services-using-soap"></a>Integrar Reporting Services con SOAP
  La API de SOAP de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] proporciona varios puntos de conexión de servicio web para desarrollar soluciones de informes personalizadas. Actualmente, los extremos pertenecen a dos categorías: administración y ejecución. La funcionalidad de administración se expone a través de los extremos <xref:ReportService2005>, <xref:ReportService2006> y <xref:ReportService2010>. El extremo <xref:ReportService2005> se utiliza para administrar un servidor de informes que se configura en modo nativo y el extremo <xref:ReportService2006> se utiliza para administrar un servidor de informes que se configura para el modo integrado de SharePoint. <xref:ReportService2010> combina las funcionalidades de <xref:ReportService2005> y <xref:ReportService2006>, y puede administrar o un servidor de informes que esté configurado para el modo nativo o integrado de SharePoint.  
  
> [!NOTE]  
>  Los tipos de datos <xref:ReportService2005> y <xref:ReportService2006> están desusados en [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. El extremo <xref:ReportService2010> incluye las funcionalidades de ambos extremos y contiene características de administración adicionales.  
  
 La funcionalidad de ejecución se expone a través del extremo <xref:ReportExecution2005> y se utiliza cuando el servidor de informes se configura en modo integrado de SharePoint o nativo. En los siguientes temas se muestra cómo pueden utilizarse estos extremos para desarrollar soluciones de informes en las aplicaciones web, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows y SharePoint.  
  
## <a name="in-this-section"></a>En esta sección  
 [Usar la API de SOAP en una aplicación Windows](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
 Describe cómo usar la API SOAP para integrar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en un entorno de Windows.  
  
 [Usar la API de SOAP en una aplicación web](../../reporting-services/application-integration/integrating-reporting-services-using-soap-web-application.md)  
 Describe cómo utilizar la API SOAP para integrar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en un entorno web.  
  
## <a name="see-also"></a>Consulte también  
 [Integración de Reporting Services en las aplicaciones](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Servicio web del servidor de informes](../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Creación de aplicaciones con el servicio web y .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
