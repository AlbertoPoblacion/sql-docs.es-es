---
title: Arquitectura de elementos de informe personalizados | Microsoft Docs
description: Obtenga información sobre cómo la arquitectura de elementos de informe personalizados es una extensión que permite a los desarrolladores agregar funcionalidad que no se admite de forma nativa en el lenguaje RDL.
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 039afae1b8be540869930055e77320c27857e23d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216964"
---
# <a name="custom-report-item-architecture"></a>Arquitectura de elementos de informe personalizados
  Un elemento de informe personalizado es una extensión del lenguaje RDL (Report Definition Language) que permite a los programadores agregar la funcionalidad que no se admite de forma nativa en RDL o que extiende la funcionalidad de los controles existentes. Hay dos componentes principales en un elemento de informe personalizado: el componente de tiempo de ejecución y el componente de tiempo de diseño. Estos componentes se implementan como ensamblados de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] y se pueden escribir en cualquier lenguaje compatible con CLS.  
  
## <a name="the-run-time-component"></a>Componente en tiempo de ejecución  
 El procesador de informes llama en tiempo de ejecución al componente de tiempo de ejecución para un elemento de informe personalizado. El componente de tiempo de ejecución acepta los datos que pasa en tiempo de ejecución el procesador del informe, procesa estos datos y devuelve una imagen que contiene el elemento de informe personalizado representado.  
  
 ![Componente de tiempo de ejecución de elemento de informe personalizado](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "Componente de tiempo de ejecución de elemento de informe personalizado")  
  
## <a name="the-design-time-component"></a>Componente de tiempo de diseño  
 El componente de tiempo de diseño permite definir y manipular el elemento de informe personalizado en la interfaz del Diseñador de informes en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. El componente de tiempo de diseño está compuesto de varios subcontroles que controlan la apariencia y las propiedades del elemento de informe personalizado en el entorno de diseño.  
  
 ![Componente de tiempo de diseño de elemento de informe personalizado](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "Componente de tiempo de diseño de elemento de informe personalizado")  
  
## <a name="see-also"></a>Consulte también  
 [Creación de un componente de tiempo de ejecución de elemento de informe personalizado](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Creación de un componente de tiempo de diseño de elemento de informe personalizado](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Cómo: Implementar un elemento de informe personalizado](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
