---
title: Objeto CubeDef (ADO MD) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea97010f67e571ddf9ddfb1dcc1cf36e38769710
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="cubedef-object-ado-md"></a>Objeto CubeDef (ADO MD)
Representa un cubo de un esquema multidimensional, que contiene un conjunto de dimensiones relacionadas.  
  
## <a name="remarks"></a>Comentarios  
 Con las colecciones y las propiedades de un **CubeDef** objeto, puede hacer lo siguiente:  
  
-   Identificar un **CubeDef** con el [nombre](../../../ado/reference/ado-md-api/name-property-ado-md.md) propiedad.  
  
-   Devolver una cadena que describe el cubo con la [descripción](../../../ado/reference/ado-md-api/description-property-ado-md.md) propiedad.  
  
-   Devolver las dimensiones que conforman el cubo con la [dimensiones](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) colección.  
  
-   Obtener información adicional sobre la **CubeDef** con ADO estándar [propiedades](../../../ado/reference/ado-api/properties-collection-ado.md) colección.  
  
 El **propiedades** colección contiene propiedades proporcionadas por el proveedor. En la tabla siguiente se enumera propiedades que estén disponibles. La lista de propiedades reales puede variar en función de la implementación del proveedor. Consulte la documentación del proveedor para obtener una lista completa de propiedades disponibles.  
  
|Nombre|Description|  
|----------|-----------------|  
|CatalogName|El nombre del catálogo al que pertenece este cubo.|  
|CreatedOn|Fecha y hora de creación del cubo.|  
|CubeGUID|GUID del cubo.|  
|CubeName|Nombre del cubo.|  
|CubeType|El tipo de cubo.|  
|DataUpdatedBy|Id. de usuario de la persona que realiza la última actualización de datos.|  
|Description|Una descripción significativa del cubo.|  
|LastSchemaUpdate|Fecha y hora de última actualización del esquema.|  
|SchemaName|El nombre del esquema al que pertenece este cubo.|  
|SchemaUpdatedBy|Id. de usuario de la persona que realiza la última actualización del esquema.|  
  
 Esta sección contiene el siguiente tema.  
  
-   [Propiedades, métodos y eventos](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Objeto Catalog (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [Colección CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Colección Dimensions (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
