---
title: Nombre (propiedad, ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c6c9ba7f2981fd4162f93f37e6ad0eb2cbae882
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311906"
---
# <a name="name-property-ado-md"></a>Name (propiedad, ADO MD)
Indica el nombre de un objeto.  
  
## <a name="return-values"></a>Valores devueltos  
 Devuelve un **cadena** y es de solo lectura.  
  
## <a name="remarks"></a>Comentarios  
 Puede recuperar el **nombre** propiedad de un objeto mediante un ordinal, tras el cual se puede hacer referencia al objeto directamente por su nombre. Por ejemplo, si `cdf.CubeDefs(0).Name` da como resultado "Bobs vídeo Store", se puede hacer referencia a este [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) como `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>Se aplica a  
  
||||  
|-|-|-|  
|[Objeto Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Objeto Catalog (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Objeto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Objeto de dimensión (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Objeto Hierarchy (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Objeto Level (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Objeto de miembro (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de catálogo (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Propiedad Caption (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Descripción (propiedad, ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName (propiedad, ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
