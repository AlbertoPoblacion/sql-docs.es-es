---
title: sp_addtype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addtype
- sp_addtype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addtype
ms.assetid: ed72cd8e-5ff7-4084-8458-2d8ed279d817
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ead23c8feb428772fcde5bcdb59f19e1a23b6cd9
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492847"
---
# <a name="spaddtype-transact-sql"></a>sp_addtype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un tipo de datos de alias.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use [CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md) en su lugar.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_addtype [ @typename = ] type,   
    [ @phystype = ] system_data_type   
    [ , [ @nulltype = ] 'null_type' ] ;  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @typename = ] type` Es el nombre del tipo de datos de alias. Alias tienen que seguir las reglas de los nombres de tipo de datos [identificadores](../../relational-databases/databases/database-identifiers.md) y deben ser únicos en cada base de datos. *tipo* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @phystype = ] system_data_type` Es físico o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona, el tipo de datos en el que se basa el tipo de datos de alias. *system_data_type* es **sysname**, no tiene ningún valor predeterminado y puede ser uno de estos valores:  
  
||||  
|-|-|-|  
|**bigint**|**binary(n)**|**bit**|  
|**char(n)**|**datetime**|**decimal**|  
|**float**|**image**|**int**|  
|**money**|**nchar(n)**|**ntext**|  
|**numeric**|**nvarchar(n)**|**real**|  
|**smalldatetime**|**smallint**|**smallmoney**|  
|**sql_variant**|**texto**|**tinyint**|  
|**uniqueidentifier**|**varbinary(n)**|**varchar(n)**|  
  
 Se requieren comillas para delimitar los parámetros que tengan espacios o signos de puntuación incrustados. Para obtener más información acerca de los tipos de datos disponibles, consulte [tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
 *n*  
 Es un entero no negativo que indica la longitud del tipo de datos elegido.  
  
 *P*  
 Es un entero no negativo que indica el número total máximo de cifras decimales que se pueden almacenar, a ambos lados del separador decimal. Para más información, vea [decimal y numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *s*  
 Es un entero no negativo que indica el número máximo de cifras decimales que se pueden almacenar a la derecha del separador decimal, y tiene que ser menor que la precisión decimal o igual a ésta. Para más información, vea [decimal y numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
`[ @nulltype = ] 'null_type'` Indica la forma en que el tipo de datos de alias trata los valores nulos. *null_type* es **varchar (** 8 **)**, su valor predeterminado es null y debe incluirse entre comillas simples ('NULL', 'NOT NULL' o 'NONULL'). Si *null_type* no se define explícitamente mediante **sp_addtype**, se establece en la nulabilidad predeterminada actual. Utilice la función de sistema GETANSINULL para determinar la nulabilidad predeterminada actual. Esto se puede ajustar mediante la instrucción SET o ALTER DATABASE. La nulabilidad se tiene que definir explícitamente. Si **@phystype** es **bit**, y **@nulltype** no se especifica, el valor predeterminado no es nulo.  
  
> [!NOTE]  
>  El *null_type* parámetro solo define la nulabilidad predeterminada para este tipo de datos. Si la nulabilidad se define explícitamente cuando se utiliza este tipo de datos de alias durante la creación de una tabla, ésta tendrá prioridad sobre la nulabilidad definida. Para obtener más información, consulte [ALTER TABLE &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md) y [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentarios  
 Los nombres de los tipos de datos de alias tienen que ser exclusivos en la base de datos, pero tipos de datos de alias con distintos nombres pueden tener la misma definición.  
  
 Ejecutar **sp_addtype** crea un tipo de datos de alias que aparece en el **sys.types** vista para una base de datos de catálogo. Si el tipo de datos de alias debe estar disponible en todas las nuevas bases de datos definido por el usuario, agregarlo a **modelo**. Después de crear un tipo de datos de alias, puede utilizarse en CREATE TABLE o ALTER TABLE, así como enlazarse a valores predeterminados y reglas. Todos los tipos de datos de alias escalares que se crean mediante **sp_addtype** se encuentran en el **dbo** esquema.  
  
 Los tipos de datos de alias heredan la intercalación predeterminada de la base de datos. Las intercalaciones de columnas y variables de tipos de alias se definen en el [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE, ALTER TABLE y DECLARE @*local_variable* instrucciones. Cualquier cambio en la intercalación predeterminada de la base de datos solo se aplica a las columnas y variables nuevas del tipo; no afecta la intercalación de los tipos existentes.  
  
> [!IMPORTANT]  
>  Para fines de compatibilidad con versiones anteriores, el **pública** rol de base de datos se concede automáticamente el permiso REFERENCES en tipos de datos de alias que se crean mediante **sp_addtype**. Tenga en cuenta cuando se crean los tipos de datos de alias con la instrucción CREATE TYPE en lugar de **sp_addtype**, se produce ninguna concesión automática.  
  
 Tipos de datos de alias no se pueden definir mediante el uso de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**, **tabla**, **xml**, **varchar (max)**, **nvarchar (max)** o **varbinary (max)** tipos de datos.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer a la **db_owner** o **db_ddladmin** rol fijo de base de datos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-creating-an-alias-data-type-that-does-not-allow-for-null-values"></a>A. Crear un tipo de datos de alias que no permite valores NULL  
 En el ejemplo siguiente se crea un tipo de datos de alias denominado `ssn` (número de seguridad social) que se basa en el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-proporcionado **varchar** tipo de datos. El tipo de datos `ssn` se utiliza en columnas que almacenan números de la seguridad social de 11 cifras (999-99-9999). La columna no puede ser NULL.  
  
 Observe que `varchar(11)` está entre comillas simples porque contiene signos de puntuación (paréntesis).  
  
```  
USE master;  
GO  
EXEC sp_addtype ssn, 'varchar(11)', 'NOT NULL';  
GO  
```  
  
### <a name="b-creating-an-alias-data-type-that-allows-for-null-values"></a>b. Crear un tipo de datos de alias que permite valores NULL  
 En este ejemplo se crea un tipo de datos de alias (basado en el tipo de datos `datetime`) denominado `birthday` que permite valores NULL.    
  
```  
USE master;  
GO  
EXEC sp_addtype birthday, datetime, 'NULL';  
```  
  
### <a name="c-creating-additional-alias-data-types"></a>C. Crear tipos de datos de alias adicionales  
 En este ejemplo se crean dos tipos de datos de alias adicionales, `telephone` y `fax`, para números de teléfono y fax locales e internacionales.    
  
```  
USE master;  
GO  
EXEC sp_addtype telephone, 'varchar(24)', 'NOT NULL';  
GO  
EXEC sp_addtype fax, 'varchar(24)', 'NULL';  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del motor de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_droptype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
