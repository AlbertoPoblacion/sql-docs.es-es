---
title: OBJECT_SCHEMA_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OBJECT_SCHEMA_NAME
- OBJECT_SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], names
- schemas [SQL Server], names
- displaying schema names
- database objects [SQL Server], names
- OBJECT_SCHEMA_NAME function
ms.assetid: 5ba90bb9-d045-4164-963e-e9e96c0b1e8b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 70556dd6365c6c3b204456db2877fdbc61e53d44
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "67914753"
---
# <a name="object_schema_name-transact-sql"></a>OBJECT_SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Devuelve el nombre del esquema de la base de datos para los objetos de ámbito de esquema. Para obtener una lista de los objetos de ámbito de esquema, vea [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
OBJECT_SCHEMA_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *object_id*  
 Es el identificador del objeto que se va a utilizar. *object_id* es de tipo **int** y se considera que se trata de un objeto de ámbito de esquema en la base de datos especificada o en el contexto de la base de datos actual.  
  
 *database_id*  
 Identificador de la base de datos donde se va a buscar el objeto. *database_id* es **int**.  
  
## <a name="return-types"></a>Tipos de valor devuelto  
 **sysname**  
  
## <a name="exceptions"></a>Excepciones  
 Devuelve NULL si se produce un error o si el autor de la llamada no tiene permiso para ver el objeto. Si la base de datos de destino tiene la opción AUTO_CLOSE establecida en ON, la función abrirá la base de datos.  
  
 Un usuario solo puede ver los metadatos de elementos protegibles que posea o para los que se le haya concedido permiso. Esto significa que las funciones integradas de emisión de metadatos, como OBJECT_SCHEMA_NAME, pueden devolver NULL si el usuario no tiene ningún permiso para el objeto. Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso ANY en el objeto. Para especificar un identificador de base de datos, también se requiere el permiso CONNECT en la base de datos o se debe habilitar la cuenta de invitado.  
  
## <a name="remarks"></a>Observaciones  
 Las funciones del sistema se pueden usar en la lista de selección, en la cláusula WHERE y en cualquier lugar donde se permita una expresión. Para obtener más información, vea [Expressions](../../t-sql/language-elements/expressions-transact-sql.md) y [WHERE](../../t-sql/queries/where-transact-sql.md).  
  
 El conjunto de resultados que devuelve esta función del sistema usa la intercalación de la base de datos actual.  
  
 Si no se especifica *database_id*, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] considera que *object_id* está en el contexto de la base de datos actual. Una consulta que hace referencia a un parámetro *object_id* de otra base de datos devuelve NULL o resultados incorrectos. Por ejemplo, en la siguiente consulta, el contexto de la base de datos actual es [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. [!INCLUDE[ssDE](../../includes/ssde-md.md)] intenta devolver un nombre de esquema de objetos para el identificador de objeto especificado en esa base de datos en lugar de en la base de datos especificada en la cláusula FROM de la consulta. Por lo tanto, se devuelve información incorrecta.  
  
```sql
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id)  
FROM master.sys.objects;  
  
```  
  
 En el ejemplo siguiente, se especifica el identificador de la base de datos `master` en la función `OBJECT_SCHEMA_NAME` y devuelve los resultados correctos.  
  
```sql
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
  
```  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-returning-the-object-schema-name-and-object-name"></a>A. Devolver el nombre del esquema de objetos y el nombre del objeto  
 En el ejemplo siguiente se devuelve el nombre del esquema de objetos, el nombre del objeto y el texto SQL para todos los planes de consulta en caché que no sean instrucciones preparadas o ad hoc.  
  
```sql
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_statement  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="b-returning-three-part-object-names"></a>B. Devolver nombres de objetos de tres partes  
 En el ejemplo siguiente se devuelve el nombre del objeto, esquema o base de datos junto con todas las demás columnas de la vista de administración dinámica `sys.dm_db_index_operational_stats` de todos los objetos de todas las bases de datos.  
  
```sql
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de metadatos &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [OBJECT_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [Elementos protegibles](../../relational-databases/security/securables.md)
