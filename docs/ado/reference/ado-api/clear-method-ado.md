---
title: Clear (método) (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d35df7a036f41d74ce0a3fc94c3adef1abae91c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718513"
---
# <a name="clear-method-ado"></a>Clear (método) (ADO)
Quita todos los [Error](../../../ado/reference/ado-api/error-object.md) objetos desde el [errores](../../../ado/reference/ado-api/errors-collection-ado.md) colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Comentarios  
 Use la **clara** método en el [errores](../../../ado/reference/ado-api/errors-collection-ado.md) colección para quitar todos los [Error](../../../ado/reference/ado-api/error-object.md) objetos de la colección. Cuando se produce un error, ADO borra automáticamente la **errores** colección y lo rellena con **Error** objetos en función del error nuevo.  
  
 Algunos métodos y propiedades devuelven advertencias que aparecen como **Error** objetos en el **errores** colección pero no detienen la ejecución de un programa. Antes de llamar a la [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) métodos en un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto; el [abrir](../../../ado/reference/ado-api/open-method-ado-connection.md) método en un [conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto; o establecer el [filtro](../../../ado/reference/ado-api/filter-property.md) propiedad en un **Recordset** de objeto, llame a la **borrar**método en el **errores** colección. De este modo, puede leer el [recuento](../../../ado/reference/ado-api/count-property-ado.md) propiedad de la **errores** devuelve de colección para probar las advertencias.  
  
## <a name="applies-to"></a>Se aplica a  
 [Colección de errores (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Execute, Requery y Clear métodos ejemplo (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery y Clear métodos ejemplo (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery y Clear métodos ejemplo (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Método CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [El método Delete (colección Fields de ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Método Delete (colección de parámetros de ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Eliminar método (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Propiedad de filtro](../../../ado/reference/ado-api/filter-property.md)   
 [Método Resync](../../../ado/reference/ado-api/resync-method.md)   
 [Método UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
