---
title: Interfaces y objetos ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5ecc6de67defb2366bf208c38bd2de5bff643e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920907"
---
# <a name="ado-objects-and-interfaces"></a>Interfaces y objetos ADO
Las relaciones entre estos objetos se representan en el [modelo de objetos ADO](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Cada objeto puede estar contenido en su colección correspondiente. Por ejemplo, un [Error](../../../ado/reference/ado-api/error-object.md) objeto puede incluirse en un [errores](../../../ado/reference/ado-api/errors-collection-ado.md) colección. Para obtener más información, consulte [colecciones de ADO](../../../ado/reference/ado-api/ado-collections.md) o un tema de la colección específica.  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Se usa para recuperar el comando de OLE DB subyacentes de un objeto ADOCommand.|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Construye un ADO **registro** objeto de OLE DB **fila** objeto en una aplicación de C o C++.|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Construye un ADO **Recordset** objeto de OLE DB **conjunto de filas** objeto en una aplicación de C o C++.|  
|[Interfaz ADOStreamConstruction](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Construye un ADO **Stream** objeto de OLE DB **IStream** objeto en una aplicación de C o C++.|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|Define un comando específico que se va a ejecutar en un origen de datos.<br /><br /> El **comando** objeto no es seguro para scripting.|  
|[Conexión](../../../ado/reference/ado-api/connection-object-ado.md)|Representa una conexión abierta a un origen de datos.<br /><br /> El **conexión** objeto es seguro para scripting.|  
|[Interfaz IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Obtiene el objeto de origen de datos OLEDB subyacente para el proveedor de formas.|  
|[Error](../../../ado/reference/ado-api/error-object.md)|Contiene detalles sobre los errores de acceso de datos que pertenecen a una única operación que implica al proveedor.<br /><br /> El **Error** objeto no es seguro para scripting.|  
|[Campo](../../../ado/reference/ado-api/field-object.md)|Representa una columna de datos con un tipo de datos común.|  
|[Parámetro](../../../ado/reference/ado-api/parameter-object.md)|Representa un parámetro o un argumento asociado a un **comando** objeto basado en un procedimiento almacenado o una consulta parametrizada.<br /><br /> El **parámetro** objeto no es seguro para scripting.|  
|[Propiedad](../../../ado/reference/ado-api/property-object-ado.md)|Representa una característica dinámica de un objeto ADO que está definida por el proveedor.|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|Representa una fila de un **Recordset**, o un directorio o archivo en un sistema de archivos. El **registro** objeto es seguro para scripting.|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|Representa el conjunto de registros de una tabla base o los resultados de un comando ejecutado. En cualquier momento, el **Recordset** objeto hace referencia a solo un único registro dentro del conjunto como el registro actual.<br /><br /> El **Recordset** objeto es seguro para scripting.|  
|[secuencia](../../../ado/reference/ado-api/stream-object-ado.md)|Representa un flujo binario de datos.<br /><br /> El **Stream** objeto es seguro para scripting.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API de ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Colecciones de ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Propiedades dinámicas de ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Constantes enumeradas de ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Apéndice B: Errores de ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventos de ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Métodos de ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modelo de objetos ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Propiedades de ADO](../../../ado/reference/ado-api/ado-properties.md)
