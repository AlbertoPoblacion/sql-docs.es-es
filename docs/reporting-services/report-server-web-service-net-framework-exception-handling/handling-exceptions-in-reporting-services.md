---
title: Administrar las excepciones en Reporting Services | Microsoft Docs
description: Obtenga información sobre cómo controlar las excepciones que se producen en Reporting Services para que pueda determinar la siguiente acción adecuada que se debe realizar en las aplicaciones.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2e29de3a0c6b622de2abb411f36a815d7071f16d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216334"
---
# <a name="handling-exceptions-in-reporting-services"></a>Administrar las excepciones en Reporting Services
  Cuando una solicitud de cliente de la API SOAP de Reporting Services no puede completarse, el servidor de informes devuelve un error en lugar de los resultados esperados de la llamada. Cuando una llamada no puede completarse, un error para el servicio web del servidor de informes se devuelve como elemento XML **Fault** de SOAP. El elemento descriptivo clave del error es **detail**, que incluye toda la información de error proporcionada por el servidor de informes así como cualquier información de error adicional del servicio web. La información clave del elemento **detail** es el código de error del servidor de informes. Según el mensaje y el código de error, puede determinar la siguiente acción adecuada que llevar a cabo en las aplicaciones. Para obtener más información acerca de los errores de SOAP, vea el sitio web de World Wide Web Consortium (W3C) en http://www.w3.org/TR/SOAP.  
  
## <a name="soap-faults-and-the-net-framework"></a>Errores de SOAP y .NET Framework  
 En [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], si se produce un error en una solicitud de cliente al servicio web, el servidor de informes comunica el error al código de cliente que llama al servicio web iniciando un objeto **SoapException**. **SoapException** ajusta la información contenida en un error de SOAP. La propiedad **Detail** de **SoapException** se asigna al elemento **detail** en el error de SOAP. Las aplicaciones deberían detectar el objeto **SoapException** con un bloque try/catch y utilizar la propiedad **Detail** de **SoapException** para tomar las medidas apropiadas. Para más información sobre la clase **SoapException** y la propiedad **Detail** en [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vea [Clase SoapException de Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md). Para más información sobre la clase **SoapException**, vea la documentación del SDK de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [Propiedad Detail](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Introducción a la administración de excepciones en Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Clase SoapException de Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
