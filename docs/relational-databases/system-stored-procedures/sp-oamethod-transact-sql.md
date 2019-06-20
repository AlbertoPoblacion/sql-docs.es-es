---
title: sp_OAMethod (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAMethod
- sp_OAMethod_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAMethod
ms.assetid: 1dfaebe2-c7cf-4041-a586-5d04faf2e25e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25eccb27b75028fdebafaa7a855137946465676b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65450112"
---
# <a name="spoamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Llama a un método de un objeto OLE.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>Argumentos  
 *objecttoken*  
 Es el token de un objeto OLE creado anteriormente mediante el uso de **sp_OACreate**.  
  
 *MethodName*  
 Es el nombre de método del objeto OLE al que se llamará.  
  
 _ReturnValue_**salida**  
 Es el valor devuelto del método del objeto OLE. Si se especifica, debe ser una variable local del tipo de datos adecuado.  
  
 Si el método devuelve un valor único, especifique una variable local para *returnvalue*, que devuelve el método devuelve el valor en la variable local o que no se especifica *returnvalue*, que devuelve el método devuelve el valor al cliente como un conjunto de resultados de una sola columna, fila única.  
  
 Si el método devuelve el valor es un objeto OLE, *returnvalue* debe ser una variable local del tipo de datos **int**. En la variable local se almacena un token de objeto que se puede utilizar con otros procedimientos almacenados de OLE Automation.  
  
 Cuando el método de valor devuelto es una matriz, si *returnvalue* se especifica, se establece en NULL.  
  
 Se genera un error si se da uno de los casos siguientes:  
  
-   *ReturnValue* se especifica, pero el método no devuelve un valor.  
  
-   El método devuelve una matriz con más de dos dimensiones.  
  
-   El método devuelve una matriz como parámetro de salida.  
  
`[ _@parametername = ] parameter[ OUTPUT ]` Es un parámetro de método. Si se especifica, *parámetro* debe ser un valor de tipo de datos adecuado.  
  
 Para obtener el valor devuelto de un parámetro de salida, *parámetro* debe ser una variable local del tipo de datos adecuado, y **salida** debe especificarse. Si se especifica un parámetro constante, o si **salida** no se especifica, todos de retorno se omite el valor de un parámetro de salida.  
  
 Si se especifica, *parametername* debe ser el nombre de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] parámetro con nombre. Tenga en cuenta que **@** _parametername_is no un [!INCLUDE[tsql](../../includes/tsql-md.md)] variable local. El signo de arroba ( **@** ) se quita, y *parametername*se pasa al objeto OLE como el nombre del parámetro. Todos los parámetros con nombre deben especificarse después de especificar todos los parámetros de posición.  
  
 *n*  
 Es un marcador de posición que indica que se pueden especificar varios parámetros.  
  
> [!NOTE]
>  *@parametername* puede ser un parámetro con nombre porque forma parte del método especificado y se pasa al objeto. Los demás parámetros de este procedimiento almacenado se especifican por la posición, no por el nombre.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o un valor distinto de cero (error) que es el valor entero del HRESULT devuelto por el objeto de OLE Automation.  
  
 Para obtener más información sobre los códigos de retorno HRESULT, [OLE Automation códigos de retorno e información de Error](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Si el valor devuelto del método es una matriz con una o dos dimensiones, se devuelve la matriz al cliente como un conjunto de resultados:  
  
-   Se devuelve al cliente una matriz unidimensional como conjunto de resultados de fila única con tantas columnas como elementos tenga la matriz. Es decir, la matriz se devuelve como (columnas).  
  
-   Se devuelve al cliente una matriz bidimensional como conjunto de resultados con tantas columnas como elementos haya en la primera dimensión de la matriz y con tantas filas como elementos haya en la segunda dimensión de la matriz. En otras palabras, la matriz se devuelve como (columnas, filas).  
  
 Cuando el valor devuelto de una propiedad o valor devuelto de método es una matriz, **sp_OAGetProperty** o **sp_OAMethod** devuelve un conjunto de resultados para el cliente. (Los parámetros de salida del método no pueden ser matrices.) Estos procedimientos recorren todos los valores de datos de la matriz para determinar los tipos de datos y las longitudes de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adecuados para cada columna del conjunto de resultados. Para una columna determinada, estos procedimientos utilizan el tipo y la longitud de datos necesarios para representar todos los valores de los datos de la columna.  
  
 Cuando todos los valores de datos de una columna comparten el mismo tipo de datos, se utiliza ese tipo para toda la columna. Cuando los valores de datos de una columna utilizan tipos de datos diferentes, el tipo de datos de toda la columna se elige como se muestra a continuación.  
  
||INT|FLOAT|money|datetime|varchar|NVARCHAR|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Comentarios  
 También puede usar **sp_OAMethod** para obtener un valor de propiedad.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer a la **sysadmin** rol fijo de servidor o permiso de ejecución directamente en este procedimiento almacenado. `Ole Automation Procedures` configuración de debe ser **habilitado** utilizar ningún procedimiento del sistema relacionadas con la automatización OLE.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-calling-a-method"></a>A. Llamar a un método  
 El ejemplo siguiente se llama el `Connect` método creado previamente **SQLServer** objeto.  
  
```  
EXEC @hr = sp_OAMethod @object, 'Connect', NULL, 'my_server',  
    'my_login', 'my_password';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
### <a name="b-getting-a-property"></a>b. Obtener una propiedad  
 En el ejemplo siguiente se obtiene el `HostName` propiedad (de creado previamente **SQLServer** objeto) y lo almacena en una variable local.  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAMethod @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
PRINT @property;  
```  
  
## <a name="see-also"></a>Vea también  
 [OLE Automation procedimientos almacenados &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Ejemplo de script de automatización OLE](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
