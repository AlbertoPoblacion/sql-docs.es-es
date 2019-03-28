---
title: sp_describe_undeclared_parameters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_undeclared_parameters
- sp_describe_undeclared_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_undeclared_parameters
ms.assetid: 6f016da6-dfee-4228-8b0d-7cd8e7d5a354
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5a35880dd299cc9eff81643dd5d955101c5eec68
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532487"
---
# <a name="spdescribeundeclaredparameters-transact-sql"></a>sp_describe_undeclared_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Devuelve un conjunto de resultados que contiene metadatos sobre parámetros no declarados en un [!INCLUDE[tsql](../../includes/tsql-md.md)] por lotes. Considera cada parámetro que se usa en el  **\@tsql** por lotes, pero no se declara en  **\@params**. Se devuelve un conjunto de resultados que contiene una fila para cada parámetro, con la información de tipo deducida para dicho parámetro. El procedimiento devuelve un resultado vacío se establece si el  **\@tsql** lote de entrada no tiene ningún parámetro excepto los declarados en  **\@params**.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```sql
  
sp_describe_undeclared_parameters   
    [ @tsql = ] 'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' data type ] [, ...n]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ \@tsql = ] 'Transact-SQL\_batch'` Uno o más [!INCLUDE[tsql](../../includes/tsql-md.md)] instrucciones. *Transact-SQL_batch* puede ser **nvarchar (**_n_**)** o **nvarchar (max)**.  
  
`[ \@params = ] N'parameters'` \@params proporciona una cadena de declaración para los parámetros para el [!INCLUDE[tsql](../../includes/tsql-md.md)] funciona por lotes, de forma similar a la forma de sp_executesql. *Parámetros* puede ser **nvarchar (**_n_**)** o **nvarchar (max)**.  
  
 Es una cadena que contiene las definiciones de todos los parámetros que se han incrustado en *Transact SQL_batch*. La cadena debe ser una constante Unicode o una variable Unicode. Cada definición de parámetro se compone de un nombre de parámetro y un tipo de datos. n es un marcador de posición que indica definiciones de parámetros adicionales. Si la instrucción Transact-SQL o el lote en la instrucción no contiene parámetros, \@params no es necesario. El valor predeterminado de este parámetro es NULL.  
  
 Datatype  
 El tipo de datos del parámetro.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **sp_describe_undeclared_parameters** siempre devuelve devuelve el estado de cero si se ejecuta correctamente. Si el procedimiento produce un error y se llama al procedimiento como un RPC, el estado de retorno se rellena con el tipo de error como se describe en la columna error_type de sys.dm_exec_describe_first_result_set. Si se llama al procedimiento desde [!INCLUDE[tsql](../../includes/tsql-md.md)], el valor devuelto siempre es cero, incluso si se produce un error.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 **sp_describe_undeclared_parameters** devuelve el siguiente conjunto de resultados.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int no NULL**|Contiene la posición ordinal del parámetro en el conjunto de resultados. La posición del primer parámetro se especificará como 1.|  
|**Nombre**|**sysname no NULL**|Contiene el nombre del parámetro.|  
|**suggested_system_type_id**|**int no NULL**|Contiene el **system_type_id** del tipo de datos del parámetro como se especifica en sys.types.<br /><br /> Para los tipos CLR, aunque el **system_type_name** columna devolverá NULL, esta columna devolverá el valor 240.|  
|**suggested_system_type_name**|**nvarchar (256) NULL**|Contiene el nombre del tipo de datos. Incluye los argumentos (como length, precision y scale) especificados para el tipo de datos del parámetro. Si el tipo de datos es un tipo de alias definido por el usuario, el tipo de sistema subyacente se especifica aquí. Si es un tipo de datos definido por el usuario de CLR, NULL se devuelve en esta columna. Si no se puede deducir el tipo del parámetro, se devuelve NULL.|  
|**suggested_max_length**|**smallint no NULL**|Consulte sys.columns. para **max_length** descripción de la columna.|  
|**suggested_precision**|**tinyint no NULL**|Consulte sys.columns. para obtener la descripción de la columna de precisión.|  
|**suggested_scale**|**tinyint no NULL**|Consulte sys.columns. para obtener la descripción de la columna de escala.|  
|**suggested_user_type_id**|**int NULL**|Para los tipos de alias y CLR, contiene el user_type_id del tipo de datos de la columna tal y como se especifica en sys.types. De lo contrario, es NULL.|  
|**suggested_user_type_database**|**sysname NULL**|Para los tipos de alias y CLR, contiene el nombre de la base de datos en la que se define el tipo. De lo contrario, es NULL.|  
|**suggested_user_type_schema**|**sysname NULL**|Para los tipos de alias y CLR, contiene el nombre del esquema en el que se define el tipo. De lo contrario, es NULL.|  
|**suggested_user_type_name**|**sysname NULL**|Para los tipos de alias y CLR, contiene el nombre del tipo. De lo contrario, es NULL.|  
|**suggested_assembly_qualified_type_name**|**nvarchar (4000) NULL**|Para los tipos de CLR, devuelve el nombre del ensamblado y la clase que define el tipo. De lo contrario, es NULL.|  
|**suggested_xml_collection_id**|**int NULL**|Contiene el xml_collection_id del tipo de datos del parámetro tal como se especifica en sys.columns. Esta columna devolverá NULL si el tipo devuelto no está asociado a una colección de esquema XML.|  
|**suggested_xml_collection_database**|**sysname NULL**|Contiene la base de datos en la que se define la colección de esquema XML asociado a este tipo. Esta columna devolverá NULL si el tipo devuelto no está asociado a una colección de esquema XML.|  
|**suggested_xml_collection_schema**|**sysname NULL**|Contiene el esquema en el que se define la colección de esquema XML asociado a este tipo. Esta columna devolverá NULL si el tipo devuelto no está asociado a una colección de esquema XML.|  
|**suggested_xml_collection_name**|**sysname NULL**|Contiene el nombre de la colección de esquema XML asociado a este tipo. Esta columna devolverá NULL si el tipo devuelto no está asociado a una colección de esquema XML.|  
|**suggested_is_xml_document**|**bit NOT NULL**|Devuelve 1 si el tipo que se va a devolver es XML y se garantiza que es un documento XML. De lo contrario, devuelve 0.|  
|**suggested_is_case_sensitive**|**bit NOT NULL**|Devuelve 1 si la columna es de un tipo de cadena con distinción entre mayúsculas y minúsculas, y 0 en caso contrario.|  
|**suggested_is_fixed_length_clr_type**|**bit NOT NULL**|Devuelve 1 si la columna es de un tipo CLR de longitud fija y 0 en caso contrario.|  
|**suggested_is_input**|**bit NOT NULL**|Devuelve 1 si el parámetro se utiliza en cualquier otro lugar que no sea el lado izquierdo de una asignación. De lo contrario, devuelve 0.|  
|**suggested_is_output**|**bit NOT NULL**|Devuelve 1 si el parámetro se utiliza en el lado izquierdo de una asignación o se pasa a un parámetro de salida de un procedimiento almacenado. De lo contrario, devuelve 0.|  
|**formal_parameter_name**|**sysname NULL**|Si el parámetro es un argumento para un procedimiento almacenado o una función definida por el usuario, devuelve el nombre del parámetro formal correspondiente. En caso contrario, devuelve NULL.|  
|**suggested_tds_type_id**|**int no NULL**|Para uso interno.|  
|**suggested_tds_length**|**int no NULL**|Para uso interno.|  
  
## <a name="remarks"></a>Comentarios  
 **sp_describe_undeclared_parameters** siempre devuelve devuelve el estado de cero.  
  
 El uso más común es cuando se proporciona a una aplicación una instrucción de [!INCLUDE[tsql](../../includes/tsql-md.md)] que podría contener parámetros y debe procesarlos de alguna manera. Un ejemplo es una interfaz de usuario (como ODBCTest o RowsetViewer) donde el usuario proporciona una consulta con la sintaxis de parámetros ODBC. La aplicación debe detectar el número de parámetros dinámicamente y pedir confirmación al usuario para cada uno.  
  
 Otro ejemplo es cuando no hay datos proporcionados por el usuario y una aplicación debe recorrer los parámetros y obtener los datos para ellos desde alguna otra ubicación (como una tabla). En este caso, la aplicación no tiene que pasar toda la información de parámetros a la vez. En su lugar, la aplicación puede obtener toda la información de parámetros del proveedor y obtener el propio dato de la tabla. Uso de código **sp_describe_undeclared_parameters** es más genérico y es menos probable que requieren la modificación si la estructura de datos los cambios más tarde.  
  
 **sp_describe_undeclared_parameters** devuelve un error en cualquiera de los casos siguientes.  
  
-   Si la entrada \@tsql no es válido [!INCLUDE[tsql](../../includes/tsql-md.md)] por lotes. Validez se determina analizando el [!INCLUDE[tsql](../../includes/tsql-md.md)] por lotes. Los errores causados por el lote durante la optimización de consultas o durante la ejecución no se consideran al determinar si el [!INCLUDE[tsql](../../includes/tsql-md.md)] por lotes es válido.  
  
-   Si \@params no es NULL y contiene una cadena que no es una cadena de declaración sintácticamente válida para los parámetros, o si contiene una cadena que declara algún parámetro más de una vez.  
  
-   Si la entrada [!INCLUDE[tsql](../../includes/tsql-md.md)] lote declara una variable local del mismo nombre como un parámetro declarado en \@params.  
  
- Si la instrucción hace referencia a tablas temporales.
  
 Si \@tsql no tiene parámetros, excepto los declarados en \@params, el procedimiento devuelve un conjunto de resultados vacío.  
  
## <a name="parameter-selection-algorithm"></a>Algoritmo de selección de parámetros  
 En una consulta con parámetros no declarados, la deducción de su tipo de datos se realiza en tres pasos.  
  
 **Paso 1**  
  
 El primer paso de la deducción del tipo de datos de una consulta con parámetros no declarados es encontrar los tipos de datos de todas las subexpresiones cuyos tipos de datos no dependen de los parámetros no declarados. El tipo se puede determinar para las siguientes expresiones:  
  
-   Columnas, constantes, variables y parámetros declarados.  
  
-   Los resultados de una llamada a una función definida por el usuario (UDF).  
  
-   Una expresión con tipos de datos que no dependen de los parámetros no declarados para todas las entradas.  
  
 Por ejemplo, considere la consulta `SELECT dbo.tbl(@p1) + c1 FROM t1 WHERE c2 = @p2 + 2`. Las expresiones dbo.tbl (\@p1) + c1 y c2 tienen tipos de datos y expresión \@p1 y \@p2 + 2 no.  
  
 Después de este paso, si alguna expresión (excepto una llamada a un UDF) tiene dos argumentos sin tipos de datos, la deducción del tipo da un error. Por ejemplo, todo lo siguiente produce errores:  
  
```sql
SELECT * FROM t1 WHERE @p1 = @p2  
SELECT * FROM t1 WHERE c1 = @p1 + @p2  
SELECT * FROM t1 WHERE @p1 = SUBSTRING(@p2, 2, 3)  
```  
  
 En el siguiente ejemplo no se genera un error:  
  
```sql
SELECT * FROM t1 WHERE @p1 = dbo.tbl(c1, @p2, @p3)  
```
  
 **Paso 2**  
  
 Para un parámetro dado no declarado \@p, el algoritmo de deducción de tipo busca la expresión más E (\@p) que contiene \@p y es uno de los siguientes:  
  
-   Un argumento de un operador de asignación o comparación.  
  
-   Un argumento de una función definida por el usuario (incluido un UDF con valor de tabla), procedimiento o método.  
  
-   Un argumento para un **valores** cláusula de una **insertar** instrucción.  
  
-   Un argumento para un **CAST** o **convertir**.  
  
 El algoritmo de deducción de tipo busca un tipo de datos de destino TT (\@p) para E (\@p). Los tipos de datos de destino de los ejemplos anteriores son los siguientes:  
  
-   El tipo de datos del otro lado de la comparación o asignación.  
  
-   El tipo de datos declarado del parámetro al que se pasa este argumento.  
  
-   El tipo de datos de la columna en la que se inserta este valor.  
  
-   El tipo de datos al que la instrucción se va a convertir.  
  
 Por ejemplo, considere la consulta `SELECT * FROM t WHERE @p1 = dbo.tbl(@p2 + c1)`. A continuación, E (\@p1) = \@p1, E (\@p2) = \@p2 + c1, TT (\@p1) es el tipo de datos devuelto declarado de dbo.tbl y TT (\@p2) es el tipo de datos de parámetro declarado de dbo.tbl.  
  
 Si \@p no se encuentra en ninguna expresión enumerada al principio del paso 2, el algoritmo de deducción de tipo determina que E (\@p) es la expresión escalar más grande que contiene \@p y el algoritmo de deducción de tipo no lo hace proceso de un tipo de datos de destino TT (\@p) para E (\@p). Por ejemplo, si la consulta es SELECT `@p + 2` , a continuación, E (\@p) = \@p + 2, y no hay ningún TT (\@p).  
  
 **Paso 3**  
  
 Ahora que E (\@p) y TT (\@p) son identificado, el algoritmo de deducción de tipo deduce un tipo de datos para \@p en una de las dos maneras siguientes:  
  
-   Deducción simple  
  
     Si E (\@p) = \@p y TT (\@p), es decir, si existe \@p es directamente un argumento a una de las expresiones que aparece al principio del paso 2, el algoritmo de deducción de tipo deduce el tipo de datos de \@p para ser TT () \@p). Por ejemplo:  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p1 AND @p2 = dbo.tbl(@p3)  
    ```  
  
     Tipo de datos de \@p1, \@p2, y \@p3 será el tipo de datos de c1, el tipo de datos devuelto de dbo.tbl, y el parámetro de tipo de datos para el dbo.tbl respectivamente.  
  
     Como caso especial, si \@p es un argumento para un \<, >, \<=, o > = (operador), no se aplican las reglas de deducción simple. El algoritmo de deducción de tipo utilizará las reglas de deducción generales explicadas en la sección siguiente. Por ejemplo, si c1 es una columna del tipo de datos char(30), considere las siguientes dos consultas:  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p  
    SELECT * FROM t WHERE c1 > @p  
    ```  
  
     En el primer caso, el algoritmo de deducción de tipo deduce **char (30)** como tipo de datos de \@p según las reglas anteriores de este tema. En el segundo caso, el algoritmo de deducción de tipo deduce **varchar (8000)** según las reglas de deducción generales en la sección siguiente.  
  
-   Deducción general  
  
     Si la deducción simple no se aplica, los siguientes tipos de datos se consideran para los parámetros no declarados:  
  
    -   Tipos de datos enteros (**bit**, **tinyint**, **smallint**, **int**, **bigint**)  
  
    -   Los tipos de datos Money (**smallmoney**, **dinero**)  
  
    -   Tipos de datos de punto flotante (**float**, **real**)  
  
    -   **numeric (38, 19)** -no se consideran otros tipos de datos decimal o numérico.  
  
    -   **varchar (8000)**, **varchar (max)**, **nvarchar (4000)**, y **nvarchar (max)** : otros tipos de datos de cadena (como **texto**, **char (8000)**, **nvarchar (30)**, etc.) no se consideran.  
  
    -   **varbinary (8000)** y **varbinary (max)** -otros tipos de datos binarios no se consideran (como **imagen**, **binary(8000)**, **varbinary (30)** , etcetera.).  
  
    -   **fecha**, **Time (7)**, **smalldatetime**, **datetime**, **datetime2 (7)**, **DateTimeOffset (7)**  - Otra fecha y hora como tipos, **time(4)**, no se consideran.  
  
    -   **sql_variant**  
  
    -   **xml**  
  
    -   Tipos CLR definido por el sistema (**hierarchyid**, **geometría**, **geography**)  
  
    -   Tipos definidos por el usuario CLR  
  
### <a name="selection-criteria"></a>Criterios de selección  
 De los tipos de datos candidatos, se rechaza cualesquiera que invalidara la consulta. De los tipos de datos candidatos restantes, el algoritmo de deducción de tipo selecciona uno según las siguientes reglas.  
  
1.  El tipo de datos que genera el menor número de conversiones implícitas en E (\@p) está seleccionado. Si un tipo de datos determinado genera un tipo de datos para E (\@p) que es diferente de TT (\@p), el algoritmo de deducción de tipo lo considera una conversión implícita adicional del tipo de datos de E (\@p) a TT (\@p).  
  
     Por ejemplo:  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_Int + @p  
    ```  
  
     En este caso, E (\@p) es Col_Int + \@p y TT (\@p) es **int**. **int** se elige para \@p porque no genera ninguna conversión implícita. Cualquier otra opción de tipo de datos genera al menos una conversión implícita.  
  
2.  Si hay varios tipos de datos que coinciden en el número menor de conversiones, se utiliza el tipo de datos con mayor prioridad. Por ejemplo  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_smallint + @p  
    ```  
  
     En este caso, **int** y **smallint** generan una conversión. Otros tipos de datos generan más de una conversión. Dado que **int** tiene prioridad sobre **smallint**, **int** se usa para \@p. Para obtener más información sobre la precedencia de tipo de datos, vea [precedencia de tipo de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
     Esta regla solo se aplica si hay una conversión implícita entre cada tipo de datos que coincide según la regla 1 y el tipo de datos con la precedencia máxima. Si no hay ninguna conversión implícita, la deducción del tipo de datos no se puede realizar y genera un error. Por ejemplo, en la consulta `SELECT @p FROM t`, se produce un error de deducción de tipos de datos porque cualquier tipo de datos para \@p sería igual de bueno. Por ejemplo, no hay ninguna conversión implícita de **int** a **xml**.  
  
3.  Si dos tipos de datos similares cumplen la regla 1, por ejemplo **varchar (8000)** y **varchar (max)**, menor será el tipo de datos (**varchar (8000)**) se elige. El mismo principio se aplica a **nvarchar** y **varbinary** tipos de datos.  
  
4.  Para los fines de la regla 1, el algoritmo de deducción de tipo prefiere ciertas conversiones sobre otras. Las conversiones, en orden de mejor a peor, son:  
  
    1.  Conversión entre el mismo tipo de datos básico de longitud diferente.  
  
    2.  Conversión entre la versión de longitud fija y variable de longitud de los mismos tipos de datos (por ejemplo, **char** a **varchar**).  
  
    3.  Conversión entre **NULL** y **int**.  
  
    4.  Cualquier otra conversión.  
  
 Por ejemplo, para la consulta `SELECT * FROM t WHERE [Col_varchar(30)] > @p`, **varchar (8000)** se elige porque la conversión (a) es mejor. Para la consulta `SELECT * FROM t WHERE [Col_char(30)] > @p`, **varchar (8000)** todavía se elige porque provoca una conversión de tipos (b) y porque otra opción (como **varchar (4000)**) produciría una conversión de tipo (d).  
  
 Como último ejemplo, dada una consulta `SELECT NULL + @p`, **int** se elige para \@p porque produce una conversión de tipos (c).  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso para ejecutar el \@argumento tsql.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve información como el tipo de datos esperado para los parámetros `@id` e `@name` no declarados.  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR name = @name'  
  
```  
  
 Cuando se proporciona el parámetro `@id` como una referencia `@params`, el parámetro `@id` se omite del conjunto de resultados y solo se describe el parámetro `@name`.  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR NAME = @name',  
@params = N'@id int'  
  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)
