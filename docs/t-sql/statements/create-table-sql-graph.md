---
title: CREATE TABLE (SQL Graph) | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQL_GRAPH_TSQL
- TABLE
- CREATE_TABLE_TSQL
- NODE
- NODE_TSQL
- AS_NODE
- AS_NODE_TSQL
- EDGE
- EDGE_TSQL
- AS_EDGE
- AS_EDGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- graph
- SQL graph
- CREATE TABLE SQL graph
- NODE
- EDGE
- SQL graph, CREATE TABLE statement
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e61c1dc4501dfdfe45d10b2fda4434be2f35e7b2
ms.sourcegitcommit: e4794943ea6d2580174d42275185e58166984f8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65503112"
---
# <a name="create-table-sql-graph"></a>CREATE TABLE (SQL Graph)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Crea una tabla de SQL Graph como una tabla `NODE` o `EDGE`. 
  
> [!NOTE]   
>  Para instrucciones Transact-SQL estándar, vea [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CREATE TABLE   
    { database_name.schema_name.table_name | schema_name.table_name | table_name }
    ( { <column_definition> } [ ,...n ] )   
    AS [ NODE | EDGE ]
[ ; ]  
```  
  
  
## <a name="arguments"></a>Argumentos  
En este documento solo se enumeran los argumentos pertenecientes a SQL Graph. Para obtener una lista completa y una descripción de los argumentos admitidos, vea [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).

 *database_name*    
 Es el nombre de la base de datos en la que se crea la tabla. *database_name* debe especificar el nombre de una base de datos existente. Si no se especifica, *database_name* usa de manera predeterminada la base de datos actual. El inicio de sesión de la conexión actual debe estar asociado a un identificador de usuario existente en la base de datos especificada por *database_name*, y ese identificador de usuario debe tener permisos CREATE TABLE.  
  
 *schema_name*    
 Es el nombre del esquema al que pertenece la nueva tabla.  
  
 *table_name*    
 Es el nombre de la tabla de nodo o perimetral. Los nombres de las tablas deben seguir las reglas de los [identificadores](../../relational-databases/databases/database-identifiers.md). *table_name* puede contener un máximo de 128 caracteres, excepto para los nombres de tablas temporales locales (nombres precedidos de un único signo de número, #), que no pueden superar los 116 caracteres.  
  
 NODE   
 Crea una tabla de nodo.

 EDGE  
 Crea una tabla perimetral.  
  
## <a name="remarks"></a>Notas  
No se admite la creación de una tabla temporal como una tabla de nodo o perimetral.  

No se admite la creación de una tabla de nodo o perimetral como una tabla temporal.

No se admite Stretch Database para una tabla de nodo o perimetral.

Las tablas de nodo o perimetrales no pueden ser tablas externas (no hay compatibilidad de PolyBase con las tablas de Graph). 
  
 
## <a name="examples"></a>Ejemplos  
  
### <a name="a-create-a-node-table"></a>A. Creación de una tabla `NODE`
 En el ejemplo siguiente se muestra cómo se crea una tabla `NODE`.

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>B. Creación de una tabla `EDGE`
En el ejemplo siguiente se muestra cómo se crean tablas `EDGE`.

```
 CREATE TABLE friends (
    id integer PRIMARY KEY,
    start_date date
 ) AS EDGE;

```

```
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;

```


## <a name="see-also"></a>Consulte también  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [INSERT (SQL Graph)](../../t-sql/statements/insert-sql-graph.md)]  
 [Graph processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Procesamiento de gráficos con SQL Server 2017)

