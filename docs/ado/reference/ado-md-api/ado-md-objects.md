---
title: Objetos de ADO MD | Documentos de Microsoft
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
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9967930e6ee7ff1310a1ea331fb972f93d902f88
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="ado-md-objects"></a>Objetos de ADO MD
|||  
|-|-|  
|[Eje](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Representa una posición o eje del filtro de un conjunto de celdas que contiene a los miembros seleccionados de una o más dimensiones.|  
|[Catálogo](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Contiene información de esquema multidimensional (es decir, cubos y dimensiones subyacentes, jerarquías, niveles y miembros) específica de un proveedor de datos multidimensionales (MDP).|  
|[Celda](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Representa los datos en la intersección de coordenadas de eje, contenidos en un conjunto de celdas.|  
|[Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Representa los resultados de una consulta multidimensional. Es una colección de celdas seleccionadas de cubos u otros conjuntos de celdas.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Representa un cubo de un esquema multidimensional, que contiene un conjunto de dimensiones relacionadas.|  
|[Dimensión](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Representa una de las dimensiones de un cubo multidimensional, que contiene una o más jerarquías de miembros.|  
|[Jerarquía de](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Representa una forma en que los miembros de una dimensión se pueden agregar o "acumular." Una dimensión puede agregarse a lo largo de una o más jerarquías.|  
|[Nivel](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Contiene un conjunto de miembros, cada uno de los cuales tiene el mismo rango dentro de una jerarquía.|  
|[Miembro](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Representa a un miembro de un nivel en un cubo, los elementos secundarios de un miembro de un nivel o un miembro de una posición a lo largo de un eje de un conjunto de celdas.|  
|[Posición](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Representa un conjunto de uno o varios miembros de distintas dimensiones que define un punto a lo largo de un eje.|  
  
 Además, el **catálogo** objeto está conectado a ADO **conexión** objeto, que se incluye con la biblioteca estándar de ADO:  
  
|Object|Description|  
|------------|-----------------|  
|[Conexión](../../../ado/reference/ado-api/connection-object-ado.md)|Representa una conexión abierta a un origen de datos.|  
  
 Las relaciones entre estos objetos se ilustran en la [el modelo de objetos de ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 Muchos objetos ADO MD pueden incluirse en una colección correspondiente. Por ejemplo, un [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) objeto puede estar contenido en una [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) colección de un **catálogo**. Para obtener más información, consulte [colecciones de ADO MD](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la API de ADO MD](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [Ejemplos de código ADO MD](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [Colecciones de ADO MD](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [Constantes enumeradas de ADO MD](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [Métodos de ADO MD](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [Modelo de objetos de ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Propiedades de ADO MD](../../../ado/reference/ado-md-api/ado-md-properties.md)
