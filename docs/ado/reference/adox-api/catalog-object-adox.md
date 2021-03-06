---
title: Objeto Catalog (ADOX) | Documentos de Microsoft
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
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d8f47b63022f481c5ed102bcc9e97f5fa563aea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="catalog-object-adox"></a>Objeto Catalog (ADOX)
Contiene colecciones ([tablas](../../../ado/reference/adox-api/tables-collection-adox.md), [vistas](../../../ado/reference/adox-api/views-collection-adox.md), [usuarios](../../../ado/reference/adox-api/users-collection-adox.md), [grupos](../../../ado/reference/adox-api/groups-collection-adox.md), y [procedimientos](../../../ado/reference/adox-api/procedures-collection-adox.md)) que describen el catálogo de esquema de un origen de datos.  
  
## <a name="remarks"></a>Comentarios  
 Puede modificar el **catálogo** objeto agregando o quitando objetos o mediante la modificación de los objetos existentes. Algunos proveedores pueden no admitir todas las **catálogo** objetos o que sólo permitan ver la información de esquema.  
  
 Con las propiedades y métodos de un **catálogo** objeto, puede:  
  
-   Abrir el catálogo estableciendo la [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propiedad ADO [conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto o una cadena de conexión válida.  
  
-   Crear un nuevo catálogo con el [Create](../../../ado/reference/adox-api/create-method-adox.md) método.  
  
-   Determinar los propietarios de los objetos de un **catálogo** con el [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) y [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) métodos.  
  
 Esta sección contiene el siguiente tema.  
  
-   [Propiedades, métodos y eventos del objeto Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de propiedad ActiveConnection de catálogo (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Comando y ejemplo de las propiedades CommandText (VB)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Método de cierre de conexión, ejemplo de propiedad de tipo de tabla (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Crear el ejemplo del método (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Anexar de teclas de método, tipo de clave, RelatedColumn, RelatedTable y ejemplo de las propiedades UpdateRule (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Colección de parámetros, ejemplo de la propiedad de comando (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Ejemplo de propiedad ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Procedimientos de ejemplo de método Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Eliminar de procedimientos de ejemplo del método (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedimientos de actualización de ejemplo del método (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Vistas y ejemplo de colecciones de campos (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Vistas de ejemplo de método Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Colección de vistas, ejemplo de la propiedad CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Vistas de eliminar el ejemplo del método (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Vistas de actualización de ejemplo del método (VB)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Colección de grupos (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Colección de procedimientos (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Colección de tablas (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Colección Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Colección de vistas (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
