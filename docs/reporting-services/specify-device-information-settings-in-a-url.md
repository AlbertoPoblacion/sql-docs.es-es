---
title: Especificar la configuración de la información del dispositivo en una dirección URL | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 906a21de49d562d788f9a1384b31e080616c67c4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "65578441"
---
# <a name="specify-device-information-settings-in-a-url"></a>Especificar la configuración de la información del dispositivo en una dirección URL
  Los valores de configuración de información de dispositivos son los parámetros que se pasan a una extensión de representación. Si usa los métodos del servicio web del servidor de informes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] para representar un informe, como parámetro de entrada se pasa un elemento XML **DeviceInfo** . Los elementos secundarios del elemento **DeviceInfo** son específicos de la configuración de información de dispositivos de diferentes extensiones de representación. Puede incluir la configuración de información de dispositivos en una dirección URL mediante la cadena de parámetro *rc:tag=value* , donde *tag* es el nombre del elemento de configuración de la información de dispositivos al que se accede. Para más información sobre la configuración de la información de dispositivos en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vea [Pasar la configuración de información de dispositivo a las extensiones de representación](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se establece el formato del informe especificado en JPEG mediante la configuración de información de dispositivos *OutputFormat* de la extensión de representación de la imagen (los saltos de línea se han agregado por legibilidad):  
  
```  
https://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Consulte también  
 [Acceso URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Referencia de parámetros de acceso URL](../reporting-services/url-access-parameter-reference.md)  
  
  
