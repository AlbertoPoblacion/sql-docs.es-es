---
title: Conceptos de XMLA | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0da9467d293c0081309accd99fb46d7589fb4b8b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62736579"
---
# <a name="xmla-concepts"></a>Conceptos de XMLA
  El estándar abierto XML for Analysis admite el acceso a datos a orígenes de datos que residen en World Wide Web. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementa XMLA de acuerdo con la especificación XMLA 1.1.  
  
 XML for Analysis (XMLA) es un protocolo XML basado en SOAP (Protocolo simple de acceso a objetos), diseñado específicamente para el acceso universal a los datos de cualquier origen de datos multidimensionales estándar que resida en la Web. XMLA también elimina la necesidad de implementar un componente de cliente que expone el modelo de objetos componentes (COM) o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] interfaces de .NET Framework. XMLA está optimizado para Internet, donde las idas y vueltas al servidor resultan costosas en términos de tiempo y recursos, y donde las conexiones con estado a un origen de datos pueden limitar las conexiones de usuario en el servidor.  
  
 XMLA es el protocolo nativo para [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], que se usa para toda interacción entre una aplicación cliente y una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] es plenamente compatible con XML for Analysis 1.1 y, además, proporciona extensiones para admitir la administración de metadatos y de sesiones e incluir capacidades de bloqueo. Tanto Objetos de administración de análisis (AMO) como ADOMD.NET utilizan el protocolo XMLA al comunicarse con una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="handling-xmla-communications"></a>Controlar las comunicaciones XMLA  
 El estándar abierto XMLA describe dos métodos accesibles a nivel general: `Discover` y `Execute`. Estos métodos utilizan la arquitectura de cliente y servidor de acoplamiento flexible admitida por XML para controlar la información de entrada y de salida en una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 El método `Discover` obtiene información y metadatos de un servicio web. Esta información puede incluir una lista de los orígenes de datos disponibles, así como información sobre cualquiera de los proveedores de orígenes de datos. Las propiedades definen y dan forma a los datos que se obtienen de un origen de datos. El método `Discover` es un método habitual para definir los numerosos tipos de información que una aplicación cliente puede requerir de los orígenes de datos en las instancias de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Las propiedades y la interfaz genérica proporcionan extensibilidad sin necesidad de volver a escribir las funciones existentes en una aplicación cliente.  
  
 El método `Execute` permite que las aplicaciones ejecuten comandos específicos del proveedor en orígenes de datos XMLA.  
  
 Aunque el protocolo XMLA está optimizado para las aplicaciones web, también se puede aprovechar para las aplicaciones orientadas a LAN. Pueden beneficiarse de esta API basada en XML las siguientes aplicaciones:  
  
-   Aplicaciones cliente/servidor que requieren una tecnología flexible entre los clientes y el servidor  
  
-   Aplicaciones cliente/servidor destinadas a diversos sistemas operativos  
  
-   Clientes que no requieren un estado relevante para aumentar la capacidad del servidor  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA y el modelo UDM  
 XMLA es el protocolo que utilizan las aplicaciones de Business Intelligence que emplean la metodología del modelo UDM (Unified Dimensional Model).  
  
  
