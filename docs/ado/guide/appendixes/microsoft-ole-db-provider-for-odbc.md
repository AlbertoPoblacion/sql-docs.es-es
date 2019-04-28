---
title: Proveedor Microsoft OLE DB para ODBC | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e75b79934022743ba806722427dd37ab733bc2f2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853331"
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Proveedor Microsoft OLE DB para ODBC Introducción
Para un programador de ADO o RDS, un mundo ideal sería uno de los datos de cada origen expone una interfaz OLE DB, por lo que podría llamar ADO directamente en el origen de datos. Aunque cada vez más proveedores de base de datos están implementando las interfaces OLE DB, algunos orígenes de datos aún no están expuestos de este modo. Sin embargo, la mayoría de los sistemas DBMS en uso hoy en día puede obtenerse a través de ODBC.

 Controladores ODBC están disponibles para todos los principales DBMS en uso hoy en día, incluidos Microsoft SQL Server, Microsoft Access (motor de base de datos Microsoft Jet) y Microsoft FoxPro, además de los productos de base de datos que no sean de Microsoft, como Oracle.

 Sin embargo, el proveedor ODBC de Microsoft, permite que ADO para conectarse a cualquier origen de datos ODBC. El proveedor es de subprocesamiento libre y está habilitado para Unicode.

 El proveedor admite las transacciones, aunque diferentes motores DBMS ofrecen diferentes tipos de compatibilidad con transacciones. Por ejemplo, Microsoft Access admite transacciones anidadas hasta cinco niveles de profundidad.

 Éste es el proveedor predeterminado para ADO y se admiten todas las propiedades que dependen del proveedor ADO y métodos.

## <a name="connection-string-parameters"></a>Parámetros de cadena de conexión
 Para conectarse a este proveedor, establezca el **proveedor =** argumento de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propiedad:

```
MSDASQL
```

 Leer el [proveedor](../../../ado/reference/ado-api/provider-property-ado.md) propiedad devolverá también esta cadena.

## <a name="typical-connection-string"></a>Cadena de conexión típica
 Una cadena de conexión típica para este proveedor es:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 La cadena consta de estas palabras clave:

|Palabra clave|Descripción|
|-------------|-----------------|
|**Proveedor**|Especifica el proveedor OLE DB para ODBC.|
|**DSN**|Especifica el nombre del origen de datos.|
|**UID**|Especifica el nombre de usuario.|
|**PWD**|Especifica la contraseña del usuario.|
|**Dirección URL**|Especifica la dirección URL de un archivo o directorio publicado en una carpeta Web.|

 Dado que este es el proveedor predeterminado para ADO, si se omite el **proveedor =** parámetro de la cadena de conexión ADO intentará establecer una conexión con este proveedor.

> [!NOTE]
>  Si se conecta a un proveedor de origen de datos que admite la autenticación de Windows, debe especificar **Trusted_Connection = yes** o **Integrated Security = SSPI** en lugar de Id. de usuario y contraseña información de la cadena de conexión.

 El proveedor no admite los parámetros de conexión específico además de los definidos por ADO. Sin embargo, el proveedor pasará los parámetros de conexión que no son de ADO para el Administrador de controladores ODBC.

 Dado que se puede omitir el **proveedor** parámetro, por lo tanto, puede crear una cadena de conexión de ADO que es idéntica a una cadena de conexión ODBC para el mismo origen de datos. Use los mismos nombres de parámetro (**controlador =**, **base de datos =**, **DSN =**, y así sucesivamente), valores y la sintaxis como se haría al componer una cadena de conexión ODBC. Puede conectar con o sin un nombre de origen de datos predefinidos (DSN) o un FileDSN.

## <a name="syntax-with-a-dsn-or-filedsn"></a>Sintaxis con un DSN o FileDSN:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>Sintaxis sin un DSN (conexión sin DSN):

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>Comentarios
 Si usa un **DSN** o **FileDSN**, debe definirse mediante el Administrador de origen de datos ODBC en el Panel de Control de Windows. En Microsoft Windows 2000, el Administrador de ODBC se encuentra en Herramientas administrativas. En versiones anteriores de Windows, el icono de administrador de ODBC se denomina **ODBC 32-bit** o simplemente **ODBC**.

 Como alternativa a la configuración de un **DSN**, puede especificar el controlador ODBC (**controlador =**), como "SQL Server"; el nombre del servidor (**SERVER =**); y el nombre de la base de datos (**Base de datos =**).

 También puede especificar un nombre de cuenta de usuario (**UID =**) y la contraseña para la cuenta de usuario (**PWD =**) en los parámetros específicos de ODBC o en el estándar definidos por ADO *usuario* y *contraseña* parámetros.

 Aunque un **DSN** definición ya especifica una base de datos, puede especificar *un* *base de datos* parámetro además un **DSN** para conectarse para una base de datos diferentes. Es una buena idea incluir siempre *el* *base de datos* cuando use un **DSN**. Esto garantizará que conectarse a la base de datos si otro usuario cambia el parámetro de base de datos predeterminado desde la última la **DSN** definición.

## <a name="provider-specific-connection-properties"></a>Propiedades de conexión específica del proveedor
 El proveedor OLE DB para ODBC agrega varias propiedades para el [propiedades](../../../ado/reference/ado-api/properties-collection-ado.md) colección de la **conexión** objeto. En la tabla siguiente se enumera estas propiedades con el nombre de propiedad de OLE DB correspondiente entre paréntesis.

|Nombre de la propiedad|Descripción|
|-------------------|-----------------|
|Procedimientos accesible (KAGPROP_ACCESSIBLEPROCEDURES)|Indica si el usuario tiene acceso a los procedimientos almacenados.|
|Tablas accesibles (KAGPROP_ACCESSIBLETABLES)|Indica si el usuario tiene permiso para ejecutar instrucciones SELECT en las tablas de base de datos.|
|Instrucciones activas (KAGPROP_ACTIVESTATEMENTS)|Indica el número de identificadores que puede admitir un controlador ODBC en una conexión.|
|Nombre del controlador (KAGPROP_DRIVERNAME)|Indica el nombre de archivo del controlador ODBC.|
|Versión del controlador ODBC (KAGPROP_DRIVERODBCVER)|Indica la versión de ODBC que admite este controlador.|
|Uso de archivos (KAGPROP_FILEUSAGE)|Indica cómo trata un archivo en un origen de datos; el controlador como una tabla o como un catálogo.|
|Al igual que la cláusula de Escape (KAGPROP_LIKEESCAPECLAUSE)|Indica si el controlador admite la definición y uso de un carácter de escape para el carácter de porcentaje (%) y subrayado (_) de caracteres en el predicado LIKE de una cláusula WHERE.|
|Número máximo de columnas en Group By (KAGPROP_MAXCOLUMNSINGROUPBY)|Indica el número máximo de columnas que pueden aparecer en la cláusula GROUP BY de una instrucción SELECT.|
|Número máximo de columnas de índice (KAGPROP_MAXCOLUMNSININDEX)|Indica el número máximo de columnas que puede incluirse en un índice.|
|Número máximo de columnas de Order By (KAGPROP_MAXCOLUMNSINORDERBY)|Indica el número máximo de columnas que pueden aparecer en la cláusula ORDER BY de una instrucción SELECT.|
|Número máximo de columnas en (KAGPROP_MAXCOLUMNSINSELECT), seleccione|Indica el número máximo de columnas que pueden aparecer en la parte SELECT de una instrucción SELECT.|
|Número máximo de columnas de tabla (KAGPROP_MAXCOLUMNSINTABLE)|Indica el número máximo de columnas permitido en una tabla.|
|Funciones numéricas (KAGPROP_NUMERICFUNCTIONS)|Indica qué funciones numéricas son compatibles con el controlador ODBC. Para obtener una lista de nombres de función y los valores asociados utilizados en esta máscara de bits, consulte [Apéndice E: Funciones escalares](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), en la documentación de ODBC.|
|Capacidades de combinación externa (KAGPROP_OJCAPABILITY)|Indica los tipos de combinaciones externas compatible con el proveedor.|
|Combinaciones externas (KAGPROP_OUTERJOINS)|Indica si el proveedor admite combinaciones externas.|
|Caracteres especiales (KAGPROP_SPECIALCHARACTERS)|Indica qué caracteres tienen un significado especial para el controlador ODBC.|
|Procedimientos almacenados (KAGPROP_PROCEDURES)|Indica si los procedimientos almacenados están disponibles para su uso con este controlador ODBC.|
|Funciones de cadena (KAGPROP_STRINGFUNCTIONS)|Indica qué funciones de cadena son compatibles con el controlador ODBC. Para obtener una lista de nombres de función y los valores asociados utilizados en esta máscara de bits, consulte [Apéndice E: Funciones escalares](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), en la documentación de ODBC.|
|Funciones del sistema (KAGPROP_SYSTEMFUNCTIONS)|Indica qué funciones del sistema son compatibles con el controlador ODBC. Para obtener una lista de nombres de función y los valores asociados utilizados en esta máscara de bits, consulte [Apéndice E: Funciones escalares](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), en la documentación de ODBC.|
|Funciones de fecha y hora (KAGPROP_TIMEDATEFUNCTIONS)|Indica las funciones de fecha y hora admitidas por el controlador ODBC. Para obtener una lista de nombres de función y los valores asociados utilizados en esta máscara de bits, consulte [Apéndice E: Funciones escalares](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), en la documentación de ODBC.|
|Compatibilidad con la gramática SQL (KAGPROP_ODBCSQLCONFORMANCE)|Indica la gramática SQL que admite el controlador ODBC.|

## <a name="provider-specific-recordset-and-command-properties"></a>Conjunto de registros específicos del proveedor y las propiedades de comando
 El proveedor OLE DB para ODBC agrega varias propiedades para el **propiedades** colección de la **Recordset** y **comando** objetos. En la tabla siguiente se enumera estas propiedades con el nombre de propiedad de OLE DB correspondiente entre paréntesis.

|Nombre de la propiedad|Descripción|
|-------------------|-----------------|
|Las actualizaciones, eliminaciones o inserciones (KAGPROP_QUERYBASEDUPDATES) basados en consultas|Indica si se pueden realizar actualizaciones, eliminaciones e inserciones mediante consultas SQL.|
|Tipo de simultaneidad ODBC (KAGPROP_CONCURRENCY)|Indica el método utilizado para reducir los posibles problemas causados por dos usuarios intentan tener acceso a los mismos datos desde el origen de datos al mismo tiempo.|
|Accesibilidad BLOB en el cursor de solo avance (KAGPROP_BLOBSONFOCURSOR)|Indica si BLOB **campos** puede obtenerse al usar un cursor de solo avance.|
|Incluir SQL_FLOAT, SQL_DOUBLE y SQL_REAL en cláusulas WHERE de consulta por ejemplo (KAGPROP_INCLUDENONEXACT)|Indica si se pueden incluir valores SQL_FLOAT, SQL_DOUBLE y SQL_REAL en una cláusula WHERE de consulta por ejemplo.|
|Posición en la última fila después de la inserción (KAGPROP_POSITIONONNEWROW)|Indica que una vez se ha insertado un nuevo registro en una tabla, será la última fila de la tabla proceden de la fila actual.|
|IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)|Indica si el **IRowsetChange** interfaz proporciona compatibilidad con la información extendida.|
|Tipo de Cursor ODBC (KAGPROP_CURSOR)|Indica el tipo de cursor utilizado por el **Recordset**.|
|Generar un conjunto de filas que se puede serializar (KAGPROP_MARSHALLABLE)|Indica que el controlador ODBC genera un conjunto de registros que se puede calcular referencias|

## <a name="command-text"></a>Texto de comando
 Cómo usar el [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto depende en gran medida el origen de datos y qué tipo de consulta o instrucción de comando que acepte.

 ODBC proporciona una sintaxis específica para llamar a procedimientos almacenados. Para el [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propiedad de un **comando** objeto, el *CommandText* argumento para el **Execute** método en un [ Conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto, o el *origen* argumento para el **abierto** método en un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto, pasa una cadena con esta sintaxis:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , ... ]] ) ] }"
```

 ¿Cada **?** hace referencia a un objeto en el [parámetros](../../../ado/reference/ado-api/parameters-collection-ado.md) colección. ¿La primera **?** ¿referencias **parámetros**(0), la próxima **?** referencias **parámetros**(1), y así sucesivamente.

 Las referencias de parámetro son opcionales y dependen de la estructura del procedimiento almacenado. Si desea llamar a un procedimiento almacenado que no se define parámetros, la cadena sería similar al siguiente:

```
"{ call procedure }"
```

 Si tiene dos parámetros de consulta, la cadena sería similar al siguiente:

```
"{ call procedure ( ?, ? ) }"
```

 Si el procedimiento almacenado devolverá un valor, el valor devuelto se trata como otro parámetro. Si no tiene ningún parámetro de consulta, pero tiene un valor devuelto, la cadena sería similar al siguiente:

```
"{ ? = call procedure }"
```

 Por último, si tiene un valor devuelto y dos parámetros de consulta, la cadena sería similar al siguiente:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Comportamiento del conjunto de registros
 Las siguientes tablas enumeran los métodos estándar de ADO y propiedades disponibles en un **Recordset** objeto abierto con este proveedor.

 Para obtener más información acerca de **Recordset** comportamiento para la configuración del proveedor, ejecute el [admite](../../../ado/reference/ado-api/supports-method.md) método y enumerar los **propiedades** colección de la **Recordset** para determinar si están presentes las propiedades dinámicas específicas del proveedor.

 Disponibilidad de ADO estándar **Recordset** propiedades:

|Property|ForwardOnly|Dinámico|Keyset|Estático|
|--------------|-----------------|-------------|------------|------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|no disponible|no disponible|lectura/escritura|lectura/escritura|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|no disponible|no disponible|lectura/escritura|lectura/escritura|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|solo lectura|solo lectura|solo lectura|solo lectura|
|[Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md)|no disponible|no disponible|lectura/escritura|lectura/escritura|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|solo lectura|solo lectura|solo lectura|solo lectura|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|lectura/escritura|no disponible|solo lectura|solo lectura|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|lectura/escritura|no disponible|solo lectura|solo lectura|
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lectura/escritura|lectura/escritura|lectura/escritura|lectura/escritura|
|[Estado](../../../ado/reference/ado-api/state-property-ado.md)|solo lectura|solo lectura|solo lectura|solo lectura|
|[Estado](../../../ado/reference/ado-api/status-property-ado-recordset.md)|solo lectura|solo lectura|solo lectura|solo lectura|

 El [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) y [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) propiedades son de solo escritura cuando se utiliza ADO con la versión 1.0 del proveedor de Microsoft OLE DB para ODBC.

 Disponibilidad de ADO estándar **Recordset** métodos:

|Método|ForwardOnly|Dinámico|Keyset|Estático|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Sí|Sí|Sí|Sí|
|[Cancelar](../../../ado/reference/ado-api/cancel-method-ado.md)|Sí|Sí|Sí|Sí|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Sí|Sí|Sí|Sí|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Sí|Sí|Sí|Sí|
|[Clon](../../../ado/reference/ado-api/clone-method-ado.md)|No|No|Sí|Sí|
|[Cerrar](../../../ado/reference/ado-api/close-method-ado.md)|Sí|Sí|Sí|Sí|
|[Eliminar](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Sí|Sí|Sí|Sí|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Sí|Sí|Sí|Sí|
|[Mover](../../../ado/reference/ado-api/move-method-ado.md)|Sí|Sí|Sí|Sí|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sí|Sí|Sí|Sí|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|No|Sí|Sí|Sí|
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sí|Sí|Sí|Sí|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|No|Sí|Sí|Sí|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|Sí|Sí|Sí|Sí|
|[Abrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Sí|Sí|Sí|Sí|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Sí|Sí|Sí|Sí|
|[Resync](../../../ado/reference/ado-api/resync-method.md)|No|No|Sí|Sí|
|[Es compatible con](../../../ado/reference/ado-api/supports-method.md)|Sí|Sí|Sí|Sí|
|[Update](../../../ado/reference/ado-api/update-method.md)|Sí|Sí|Sí|Sí|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Sí|Sí|Sí|Sí|

 * No se admite para bases de datos de Microsoft Access.

## <a name="dynamic-properties"></a>Propiedades dinámicas
 El proveedor Microsoft OLE DB para ODBC inserta varias propiedades dinámicas en la **propiedades** colección de los no abierto [conexión](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)y [Comando](../../../ado/reference/ado-api/command-object-ado.md) objetos.

 Las tablas siguientes son un índice cruzado de los nombres de ADO y OLE DB para cada propiedad dinámica. Referencia de la base de datos del programador de OLE se refiere a un nombre de la propiedad ADO con el término, "Description". Puede encontrar más información acerca de estas propiedades en referencia del programador de OLE DB. Busque el nombre de propiedad de OLE DB en el índice o vea [Apéndice C: Propiedades de OLE DB](https://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Propiedades dinámicas de conexión
 Las siguientes propiedades se agregan a la **conexión** del objeto **propiedades** colección.

|Nombre de la propiedad ADO|Nombre de propiedad OLE DB|
|-----------------------|--------------------------|
|Sesiones activas|DBPROP_ACTIVESESSIONS|
|Anulación asincrónica|DBPROP_ASYNCTXNABORT|
|Confirmación asíncrona|DBPROP_ASYNCTNXCOMMIT|
|Niveles de aislamiento de confirmación automática|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Ubicación del catálogo|DBPROP_CATALOGLOCATION|
|Término de catálogo|DBPROP_CATALOGTERM|
|Definición de columna|DBPROP_COLUMNDEFINITION|
|Tiempo de espera de la conexión|DBPROP_INIT_TIMEOUT|
|Catálogo actual|DBPROP_CURRENTCATALOG|
|Origen de datos|DBPROP_INIT_DATASOURCE|
|Data Source Name|DBPROP_DATASOURCENAME|
|Objeto de origen de datos modelo de subprocesos|DBPROP_DSOTHREADMODEL|
|Nombre DBMS|DBPROP_DBMSNAME|
|Versión DBMS|DBPROP_DBMSVER|
|Propiedades extendidas|DBPROP_INIT_PROVIDERSTRING|
|Compatibilidad GROUP BY|DBPROP_GROUPBY|
|Compatibilidad con tablas heterogéneas|DBPROP_HETEROGENEOUSTABLES|
|Minúsculas en identificadores|DBPROP_IDENTIFIERCASE|
|Catálogo original|DBPROP_INIT_CATALOG|
|Niveles de aislamiento|DBPROP_SUPPORTEDTXNISOLEVELS|
|Retención de aislamiento|DBPROP_SUPPORTEDTXNISORETAIN|
|Identificador de configuración regional|DBPROP_INIT_LCID|
|Location|DBPROP_INIT_LOCATION|
|Tamaño máximo de índice|DBPROP_MAXINDEXSIZE|
|Tamaño máximo de fila|DBPROP_MAXROWSIZE|
|Tamaño máximo de fila incluye BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Número máximo de tablas en SELECT|DBPROP_MAXTABLESINSELECT|
|Modo|DBPROP_INIT_MODE|
|Varios conjuntos de parámetros|DBPROP_MULTIPLEPARAMSETS|
|Varios resultados|DBPROP_MULTIPLERESULTS|
|Varios objetos de almacenamiento|DBPROP_MULTIPLESTORAGEOBJECTS|
|Actualización de varias tablas|DBPROP_MULTITABLEUPDATE|
|Orden de intercalación de NULL|DBPROP_NULLCOLLATION|
|Comportamiento de concatenación de NULL|DBPROP_CONCATNULLBEHAVIOR|
|Servicios OLE DB|DBPROP_INIT_OLEDBSERVICES|
|Versión OLE DB|DBPROP_PROVIDEROLEDBVER|
|Compatibilidad con objetos OLE|DBPROP_OLEOBJECTS|
|Conjunto de filas abierto|DBPROP_OPENROWSETSUPPORT|
|Columnas ORDER BY en la lista de selección|DBPROP_ORDERBYCOLUMNSINSELECT|
|Disponibilidad de parámetro de salida|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Contraseña|DBPROP_AUTH_PASSWORD|
|Pasar por Ref descriptores de acceso|DBPROP_BYREFACCESSORS|
|Persist Security Info|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
|Tipo de Id.|DBPROP_PERSISTENTIDTYPE|
|Preparar el comportamiento de anulación|DBPROP_PREPAREABORTBEHAVIOR|
|Preparar el comportamiento de confirmación|DBPROP_PREPARECOMMITBEHAVIOR|
|Término de procedimiento|DBPROP_PROCEDURETERM|
|Pedir datos|DBPROP_INIT_PROMPT|
|Nombre descriptivo del proveedor|DBPROP_PROVIDERFRIENDLYNAME|
|Provider Name|DBPROP_PROVIDERFILENAME|
|Versión del proveedor|DBPROP_PROVIDERVER|
|Origen de datos de solo lectura|DBPROP_DATASOURCEREADONLY|
|Conversiones de conjunto de filas en el comando|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|Término de esquema|DBPROP_SCHEMATERM|
|Uso del esquema|DBPROP_SCHEMAUSAGE|
|Compatibilidad con SQL|DBPROP_SQLSUPPORT|
|Almacenamiento estructurado|DBPROP_STRUCTUREDSTORAGE|
|Compatibilidad para subconsultas|DBPROP_SUBQUERIES|
|Término de tabla|DBPROP_TABLETERM|
|Transacción de DDL|DBPROP_SUPPORTEDTXNDDL|
|Id. de usuario|DBPROP_AUTH_USERID|
|Nombre de usuario|DBPROP_USERNAME|
|Identificador de ventana|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>Propiedades del conjunto de registros dinámicos
 Las siguientes propiedades se agregan a la **Recordset** del objeto **propiedades** colección.

|Nombre de la propiedad ADO|Nombre de propiedad OLE DB|
|-----------------------|--------------------------|
|Orden de acceso|DBPROP_ACCESSORDER|
|Bloquear objetos de almacenamiento|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo de marcador|DBPROP_BOOKMARKTYPE|
|Admite marcadores|DBPROP_IROWSETLOCATE|
|Cambiar filas insertadas|DBPROP_CHANGEINSERTEDROWS|
|Privilegios de columna|DBPROP_COLUMNRESTRICT|
|Notificación de conjunto de columnas|DBPROP_NOTIFYCOLUMNSET|
|Actualizaciones de objetos de almacenamiento de retraso|DBPROP_DELAYSTORAGEOBJECTS|
|Buscar hacia atrás|DBPROP_CANFETCHBACKWARDS|
|Conservar filas|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Filas inmóviles|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Marcadores literales|DBPROP_LITERALBOOKMARKS|
|Identidad de fila literal|DBPROP_LITERALIDENTITY|
|Número máximo de filas abierto|DBPROP_MAXOPENROWS|
|Máximo de filas pendientes|DBPROP_MAXPENDINGROWS|
|Número máximo de filas|DBPROP_MAXROWS|
|Granularidad de notificación|DBPROP_NOTIFICATIONGRANULARITY|
|Fases de notificación|DBPROP_NOTIFICATIONPHASES|
|Objetos de transacción|DBPROP_TRANSACTEDOBJECT|
|Propios cambios visibles|DBPROP_OWNUPDATEDELETE|
|Propias inserciones visibles|DBPROP_OWNINSERT|
|Conservar al anular|DBPROP_ABORTPRESERVE|
|Conservar al confirmar|DBPROP_COMMITPRESERVE|
|Reinicio rápido|DBPROP_QUICKRESTART|
|Eventos reentrantes|DBPROP_REENTRANTEVENTS|
|Quitar filas eliminadas|DBPROP_REMOVEDELETED|
|Comunicar múltiples cambios|DBPROP_REPORTMULTIPLECHANGES|
|Devolver inserciones pendientes|DBPROP_RETURNPENDINGINSERTS|
|Notificación de eliminación de fila|DBPROP_NOTIFYROWDELETE|
|Primera notificación de cambio de fila|DBPROP_NOTIFYROWFIRSTCHANGE|
|Notificación de inserción de fila|DBPROP_NOTIFYROWINSERT|
|Privilegios de fila|DBPROP_ROWRESTRICT|
|Notificación de resincronización de fila|DBPROP_NOTIFYROWRESYNCH|
|Modelo de subprocesos de fila|DBPROP_ROWTHREADMODEL|
|Notificación de cambio de deshacer de fila|DBPROP_NOTIFYROWUNDOCHANGE|
|Notificación de eliminación de deshacer de fila|DBPROP_NOTIFYROWUNDODELETE|
|Notificación de inserción de deshacer de fila|DBPROP_NOTIFYROWUNDOINSERT|
|Notificación de actualización de fila|DBPROP_NOTIFYROWUPDATE|
|Notificación de cambio de posición de captura del conjunto de filas|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Notificación de liberación del conjunto de filas|DBPROP_NOTIFYROWSETRELEASE|
|Desplazar hacia atrás|DBPROP_CANSCROLLBACKWARDS|
|Omitir marcadores eliminados|DBPROP_BOOKMARKSKIPPED|
|Identidad de fila segura|DBPROP_STRONGITDENTITY|
|Filas únicas|DBPROP_UNIQUEROWS|
|Posibilidad de actualización|DBPROP_UPDATABILITY|
|Utilizar marcadores|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Propiedades dinámicas de comando
 Las siguientes propiedades se agregan a la **comando** del objeto **propiedades** colección.

|Nombre de la propiedad ADO|Nombre de propiedad OLE DB|
|-----------------------|--------------------------|
|Orden de acceso|DBPROP_ACCESSORDER|
|Bloquear objetos de almacenamiento|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Tipo de marcador|DBPROP_BOOKMARKTYPE|
|Admite marcadores|DBPROP_IROWSETLOCATE|
|Cambiar filas insertadas|DBPROP_CHANGEINSERTEDROWS|
|Privilegios de columna|DBPROP_COLUMNRESTRICT|
|Notificación de conjunto de columnas|DBPROP_NOTIFYCOLUMNSET|
|Actualizaciones de objetos de almacenamiento de retraso|DBPROP_DELAYSTORAGEOBJECTS|
|Buscar hacia atrás|DBPROP_CANFETCHBACKWARDS|
|Conservar filas|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Filas inmóviles|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Marcadores literales|DBPROP_LITERALBOOKMARKS|
|Identidad de fila literal|DBPROP_LITERALIDENTITY|
|Número máximo de filas abierto|DBPROP_MAXOPENROWS|
|Máximo de filas pendientes|DBPROP_MAXPENDINGROWS|
|Número máximo de filas|DBPROP_MAXROWS|
|Granularidad de notificación|DBPROP_NOTIFICATIONGRANULARITY|
|Fases de notificación|DBPROP_NOTIFICATIONPHASES|
|Objetos de transacción|DBPROP_TRANSACTEDOBJECT|
|Propios cambios visibles|DBPROP_OWNUPDATEDELETE|
|Propias inserciones visibles|DBPROP_OWNINSERT|
|Conservar al anular|DBPROP_ABORTPRESERVE|
|Conservar al confirmar|DBPROP_COMMITPRESERVE|
|Reinicio rápido|DBPROP_QUICKRESTART|
|Eventos reentrantes|DBPROP_REENTRANTEVENTS|
|Quitar filas eliminadas|DBPROP_REMOVEDELETED|
|Comunicar múltiples cambios|DBPROP_REPORTMULTIPLECHANGES|
|Devolver inserciones pendientes|DBPROP_RETURNPENDINGINSERTS|
|Notificación de eliminación de fila|DBPROP_NOTIFYROWDELETE|
|Primera notificación de cambio de fila|DBPROP_NOTIFYROWFIRSTCHANGE|
|Notificación de inserción de fila|DBPROP_NOTIFYROWINSERT|
|Privilegios de fila|DBPROP_ROWRESTRICT|
|Notificación de resincronización de fila|DBPROP_NOTIFYROWRESYNCH|
|Modelo de subprocesos de fila|DBPROP_ROWTHREADMODEL|
|Notificación de cambio de deshacer de fila|DBPROP_NOTIFYROWUNDOCHANGE|
|Notificación de eliminación de deshacer de fila|DBPROP_NOTIFYROWUNDODELETE|
|Notificación de inserción de deshacer de fila|DBPROP_NOTIFYROWUNDOINSERT|
|Notificación de actualización de fila|DBPROP_NOTIFYROWUPDATE|
|Notificación de cambio de posición de captura del conjunto de filas|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|
|Notificación de liberación del conjunto de filas|DBPROP_NOTIFYROWSETRELEASE|
|Desplazar hacia atrás|DBPROP_CANSCROLLBACKWARDS|
|Omitir marcadores eliminados|DBPROP_BOOKMARKSKIP|
|Identidad de fila segura|DBPROP_STRONGIDENTITY|
|Posibilidad de actualización|DBPROP_UPDATABILITY|
|Utilizar marcadores|DBPROP_BOOKMARKS|

 Para más información sobre la implementación específica funcional información sobre el proveedor Microsoft OLE DB para ODBC, vea el [referencia del programador de OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) o visite el sitio Web del Centro para desarrolladores de almacenamiento y de acceso a datos en MSDN.

## <a name="see-also"></a>Vea también
 [Comando (ADO) del objeto](../../../ado/reference/ado-api/command-object-ado.md) [propiedad CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) [el objeto de conexión (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [propiedad ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [ejecutar Método (Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md) [método Open (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) [colección de parámetros (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md) [colección de propiedades (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Proveedor (propiedad, ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [el objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [admite (método)](../../../ado/reference/ado-api/supports-method.md)
