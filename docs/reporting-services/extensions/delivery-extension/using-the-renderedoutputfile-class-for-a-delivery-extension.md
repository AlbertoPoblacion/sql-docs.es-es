---
title: Usar la clase RenderedOutputFile para una extensión de entrega | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 152a60911157b261ed95f7a68364e59470110637
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "63193665"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Usar la clase RenderedOutputFile para una extensión de entrega
  La clase <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> representa un flujo de datos e información sobre las propiedades asociadas del mismo. La propiedad **Data** de la clase <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> se usa para representar un informe representado o un recurso de informe como un objeto **Stream**.  
  
 El método <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> del objeto **Report** devuelve una matriz de uno o varios objetos <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> que constituyen en conjunto un único informe representado. El primer objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> es el informe representado. Cualquier otro objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> son los recursos que se deben entregar junto con los datos del informe (por ejemplo, un archivo HTML e imágenes asociadas). Las extensiones de representación que son extensiones de un único flujo (IMAGE, PDF, MHTML y EXCEL) devuelven solo un objeto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> en la matriz.  
  
 Para obtener un ejemplo de cómo usar la clase <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>, vea [Ejemplos del producto SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Consulte también  
 [Implementar una extensión de entrega](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Biblioteca de extensiones de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
