---
title: SQLDescribeParam | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d52d68cc0cd31e9dbb3da25c46901e126252607
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63067741"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
  Para describir los parámetros de cualquier instrucción SQL, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client genera y ejecuta un [!INCLUDE[tsql](../../includes/tsql-md.md)] instrucción SELECT cuando se llama SQLDescribeParam en un identificador de instrucción ODBC preparado. Los metadatos del conjunto de resultados determinan las características de los parámetros en la instrucción preparada. SQLDescribeParam puede devolver cualquier código de error que podría devolver SQLExecute o SQLExecDirect.  
  
 Mejoras en el motor de base de datos a partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permitir SQLDescribeParam obtener descripciones más precisas de los resultados esperados. Estos resultados más precisos pueden diferir de los valores devueltos por SQLDescribeParam en versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, vea [Detección de metadatos](../native-client/features/metadata-discovery.md).  
  
 También como novedad en [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *ParameterSizePtr* ahora devuelve un valor que se alinea con la definición para el tamaño, en caracteres, de la columna o expresión de marcador de parámetro correspondiente, tal como se define en el [ODBC especificación](https://go.microsoft.com/fwlink/?LinkId=207044). En versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, *ParameterSizePtr* podría ser el valor correspondiente de `SQL_DESC_OCTET_LENGTH` para el tipo o un valor de tamaño de columna irrelevante que se proporcionó a SQLBindParameter para un tipo, el valor de lo que debe omitirse (`SQL_INTEGER`, por ejemplo).  
  
 El controlador no admite SQLDescribeParam que realiza la llamada en las situaciones siguientes:  
  
-   Después de SQLExecDirect para cualquier [!INCLUDE[tsql](../../includes/tsql-md.md)] que contiene la cláusula FROM de instrucciones UPDATE o DELETE.  
  
-   En cualquier instrucción ODBC o [!INCLUDE[tsql](../../includes/tsql-md.md)] que contenga un parámetro en una cláusula HAVING o se compare con el resultado de una función SUM.  
  
-   En cualquier instrucción ODBC o [!INCLUDE[tsql](../../includes/tsql-md.md)] que dependa de una subconsulta que contiene parámetros.  
  
-   En instrucciones ODBC SQL que contengan marcadores de parámetros en ambas expresiones de una comparación, igualdad o predicado cuantificado.  
  
-   En cualquier consulta donde uno de los parámetros sea un parámetro a una función.  
  
-   Cuando haya comentarios (/ * \*/) en el [!INCLUDE[tsql](../../includes/tsql-md.md)] comando.  
  
 Al procesar un lote de [!INCLUDE[tsql](../../includes/tsql-md.md)] instrucciones, el controlador también no admite una llamada a SQLDescribeParam marcadores de parámetros en instrucciones después de la primera instrucción del lote.  
  
 Al describir los parámetros de procedimientos almacenados preparados, SQLDescribeParam utiliza el procedimiento almacenado del sistema [sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql) para recuperar las características de parámetro. sp_sproc_columns pueden notificar datos de procedimientos almacenados dentro de la base de datos de usuario actual. Preparación de un nombre de procedimiento almacenado completo permite SQLDescribeParam ejecute en todas las bases de datos. Por ejemplo, el sistema almacena procedimiento [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) se puede preparar y ejecutar en cualquier base de datos como:  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 Ejecutar SQLDescribeParam después de preparación correcta devuelve una fila vacía que se establece cuando se conecta a cualquier base de datos pero `master`. Hace que la misma llamada, preparada como sigue, SQLDescribeParam correctamente con independencia de la base de datos de usuario actual:  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Tipos de datos de valor grande, el valor devuelto en *DataTypePtr* es SQL_VARCHAR, SQL_VARBINARY o SQL_NVARCHAR. Para indicar que el tamaño del parámetro de tipo de datos de valor grande es "ilimitado", la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conjuntos de controladores ODBC de Native Client *ParameterSizePtr* en 0. En los parámetros `varchar` estándar se devuelven los valores de tamaño reales.  
  
> [!NOTE]  
>  Si el parámetro ya se ha enlazado con un tamaño máximo para los parámetros SQL_VARCHAR, SQL_WVARCHAR o SQL_VARBINARY, se devuelve el tamaño enlazado del parámetro, no "ilimitado".  
  
 Para enlazar un parámetro de entrada de tamaño "ilimitado", se deben utilizar datos en ejecución. No es posible enlazar un parámetro de salida de "tamaño"ilimitado"(no hay ningún método de flujo de datos de un parámetro de salida, como [SQLGetData](sqlgetdata.md) para conjuntos de resultados).  
  
 Para los parámetros de salida se debe enlazar un búfer y, si el valor es demasiado grande, el búfer se rellena y se devuelve un mensaje SQL_SUCCESS_WITH_INFO junto con la advertencia "Datos tipo String, se truncarán por la derecha". Los datos truncados se descartan.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>SQLDescribeParam y parámetros con valores de tabla  
 Una aplicación puede recuperar información de parámetros con valores de tabla para una instrucción preparada con SQLDescribeParam. Para obtener más información, consulte [los metadatos del parámetro con valores de tabla para instrucciones preparadas](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Para obtener más información acerca de los parámetros con valores de tabla en general, vea [parámetros con valores de tabla &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>SQLDescribeParam admite las características mejoradas de fecha y hora  
 Los valores devueltos para los tipos de fecha y hora son los siguientes:  
  
||*DataTypePtr*|*ParameterSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Para obtener más información, consulte [mejoras de fecha y hora &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>SQLDescribeParam admite UDT CLR grandes  
 `SQLDescribeParam` admite tipos CLR definidos por el usuario (UDT) grandes. Para obtener más información, consulte [Large CLR User-Defined tipos &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [Función SQLDescribeParam](https://go.microsoft.com/fwlink/?LinkId=59339)   
 [Detalles de implementación de la API de ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
