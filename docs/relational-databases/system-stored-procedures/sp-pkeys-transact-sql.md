---
title: sp_pkeys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_pkeys
- sp_pkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_pkeys
ms.assetid: e614c75d-847b-4726-8f6f-cd18de688eda
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ed0e041a6aa36027613059f16f3902bdb664aeb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056424"
---
# <a name="sppkeys-transact-sql"></a>sp_pkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve la información de clave principal de una única tabla en el entorno actual.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_pkeys [ @table_name = ] 'name'       
    [ , [ @table_owner = ] 'owner' ]   
    [ , [ @table_qualifier = ] 'qualifier' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @table_name=] '*nombre*'  
 Es la tabla que se va a devolver información. *nombre* es **sysname**, no tiene ningún valor predeterminado. No se admite la coincidencia de patrón de caracteres comodín.  
  
 [ @table_owner=] '*propietario*'  
 Especifica el propietario de la tabla especificada. *propietario* es **sysname**, su valor predeterminado es null. No se admite la coincidencia de patrón de caracteres comodín. Si *propietario* no se especifica, se aplican las reglas predeterminadas de visibilidad de tabla del DBMS subyacente.  
  
 En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si el usuario actual posee una tabla en la que se especifica el nombre, se devuelven las columnas de esa tabla. Si el *propietario* no se especifica y el usuario actual no posee una tabla con los valores especificados *nombre*, este procedimiento busca una tabla con los valores especificados *nombre* que pertenecen a la propietario de la base de datos. Si existe una, se devuelven las columnas de esa tabla.  
  
 [ @table_qualifier=] '*calificador*'  
 Es el calificador de la tabla. *calificador* es **sysname**, su valor predeterminado es null. Varios productos DBMS admiten nombres de tres partes para tablas (_calificador_ **.** _propietario_ **.** _nombre_). En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre de la base de datos. En algunos productos, representa el nombre del servidor del entorno de base de datos de la tabla.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 None  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Nombre del calificador de tabla. Este campo puede ser NULL.|  
|TABLE_OWNER|**sysname**|Nombre del propietario de la tabla. Este campo siempre devuelve un valor.|  
|TABLE_NAME|**sysname**|Nombre de la tabla. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre de la tabla como se muestra en la tabla sysobjects. Este campo siempre devuelve un valor.|  
|COLUMN_NAME|**sysname**|Nombre de la columna, para cada columna de TABLE_NAME devuelta. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre de la columna como se muestra en la tabla sys.columns. Este campo siempre devuelve un valor.|  
|KEY_SEQ|**smallint**|Número de secuencia de la columna en una clave principal con varias columnas.|  
|PK_NAME|**sysname**|Identificador de la clave principal. Devuelve NULL si no es aplicable al origen de datos.|  
  
## <a name="remarks"></a>Comentarios  
 sp_pkeys devuelve información acerca de las columnas definidas explícitamente con una restricción PRIMARY KEY. Debido a que no todos los sistemas aceptan claves principales con nombre explícito, el implementador de puerta de enlace determina qué constituye una clave principal. Observe que el término clave principal hace referencia a la clave principal lógica de una tabla. Se espera que cada clave enumerada como clave principal lógica tenga un índice único definido en la misma. Este índice único también se devuelve en sp_statistics.  
  
 El procedimiento almacenado sp_pkeys es equivalente a SQLPrimaryKeys en ODBC. Los resultados devueltos se ordenan por TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME y KEY_SEQ.  
  
## <a name="permissions"></a>Permisos  
 Es necesario contar con un permiso de tipo SELECT sobre el esquema.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se recupera la clave principal de la tabla `HumanResources.Department` de la base de datos `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_pkeys @table_name = N'Department'  
    ,@table_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 En el siguiente ejemplo se recupera la clave principal de la tabla `DimAccount` de la base de datos `AdventureWorksPDW2012`. Devuelve cero filas indicando que la tabla no tiene una clave principal.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_pkeys @table_name = N'DimAccount;  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

