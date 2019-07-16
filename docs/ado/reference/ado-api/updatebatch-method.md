---
title: Método UpdateBatch | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e9d74fe938ce486a4cd15573af8166dbed12ba6f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937841"
---
# <a name="updatebatch-method"></a>Método UpdateBatch
Escribe todas las actualizaciones por lotes pendientes en el disco.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Parámetros  
 *AffectRecords*  
 Opcional. Un [AffectEnum](../../../ado/reference/ado-api/affectenum.md) valor que indica cuántos registros la **UpdateBatch** afectará a método.  
  
 *PreserveStatus*  
 Opcional. Un **booleano** valor que especifica si los cambios locales, tal y como indica la [estado](../../../ado/reference/ado-api/status-property-ado-recordset.md) propiedad, se deben confirmar. Si este valor se establece en **True**, **estado** propiedad de cada registro permanece sin cambios una vez completada la actualización.  
  
## <a name="remarks"></a>Comentarios  
 Use la **UpdateBatch** método cuando se modifica un **Recordset** objeto en modo de actualización por lotes para transmitir todos los cambios realizados en un **Recordset** objeto a la base de datos subyacente.  
  
 Si el **Recordset** objeto admite la actualización por lotes, puede almacenar en caché los cambios de varios a uno o más registros localmente hasta que llame a la **UpdateBatch** método. Si está modificando el registro actual o agregando un nuevo registro al llamar a la **UpdateBatch** método, ADO llamará automáticamente a la [actualización](../../../ado/reference/ado-api/update-method.md) método para guardar los cambios pendientes en el registro actual antes de transmitir los cambios por lotes al proveedor. Debe usar la actualización por lotes con un conjunto de claves o un cursor estático solo.  
  
> [!NOTE]
>  Especificar **adAffectGroup** como el valor para este parámetro producirá un error cuando no hay ningún registro visible actual **Recordset** (por ejemplo, un filtro que coincide con ningún registro).  
  
 Si falla el intento de transmitir los cambios de algunos o todos los registros debido a un conflicto con los datos subyacentes (por ejemplo, otro usuario ya se ha eliminado un registro), el proveedor devuelve advertencias a la [errores](../../../ado/reference/ado-api/errors-collection-ado.md) colección y una se produce el error de tiempo de ejecución. Use la [filtro](../../../ado/reference/ado-api/filter-property.md) propiedad (**adFilterAffectedRecords**) y el [estado](../../../ado/reference/ado-api/status-property-ado-recordset.md) propiedad para localizar los registros con conflictos.  
  
 Para cancelar todas las pendientes las actualizaciones por lotes, utilice el [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) método.  
  
 Si el [Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) y [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) se establecen las propiedades dinámicas y el **Recordset** es el resultado de ejecutar una operación JOIN en varias tablas, el ejecución de la **UpdateBatch** método va seguido de forma implícita el [Resync](../../../ado/reference/ado-api/resync-method.md) método, según la configuración de la [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) propiedad.  
  
 El orden en que se realizan las actualizaciones individuales de un lote en el origen de datos no es necesariamente el mismo que el orden en el que se realizaron en el equipo local **Recordset**. Orden de actualización depende del proveedor. Tenga esto en cuenta al programar las actualizaciones que están relacionadas entre sí, como las restricciones de clave externa en una inserción o actualización.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo UpdateBatch y CancelBatch métodos (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Ejemplo UpdateBatch y CancelBatch métodos (VC ++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Método CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Clear (método) (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Propiedad LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Update (método)](../../../ado/reference/ado-api/update-method.md)
