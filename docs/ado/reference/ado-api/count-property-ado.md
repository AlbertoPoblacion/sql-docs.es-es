---
title: Count (propiedad, ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 10f531b601e44f346e27b52e40e6591457055ee8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698453"
---
# <a name="count-property-ado"></a>Count (propiedad, ADO)
Indica el número de objetos de una colección.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un **largo** valor.  
  
## <a name="remarks"></a>Comentarios  
 Use la **recuento** propiedad para determinar cuántos objetos se encuentran en una colección determinada.  
  
 Dado que la numeración de los miembros de una colección comienza con cero, siempre se deben codificar bucles empezando por el miembro cero y terminando con el valor de la **recuento** propiedad menos 1. Si está utilizando Microsoft Visual Basic y desea recorrer los miembros de una colección sin comprobar en el **recuento** propiedad, utilice el **For Each... Siguiente** comando.  
  
 Si el **recuento** propiedad es cero, no hay ningún objeto en la colección.  
  
## <a name="applies-to"></a>Se aplica a  
  
||||  
|-|-|-|  
|[Colección Axes (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Colección de columnas (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Colección CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Colección Dimensions (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Colección de errores (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields (colección) (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Colección de grupos (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Colección Hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Colección de índices (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Colección de claves (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Colección de niveles (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Colección Members (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Colección de parámetros (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Colección de posiciones (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Colección de procedimientos (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Colección de tablas (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Colección de usuarios (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Colección de vistas (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de la propiedad de recuento (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Ejemplo de la propiedad Count (VC ++)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Actualizar (método, ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
