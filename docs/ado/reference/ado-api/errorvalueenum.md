---
title: ErrorValueEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ErrorValueEnum
helpviewer_keywords:
- ErrorValueEnum enumeration [ADO]
ms.assetid: 9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f9efa743e6e5f9efe99e08001980ab87bf13247
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695226"
---
# <a name="errorvalueenum"></a>ErrorValueEnum
Especifica el tipo de error de tiempo de ejecución de ADO.  
  
 Se muestran tres formas del número de error:  
  
-   Positivos decimal, el bajo dos bytes del número completo en formato decimal. Este número se muestra en el cuadro de diálogo del mensaje de error predeterminada Visual Basic. Por ejemplo, error de tiempo de ejecución "3707".  
  
-   Negativo decimal, la traducción decimal del número de error completo.  
  
-   Hexadecimal, la representación hexadecimal del número de error completo. El código de componente de Windows está en el cuarto dígito. El código de servicio para los números de error de ADO es *A*. Por ejemplo: 0x800***A***0E7B.  
  
> [!NOTE]
>  Errores de OLE DB pueden pasarse a la aplicación de ADO. Normalmente, estos pueden identificarse mediante un código de servicio de Windows de *4*. Por ejemplo, 0 x 800***4***.  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|**adErrBoundToCommand**|3707 -2146824581 0x800A0E7B|No se puede cambiar el **ActiveConnection** propiedad de un **Recordset** objeto que tiene un **comando** objeto como su origen.|  
|**adErrCannotComplete**|3732 -2146824556 0x800A0E94|Servidor no puede completar la operación.|  
|**adErrCantChangeConnection**|3748 -2146824540 0x800A0EA4|Se denegó la conexión. Nueva conexión solicitada tiene características diferentes de lo que ya está en uso.|  
|**adErrCantChangeProvider**|3220 -2146825068 0X800A0C94|El proveedor suministrado es diferente al ya está en uso.|  
|**adErrCantConvertvalue**|3724 -2146824564 0x800A0E8C|No se puede convertir el valor de datos por razones distintas del desbordamiento de datos o la falta de coincidencia de inicio de sesión. Por ejemplo, conversión habría truncado los datos.|  
|**adErrCantCreate**|3725 -2146824563 0x800A0E8D|Valor de datos no se puede establecer o recuperar porque se desconoce el tipo de datos de campo o el proveedor tuvo recursos insuficientes para realizar la operación.|  
|**adErrCatalogNotSet**|3747 -2146824541 0x800A0EA3|Operación requiere válido **ParentCatalog**.|  
|**adErrColumnNotOnThisRow**|3726 -2146824562 0x800A0E8E|Registro no contiene este campo.|  
|**adErrDataConversion**|3421 -2146824867 0x800A0D5D|Aplicación utiliza un valor de un tipo incorrecto para la operación actual.|  
|**adErrDataOverflow**|3721 -2146824567 0x800A0E89|Valor de datos es demasiado grande para representarlo mediante el tipo de datos.|  
|**adErrDelResOutOfScope**|3738 -2146824550 0x800A0E9A|Dirección URL del objeto que se va a eliminar está fuera del ámbito del registro actual.|  
|**adErrDenyNotSupported**|3750 -2146824538 0x800A0EA6|Proveedor no admite restricciones de uso compartido.|  
|**adErrDenyTypeNotSupported**|3751 -2146824537 0x800A0EA7|Proveedor no admite el tipo solicitado de restricción de uso compartido.|  
|**adErrFeatureNotAvailable**|3251 -2146825037 0x800A0CB3|Objeto o el proveedor no es capaz de realizar la operación solicitada.|  
|**adErrFieldsUpdateFailed**|3749 -2146824539 0x800A0EA5|Error al actualizar los campos. Para obtener más información, examine el **estado** propiedad de cada objeto de campo.|  
|**adErrIllegalOperation**|3219 -2146825069 0x800A0C93|Operación no se permite en este contexto.|  
|**adErrIntegrityViolation**|3719 -2146824569 0x800A0E87|Valor de datos está en conflicto con las restricciones de integridad del campo.|  
|**adErrInTransaction**|3246 -2146825042 0x800A0CAE|**Conexión** objeto no se puede cerrar explícitamente en una transacción.|  
|**adErrInvalidArgument**|3001 -2146825287 0x800A0BB9|Los argumentos son del tipo incorrecto, están fuera del intervalo aceptable o están en conflicto entre sí.|  
|**adErrInvalidConnection**|3709 -2146824579 0x800A0E7D|La conexión no se puede usar para realizar esta operación. Es cerrado o no válido en este contexto.|  
|**adErrInvalidParamInfo**|3708 -2146824580 0x800A0E7C|**Parámetro** objeto está definido de forma incorrecta. Se proporcionó información incoherente o incompleta.|  
|**adErrInvalidTransaction**|3714 -2146824574 0x800A0E82|Coordinación de transacciones no es válido o no se ha iniciado.|  
|**adErrInvalidURL**|3729 -2146824559 0x800A0E91|Dirección URL contiene caracteres no válidos. Asegúrese de que la dirección URL está escrita correctamente.|  
|**adErrItemNotFound**|3265 -2146825023 0x800A0CC1|No se encuentra el elemento de la colección que corresponde al nombre solicitado u ordinal.|  
|**adErrNoCurrentRecord**|3021 -2146825267 0x800A0BCD|Cualquier **BOF** o **EOF** es True, o se ha eliminado el registro actual. La operación solicitada requiere un registro actual.|  
|**adErrNotExecuting**|3715 -2146824573 0x800A0E83|No se puede realizar la operación mientras no se ejecute.|  
|**adErrNotReentrant**|3710 -2146824578 0x800A0E7E|No se puede realizar la operación al evento de procesamiento.|  
|**adErrObjectClosed**|3704 -2146824584 0x800A0E78|No se permite la operación cuando el objeto está cerrado.|  
|**adErrObjectInCollection**|3367 -2146824921 0x800A0D27|Objeto ya está en la colección. No se puede anexar.|  
|**adErrObjectNotSet**|3420-2146824868 0x800A0D5C|Objeto ya no es válido.|  
|**adErrObjectOpen**|3705 -2146824583 0x800A0E79|No se permite la operación cuando el objeto está abierto.|  
|**adErrOpeningFile**|3002 -2146825286 0x800A0BBA|No se pudo abrir el archivo.|  
|**adErrOperationCancelled**|3712 -2146824576 0x800A0E80|Operación cancelada por el usuario.|  
|**adErrOutOfSpace**|3734 -2146824554 0x800A0E96|No se puede realizar la operación. Proveedor no puede obtener suficiente espacio de almacenamiento.|  
|**adErrPermissionDenied**|3720 -2146824568 0x800A0E88|Permisos insuficientes impide escribir en el campo.|  
|**adErrProviderFailed**|3000 -2146825288 0x800A0BB8|Proveedor no llevó a cabo la operación solicitada.|  
|**adErrProviderNotFound**|3706 -2146824582 0x800A0E7A|No se encuentra el proveedor. Es posible que no esté correctamente instalado.|  
|**adErrReadFile**|3003 -2146825285 0x800A0BBB|No se pudo leer el archivo.|  
|**adErrResourceExists**|3731 -2146824557 0x800A0E93|No se puede realizar la operación de copia. Objeto con nombre mediante la dirección URL de destino ya existe. Especificar **adCopyOverwrite** para reemplazar el objeto.|  
|**adErrResourceLocked**|3730 -2146824558 0x800A0E92|Objeto que representa la dirección URL especificada está bloqueado por uno o varios procesos. Espere hasta que haya finalizado el proceso y vuelva a intentarlo.|  
|**adErrResourceOutOfScope**|3735 -2146824553 0x800A0E97|Dirección URL de origen o destino está fuera del ámbito del registro actual.|  
|**adErrSchemaViolation**|3722 -2146824566 0x800A0E8A|Valor de datos está en conflicto con el tipo de datos o las restricciones del campo.|  
|**adErrSignMismatch**|3723 -2146824565 0x800A0E8B|Error de conversión porque el valor de datos tenía signo y el tipo de datos utilizado por el proveedor no tenía signo.|  
|**adErrStillConnecting**|3713 -2146824575 0x800A0E81|No se puede realizar la operación mientras se conecta de forma asincrónica.|  
|**adErrStillExecuting**|3711 -2146824577 0x800A0E7F|No se puede realizar la operación mientras se ejecuta de forma asincrónica.|  
|**adErrTreePermissionDenied**|3728 -2146824560 0x800A0E90|Los permisos son insuficientes para acceder a árbol o subárbol.|  
|**adErrUnavailable**|3736 -2146824552 0x800A0E98|No se completó la operación y el estado no está disponible. El campo no esté disponible o no se intentó realizar la operación.|  
|**adErrUnsafeOperation**|3716 -2146824572 0x800A0E84|Configuración de seguridad de este equipo evita el acceso a un origen de datos en otro dominio.|  
|**adErrURLDoesNotExist**|3727 -2146824561 0x800A0E8F|La dirección URL de origen o el elemento primario de la dirección URL de destino no existe.|  
|**adErrURLNamedRowDoesNotExist**|3737 -2146824551 0x800A0E99|Esta dirección URL con el nombre de registro no existe.|  
|**adErrVolumeNotFound**|3733 -2146824555 0x800A0E95|El proveedor no puede encontrar el dispositivo de almacenamiento indicado por la dirección URL. Asegúrese de que la dirección URL está escrita correctamente.|  
|**adErrWriteFile**|3004 -2146825284 0x800A0BBC|Escritura en un archivo error.|  
|**adWrnSecurityDialog**|3717 -2146824571 0x800A0E85|Exclusivamente para uso interno. No debe usarse.|  
|**adWrnSecurityDialogHeader**|3718 -2146824570 0x800A0E86|Exclusivamente para uso interno. No debe usarse.|  
  
## <a name="adowfc-equivalent"></a>Equivalente de ADO y WFC  
 Package: **com.ms.wfc.data**  
  
 Se definen sólo los subconjuntos siguientes de equivalentes ADO y WFC.  
  
|Constante|  
|--------------|  
|AdoEnums.ErrorValue.BOUNDTOCOMMAND|  
|AdoEnums.ErrorValue.DATACONVERSION|  
|AdoEnums.ErrorValue.FEATURENOTAVAILABLE|  
|AdoEnums.ErrorValue.ILLEGALOPERATION|  
|AdoEnums.ErrorValue.INTRANSACTION|  
|AdoEnums.ErrorValue.INVALIDARGUMENT|  
|AdoEnums.ErrorValue.INVALIDCONNECTION|  
|AdoEnums.ErrorValue.INVALIDPARAMINFO|  
|AdoEnums.ErrorValue.ITEMNOTFOUND|  
|AdoEnums.ErrorValue.NOCURRENTRECORD|  
|AdoEnums.ErrorValue.NOTEXECUTING|  
|AdoEnums.ErrorValue.NOTREENTRANT|  
|AdoEnums.ErrorValue.OBJECTCLOSED|  
|AdoEnums.ErrorValue.OBJECTINCOLLECTION|  
|AdoEnums.ErrorValue.OBJECTNOTSET|  
|AdoEnums.ErrorValue.OBJECTOPEN|  
|AdoEnums.ErrorValue.OPERATIONCANCELLED|  
|AdoEnums.ErrorValue.PROVIDERNOTFOUND|  
|AdoEnums.ErrorValue.STILLCONNECTING|  
|AdoEnums.ErrorValue.STILLEXECUTING|  
|AdoEnums.ErrorValue.UNSAFEOPERATION|  
  
## <a name="applies-to"></a>Se aplica a  
 [Propiedad Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Captura de códigos de Error de ADO](../../../ado/guide/appendixes/ado-error-codes.md)
