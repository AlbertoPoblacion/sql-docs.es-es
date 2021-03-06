---
title: Errores y advertencias Events Data Columns | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Errors and Warnings event category [SQL Server]
ms.assetid: f375d303-7aab-4c51-a955-05a2762cc4d1
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7c3e94c56f836301b853902751c2fb4085e2df7e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="errors-and-warnings-events-data-columns"></a>Columnas de datos de eventos de Errores y advertencias
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]La categoría de eventos de auditoría de seguridad tiene la siguiente clase de evento:  
  
-   Clase de error  
  
 En la siguiente tabla se muestran las columnas de datos de esta clase de eventos.  
  
## <a name="error-event-classdata-columns"></a>Columnas de datos de la clase de eventos Error  
  
|**Nombre de la columna**|**Identificador de la columna**|**Tipo de columna**|**Descripción de la columna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|EventClass se usa para clasificar los eventos.|  
|StartTime|3|5|Contiene la hora a la que se inició el evento, si está disponible. Para filtrar, los formatos esperados son "AAAA-MM-DD" y "AAAA-MM-DD HH:MM:SS".|  
|SessionType|8|8|Contiene el tipo de la entidad que causó el error.|  
|Severity|22|1|Contiene el nivel de gravedad de una excepción asociada al evento de error. Los valores son:<br /><br /> 0 = Correcto.<br /><br /> 1 = De información<br /><br /> 2 = Advertencia<br /><br /> 3 = Error|  
|Success|23|1|Contiene un valor que indica el éxito o el fracaso del evento de error. Los valores son:<br /><br /> 0 = Error<br /><br /> 1 = Correcto|  
|Error|24|1|Contiene el número de error de cualquier error asociado al evento de error.|  
|ConnectionID|25|1|Contiene el identificador único de conexión asociado al evento de error.|  
|DatabaseName|28|8|Contiene el nombre de la instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en la que se ha producido el evento de error.|  
|NTUserName|32|8|Contiene el nombre de usuario de Windows asociado al evento de error.|  
|NTDomainName|33|8|Contiene la cuenta de dominio de Windows asociada al evento de inicio de sesión.|  
|ClientHostName|35|8|Contiene el nombre del equipo en el que se está ejecutando el cliente. Esta columna de datos se rellena si el cliente proporciona el nombre del host.|  
|ClientProcessID|36|1|Contiene el identificador del proceso de la aplicación cliente.|  
|ApplicationName|37|8|Contiene el nombre de la aplicación cliente que ha creado la conexión con el servidor. Esta columna se rellena con los valores que pasa la aplicación, en lugar de con el nombre que se muestra para el programa.|  
|SessionID|39|8|Contiene el identificador de proceso de servidor (SPID) que identifica de forma única la sesión de usuario asociada al evento de error. El SPID corresponde directamente al GUID de sesión usado por XML for Analysis (XMLA).|  
|SPID|41|1|Contiene el identificador de proceso de servidor (SPID) que identifica de forma única la sesión de usuario asociada al evento de error. El SPID corresponde directamente al GUID de sesión usado por XML for Analysis (XMLA).|  
|TextData|42|9|Contiene los datos de texto asociados al evento de error.|  
|ServerName|43|8|Contiene el nombre del servidor que ejecuta la instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en la que se ha producido el evento de error.|  
  
## <a name="see-also"></a>Ver también  
 [Auditoría de seguridad (categoría de eventos)](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
