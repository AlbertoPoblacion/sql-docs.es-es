---
title: Método Open (Record ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4d105d648c7877e7099dea637c2a2c6a094985f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241087"
---
# <a name="open-method-ado-record"></a>Open (método) (registro de ADO)
Se abre una existente [registro](../../../ado/reference/ado-api/record-object-ado.md) de objeto o crea un nuevo elemento representado por la **registro**, por ejemplo, un archivo o directorio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Source*  
 Opcional. Un **Variant** que puede representar la dirección URL de la entidad para ser representado por este **registro** objeto, un **comando**, abierto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o otro **registro** (objeto), una cadena que contiene una instrucción SQL SELECT o un nombre de tabla.  
  
 *ActiveConnection*  
 Opcional. Un **Variant** que representa la cadena de conexión o abierto [conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto.  
  
 *Modo*  
 Opcional. Un [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) valor que especifica el modo de acceso para el resultado **registro** objeto. Valor predeterminado es **adModeUnknown**.  
  
 *CreateOptions*  
 Opcional. Un [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) valor que especifica si se debe abrir un archivo o directorio existente, o si se debe crear un nuevo archivo o directorio. Valor predeterminado es **adFailIfNotExists**. Si se establece en el valor predeterminado, el modo de acceso se obtiene de la [modo](../../../ado/reference/ado-api/mode-property-ado.md) propiedad. Este parámetro se omite cuando el *origen* parámetro no tiene una dirección URL.  
  
 *Opciones*  
 Opcional. Un [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md) valor que especifica opciones para abrir el **registro**. Valor predeterminado es **adOpenRecordUnspecified**. Estos valores se pueden combinar.  
  
 *UserName*  
 Opcional. Un **cadena** valor que contiene el identificador de usuario que, si es necesario, autoriza el acceso a *origen*.  
  
 *Contraseña*  
 Opcional. Un **cadena** valor que contiene la contraseña que, si es necesario, comprueba *UserName*.  
  
## <a name="remarks"></a>Comentarios  
 *Origen* puede ser:  
  
-   UNA DIRECCIÓN URL. Si el protocolo para la dirección URL es http, se invocará el proveedor de Internet de forma predeterminada. Si la dirección URL apunta a un nodo que contiene una secuencia de comandos ejecutable (como un. Página ASP), un **registro** que contiene el origen en lugar de ejecutado contenido se abre de forma predeterminada. Use la *opciones* argumento para modificar este comportamiento.  
  
-   Un **registro** objeto. Un **registro** abre el objeto de otro **registro** duplicará el original **registro** objeto.  
  
-   Un **comando** objeto. Abierto **registro** objeto representa la fila devuelta mediante la ejecución de la **comando**. Si los resultados contienen más de una sola fila, el contenido de la primera fila se coloca en el registro y es posible que se agrega un error a la **errores** colección.  
  
-   Una instrucción SELECT de SQL. Abierto **registro** objeto representa la fila devuelta por la ejecución del contenido de la cadena. Si los resultados contienen más de una sola fila, el contenido de la primera fila se coloca en el registro y es posible que se agrega un error a la **errores** colección.  
  
-   Un nombre de tabla.  
  
 Si el **registro** objeto representa una entidad que no se puede tener acceso con una dirección URL (por ejemplo, una fila de un **Recordset** derivado de una base de datos), los valores de la [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)propiedad y el campo que se obtiene acceso con el **adRecordURL** constante son null.  
  
> [!NOTE]
>  Las direcciones URL con el esquema http, se invocarán automáticamente el [proveedor Microsoft OLE DB para la publicación en Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Para obtener más información, consulte [absoluto y las direcciones URL relativas](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Método Open (conexión de ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Método Open (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Método Open (Stream de ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Método OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
