---
title: Atributos basados en dominios (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7552d30b0c435147cc9b94a01ec9303977fc7f00
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65487512"
---
# <a name="domain-based-attributes-master-data-services"></a>Atributos basados en dominios (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], un atributo basado en dominio es un atributo con valores rellenados por miembros de otra entidad. Se podría considerar que un atributo basado en dominio es una lista restringida; los atributos basados en dominios evitan que los usuarios puede especificar valores de atributo no válidos. Para seleccionar un valor de atributo, el usuario debe elegir en una lista.  
  
## <a name="domain-based-attribute-example"></a>Ejemplo de atributo basado en dominio  
 En la imagen siguiente, la entidad Product tiene un atributo basado en dominio denominado Subcategory. El atributo Subcategory se rellena con los valores de la entidad Subcategory.  
  
 La entidad Category tiene un atributo basado en domino denominado Subcategory. El atributo Category se rellena con los valores de la entidad Category.  
  
 ![Atributos basados en dominio en una entidad](../master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Atributos basados en dominio en una entidad")  
  
## <a name="use-same-entity-for-multiple-domain-based-attributes"></a>Usar la misma entidad para varios atributos basados en dominios  
 Puede usar la misma entidad que un atributo basado en dominio de varias entidades. Por ejemplo, puede crear una entidad denominada YesNoIndicator con los miembros: Yes, No y Maybe. Puede crear un atributo basado en dominio denominado InStock y usar la entidad YesNoIndicator como origen. También puede crear otro atributo basado en dominio denominado Approved y usar la entidad YesNoIndicator como origen. Siempre que desee que los usuarios elijan en una lista de los miembros de la entidad YesNoIndicator, puede usar la entidad como atributo basado en dominio.  
  
## <a name="domain-based-attributes-form-derived-hierarchies"></a>Los atributos basados en dominio forman jerarquías derivadas  
 Las relaciones de atributo basados en dominio son la base de las jerarquías derivadas. Para obtener más información, consulte [Jerarquías derivadas &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Crear un nuevo atributo basado en dominio originado en una entidad existente.|[Crear un atributo basado en dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Crear una entidad nueva.|[Crear una entidad &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Jerarquías derivadas &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Atributos &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [Entidades &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
