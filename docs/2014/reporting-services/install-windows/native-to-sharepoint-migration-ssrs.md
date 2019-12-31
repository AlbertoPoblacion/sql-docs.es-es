---
title: Migración del modo nativo al modo de SharePoint (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adf6b91b1c83f490ffe6c85fecd374fca7c1a085
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75253184"
---
# <a name="native-to-sharepoint-migration-ssrs"></a>Migración del modo nativo al modo de SharePoint (SSRS)
  No se puede actualizar o convertir desde un modo de servidor de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a otro. Por ejemplo, no puede actualizar o convertir un servidor de informes en modo nativo al modo de SharePoint. No puede copiar las bases de datos del servidor de informes entre distintos modos porque usan distintos esquemas de la base de datos. Puede migrar el contenido de un servidor de informes a otro. Las herramientas que use dependen del modo del servidor de informes configurado para los servidores de origen y de destino.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Modo nativo | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modo de SharePoint  
  
##  <a name="bkmk_native_to_sharepoint"></a>Herramienta de migración de Reporting Services  
 La herramienta admite la migración de contenido de una implementación en modo nativo a una implementación en modo de SharePoint. La herramienta no admite la migración del modo de SharePoint al modo de SharePoint o del modo de SharePoint al modo nativo.  
  
 Para obtener más información, vea herramienta de migraciónhttps://www.microsoft.com/download/details.aspx?id=29560)de [Reporting Services](https://www.microsoft.com/download/details.aspx?id=29560) (.  
  
## <a name="use-script-to-migrate-content"></a>Usar Script para migrar contenido  
 Si la herramienta de migración no satisface sus necesidades, puede migrar manualmente los datos del servidor de informes. A continuación se muestra un resumen de los pasos necesarios para migrar elementos de informe de una implementación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a otra. El método admite el modo nativo o de SharePoint como servidores de origen o de destino.  
  
1.  Realice copias de seguridad y restaure las claves de cifrado. Esta es la clave que se emplea para cifrar datos. La clave de cifrado también se usa para cifrar contraseñas, como las contraseñas almacenadas para las conexiones a orígenes de datos. Sin embargo, las contraseñas no se pueden migrar y deberá especificarlas de nuevo en el entorno de destino.  
  
2.  ** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Scripts RSS:** Escriba un script Visual Basic que llame a los métodos SOAP del servicio Web del servidor de informes para copiar datos entre las bases de datos. Emplee la utilidad **RS.exe** para ejecutar el script. Rs.exe se instala con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    -   [Ejemplo Reporting Services script RS. exe para migrar contenido entre servidores de informes](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md). En los temas se explica cómo usar el script de ejemplo que puede descargar de CodePlex.  
  
    -   El script de rss de ejemplo de CodePlex, [Script Reporting Services RS.exe que migra contenido de un servidor de informes a otro](https://azuresql.codeplex.com/releases/view/115207).  
  
    -   [Scripting y PowerShell con Reporting Services](../tools/scripting-and-powershell-with-reporting-services.md)  
  
 En la tabla siguiente se resumen los objetos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que puede migrar mediante scripts:  
  
|Objeto|Se puede incluir en scripts|Comentarios|  
|------------|---------------------|--------------|  
|Informes|Sí|Tras la migración, vuelva a escribir las contraseñas para los orígenes de datos.|  
|Orígenes de datos|Sí|Tras la migración, vuelva a vincular los informes con los orígenes de datos.|  
|Modelos|Sí||  
|Conjuntos de datos|Sí||  
|Elementos de informe||Tras la migración, compruebe o actualice la ruta de acceso a los elementos de informe.|  
|Programaciones|Sí|Vea el método ListSchedules en [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md).|  
|Suscripciones|Sí|Vea los [métodos de suscripción y entrega](../report-server-web-service/methods/subscription-and-delivery-methods.md) del método List subscriptions y el método ChangeSubscriptionOwner<xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>|  
|Instantáneas|||  
||||  
  
