---
title: Celda (objeto) (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fc34bb3dc275e325163d8113db1a3b38c954840b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709786"
---
# <a name="cell-object-ado-md"></a>Objeto Cell (ADO MD)
Representa los datos en la intersección de coordenadas del eje contenidos en un conjunto de celdas.  
  
## <a name="remarks"></a>Comentarios  
 Un **celda** objeto devuelto por la [elemento](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) propiedad de un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objeto.  
  
 Con las colecciones y propiedades de un **celda** objeto, puede hacer lo siguiente:  
  
-   Devolver los datos en el **celda** con el [valor](../../../ado/reference/ado-md-api/value-property-ado-md.md) propiedad.  
  
-   Devolver la cadena que representa la visualización con formato de la **valor** propiedad con el [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) propiedad.  
  
-   Devolver el valor ordinal de la **celda** dentro de la **Cellset** con el [Ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) propiedad.  
  
-   Determinar la posición de la **celda** dentro de la [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) con el [posiciones](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) colección.  
  
-   Recuperar otra información sobre la **celda** con el estándar de ADO [propiedades](../../../ado/reference/ado-api/properties-collection-ado.md) colección.  
  
 El **propiedades** colección contiene las propiedades proporcionadas por el proveedor. En la tabla siguiente se enumera las propiedades que podrían estar disponibles. La lista de propiedades reales puede variar en función de la implementación del proveedor. Consulte la documentación del proveedor para obtener una lista completa de las propiedades disponibles.  
  
|NOMBRE|Descripción|  
|----------|-----------------|  
|BackColor|Color de fondo usado para mostrar la celda.|  
|FontFlags|Máscara de bits que detalla los efectos de la fuente.|  
|FontName|Fuente utilizada para mostrar el valor de celda.|  
|FontSize|Tamaño de fuente utilizado para mostrar el valor de celda.|  
|ForeColor|Color de primer plano utilizado al mostrar la celda.|  
|FormatString|Valor de una cadena con formato.|  
  
 Esta sección contiene el siguiente tema.  
  
-   [Propiedades, métodos y eventos](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de Axis (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Objeto de conjunto de celdas (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Colección de posiciones (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
