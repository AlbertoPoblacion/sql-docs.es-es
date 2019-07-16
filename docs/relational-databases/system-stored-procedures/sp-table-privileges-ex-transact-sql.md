---
title: sp_table_privileges_ex (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
author: stevestein
ms.author: sstein
ms.openlocfilehash: b40f7233bb3c50203a68c0b01cfcbdaf631e0098
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096167"
---
# <a name="sptableprivilegesex-transact-sql"></a>sp_table_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información de privilegios sobre la tabla especificada del servidor vinculado especificado.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_table_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
     [ , [@fUsePattern =] 'fUsePattern']  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @table_server = ] 'table_server'` Es el nombre del servidor vinculado que se va a devolver información. *table_server* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @table_name = ] 'table_name']` Es el nombre de la tabla para que se va a proporcionar información de privilegios de tabla. *table_name* es **sysname**, su valor predeterminado es null.  
  
`[ @table_schema = ] 'table_schema'` Es el esquema de tabla. En algunos entornos DBMS es el propietario de la tabla. *TABLE_SCHEMA* es **sysname**, su valor predeterminado es null.  
  
`[ @table_catalog = ] 'table_catalog'` Es el nombre de la base de datos en el que el especificado *table_name* reside. *TABLE_CATALOG* es **sysname**, su valor predeterminado es null.  
  
`[ @fUsePattern = ] 'fUsePattern'` Determina si los caracteres '_', '%', ' [', y ']' se interpretan como caracteres comodín. Los valores válidos son 0 (coincidencia de patrón desactivada) y 1 (coincidencia de patrón activada). *fUsePattern* es **bit**, su valor predeterminado es 1.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 None  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Nombre del calificador de tabla. Varios productos DBMS admiten nombres de tres partes para tablas (_calificador_ **.** _propietario_ **.** _nombre_). En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre de la base de datos. En algunos productos, representa el nombre del servidor del entorno de base de datos de la tabla. Este campo puede ser NULL.|  
|**TABLE_SCHEM**|**sysname**|Nombre de propietario de la tabla. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna representa el nombre del usuario de base de datos que creó la tabla. Este campo siempre devuelve un valor.|  
|**TABLE_NAME**|**sysname**|Nombre de la tabla. Este campo siempre devuelve un valor.|  
|**OTORGANTE DE PERMISOS**|**sysname**|Nombre de usuario de base de datos que ha concedido permisos **TABLE_NAME** al **receptor**. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta columna siempre es el mismo que el **TABLE_OWNER**. Este campo siempre devuelve un valor. Además, la columna GRANTOR puede ser el propietario de la base de datos (**TABLE_OWNER**) o un usuario a los que el propietario de la base de datos haya concedido permiso mediante la cláusula WITH GRANT OPTION en la instrucción GRANT.|  
|**RECEPTOR DE PERMISOS**|**sysname**|Nombre de usuario de base de datos que se ha concedido permisos sobre este **TABLE_NAME** por la lista **otorgante de permisos**. Este campo siempre devuelve un valor.|  
|**PRIVILEGIO**|**varchar(** 32 **)**|Uno de los permisos de tabla disponibles. Los permisos de tabla pueden ser uno de los valores siguientes u otros valores que el origen de datos admita al definirse la implementación.<br /><br /> Seleccione = **receptor** puede recuperar datos de una o varias de las columnas.<br /><br /> INSERT = **receptor** puede proporcionar datos para nuevas filas de una o varias de las columnas.<br /><br /> UPDATE = **receptor** puede modificar datos existentes de una o varias de las columnas.<br /><br /> ELIMINAR = **receptor** puede quitar filas de la tabla.<br /><br /> REFERENCIAS = **receptor** puede hacer referencia a una columna de una tabla externa en una relación de clave principal/clave externa. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], las relaciones entre clave principal y clave externa se definen mediante restricciones de tabla.<br /><br /> El ámbito de acción dado a la **receptor** por una tabla específica privilegio es depende del origen de datos. Por ejemplo, el permiso de UPDATE podría permitir la **receptor** para actualizar todas las columnas de una tabla en un origen de datos y solo aquellas columnas para que el **otorgante de permisos** tiene el permiso UPDATE en otro origen de datos.|  
|**IS_GRANTABLE**|**varchar(** 3 **)**|Indica si el **receptor** tiene permiso para conceder permisos a otros usuarios. A esto se le suele denominar permiso "conceder por concesión". Puede ser YES, NO o NULL. Un valor desconocido, o NULL, hace referencia a un origen de datos en el que “conceder por concesión” no es aplicable.|  
  
## <a name="remarks"></a>Comentarios  
 Los resultados devueltos se ordenan por **TABLE_QUALIFIER**, **TABLE_OWNER**, **TABLE_NAME**, y **PRIVILEGIO**.  
  
## <a name="permissions"></a>Permisos  
 Es necesario contar con un permiso de tipo SELECT sobre el esquema.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se devuelve información de privilegios acerca de las tablas con nombres que comienzan por `Product` de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] del servidor vinculado especificado `Seattle1`. ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se supone que el servidor vinculado).  
  
```  
EXEC sp_table_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Product%',   
   @table_schema = 'Production',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_column_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-ex-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Distribuye los procedimientos almacenados de consultas &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
