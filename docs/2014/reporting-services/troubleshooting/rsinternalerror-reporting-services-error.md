---
title: 'rsInternalError: error de Reporting Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 302772c87a1e1d4e5cf3ab1e7c5a304e6100b785
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66099156"
---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Error de Reporting Services
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|rsInternalError|  
|Origen del evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texto del mensaje|Error interno en el servidor de informes. Vea el registro de errores para obtener más detalles.|  
  
## <a name="explanation"></a>Explicación  
 Se trata de un mensaje de error genérico que suele ir seguido de un error más descriptivo que proporciona más información.  
  
 Los errores internos no son comunes. Si obtiene este error, puede conseguir más información en los registros de seguimiento del servidor de informes. Además, si está ejecutando como administrador local en el mismo equipo en el que se produjo el error, puede ver la pila de llamadas para obtener más información.  
  
## <a name="user-action"></a>Acción del usuario  
 Para determinar la causa específica de este mensaje, revise los archivos de registro del servidor de informes, que se encuentran en \Microsoft SQL Server\MSRS12.\<nombreDeInstancia >\Reporting Services\LogFiles. Para más información, vea [Archivos de registro y orígenes de Reporting Services](../report-server/reporting-services-log-files-and-sources.md).  
  
 Para ver la pila de llamadas, haga clic con el botón derecho en la página donde se ha producido el error y seleccione **Ver código fuente**. Esta acción requiere tener permisos de administrador para el mismo equipo en que se produce el error.  
  
 Si no hay información adicional disponible, puede intentar de nuevo la solicitud.  
  
## <a name="internal-only"></a>Solo para uso interno  
  
## <a name="see-also"></a>Vea también  
 [Iniciar y detener el servicio del servidor de informes](../report-server/start-and-stop-the-report-server-service.md)  
  
  
