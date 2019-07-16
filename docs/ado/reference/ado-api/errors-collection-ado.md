---
title: Colección de errores (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e3c8f981d4dc40a4a6f618f3cca387379d51def9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932977"
---
# <a name="errors-collection-ado"></a>Colección de errores (ADO)
Contiene todos los [Error](../../../ado/reference/ado-api/error-object.md) objetos creados en respuesta a un error relacionado con el proveedor.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier operación que implica objetos ADO puede generar uno o varios errores del proveedor. Cuando se produce cada error, uno o varios **Error** objetos se pueden colocar en el **errores** colección de la [conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto. Cuando otra operación ADO genera un error, el **errores** se borra la colección y el nuevo conjunto de **Error** objetos se pueden colocar en el **errores** colección.  
  
 Cada **Error** objeto representa un error de proveedor específico, no un error de ADO. Errores de ADO se exponen en el mecanismo de control de excepciones de tiempo de ejecución. Por ejemplo, en Microsoft Visual Basic, la aparición de un error específico de ADO desencadenará una [onError](../../../ado/reference/rds-api/onerror-event-rds.md) eventos y aparecen en la **Err** objeto.  
  
 Las operaciones de ADO que no generan un error no tienen ningún efecto el **errores** colección. Use la [borrar](../../../ado/reference/ado-api/clear-method-ado.md) método borrar manualmente la **errores** colección.  
  
 El conjunto de **Error** objetos en el **errores** colección describe todos los errores producidos en respuesta a una única instrucción. Enumerar los errores específicos en el **errores** colección permite que las rutinas de control de errores determinar la causa y el origen de un error con más precisión y tomar las medidas adecuadas para recuperar.  
  
 Algunos métodos y propiedades devuelven advertencias que aparecen como **Error** objetos en el **errores** colección pero no detienen la ejecución de un programa. Antes de llamar a la [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) métodos en un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto, el [abrir](../../../ado/reference/ado-api/open-method-ado-connection.md) método en un **conexión** de objeto, o establecer el [filtro](../../../ado/reference/ado-api/filter-property.md) propiedad en un **Recordset** de objeto, llame a la **borrar**método en el **errores** colección. De este modo puede leer el [recuento](../../../ado/reference/ado-api/count-property-ado.md) propiedad de la **errores** devuelve de colección para probar las advertencias.  
  
> [!NOTE]
>  Consulte la **Error** tema del objeto para obtener una explicación más detallada de la forma en una única operación ADO puede generar varios errores.  
  
 Esta sección contiene el siguiente tema.  
  
-   [Los eventos, métodos y propiedades de la colección de errores](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Objeto de error](../../../ado/reference/ado-api/error-object.md)   
 [Apéndice A: proveedores](../../../ado/guide/appendixes/appendix-a-providers.md)
