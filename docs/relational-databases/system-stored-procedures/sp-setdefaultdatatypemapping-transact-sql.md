---
title: sp_setdefaultdatatypemapping (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setdefaultdatatypemapping
- sp_setdefaultdatatypemapping_TSQL
helpviewer_keywords:
- sp_setdefaultdatatypemapping
ms.assetid: 7394e8ca-4ce1-4e99-a784-205007c2c248
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7d3ee86844f2b120c69e2cc2ddef55644cce8f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62714352"
---
# <a name="spsetdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Marca una asignación de tipo de datos existente entre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y que no es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de datos (DBMS) de sistema de administración como el valor predeterminado. Este procedimiento almacenado se ejecuta en el distribuidor de cualquier base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_setdefaultdatatypemapping [ [ @mapping_id = ] mapping_id ]  
    [ , [ @source_dbms = ] 'source_dbms' ]  
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @source_length_min = ] source_length_min ]  
    [ , [ @source_length_max = ] source_length_max ]  
    [ , [ @source_precision_min = ] source_precision_min ]  
    [ , [ @source_precision_max = ] source_precision_max ]  
    [ , [ @source_scale_min = ] source_scale_min ]  
    [ , [ @source_scale_max = ] source_scale_max ]  
    [ , [ @source_nullable = ] source_nullable ]  
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @destination_length = ] destination_length ]  
    [ , [ @destination_precision = ] destination_precision ]  
    [ , [ @destination_scale = ] destination_scale ]  
    [ , [ @destination_nullable = ] source_nullable ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @mapping_id = ] mapping_id` Identifica una asignación de tipo de datos existente.  *mapping_id* es **int**, su valor predeterminado es NULL. Si especifica *mapping_id*, no se requieren los parámetros restantes.  
  
`[ @source_dbms = ] 'source_dbms'` Es el nombre del DBMS desde el que se asignan los tipos de datos. *source_dbms* es **sysname**, y puede tener uno de los siguientes valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**MSSQLSERVER**|El origen es una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|El origen es una base de datos de Oracle.|  
|NULL (predeterminado)||  
  
 Debe especificar este parámetro si *mapping_id* es NULL.  
  
`[ @source_version = ] 'source_version'` Es el número de versión del DBMS de origen. *source_version* es **varchar (10)** , su valor predeterminado es null.  
  
`[ @source_type = ] 'source_type'` Es el tipo de datos del DBMS de origen. *source_type* es **sysname**. Debe especificar este parámetro si *mapping_id* es NULL.  
  
`[ @source_length_min = ] source_length_min` Es la longitud mínima del tipo de datos del DBMS de origen. *source_length_min* es **bigint**, su valor predeterminado es null.  
  
`[ @source_length_max = ] source_length_max` Es la longitud máxima del tipo de datos del DBMS de origen. *source_length_max* es **bigint**, su valor predeterminado es null.  
  
`[ @source_precision_min = ] source_precision_min` Es la precisión mínima del tipo de datos del DBMS de origen. *source_precision_min* es **bigint**, su valor predeterminado es null.  
  
`[ @source_precision_max = ] source_precision_max` Es la precisión máxima del tipo de datos del DBMS de origen. *source_precision_max* es **bigint**, su valor predeterminado es null.  
  
`[ @source_scale_min = ] source_scale_min` Es la escala mínima del tipo de datos del DBMS de origen. *source_scale_min* es **int**, su valor predeterminado es null.  
  
`[ @source_scale_max = ] source_scale_max` Es la escala máxima del tipo de datos del DBMS de origen. *source_scale_max* es **int**, su valor predeterminado es null.  
  
`[ @source_nullable = ] source_nullable` Indica si el tipo de datos del DBMS de origen admite un valor null. *source_nullable* es **bit**, su valor predeterminado es null. **1** significa que se admiten valores NULL.  
  
`[ @destination_dbms = ] 'destination_dbms'` Es el nombre del DBMS de destino. *destination_dbms* es **sysname**, y puede tener uno de los siguientes valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**MSSQLSERVER**|El destino es una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|El destino es una base de datos de Oracle.|  
|**DB2**|El destino es una base de datos IBM DB2.|  
|**SYBASE**|El destino es una base de datos Sybase.|  
|NULL (predeterminado)||  
  
`[ @destination_version = ] 'destination_version'` Es la versión del producto del DBMS de destino. *destination_version* es **varchar (10)** , su valor predeterminado es null.  
  
`[ @destination_type = ] 'destination_type'` El tipo de datos aparece en el DBMS de destino. *destination_type* es **sysname**, su valor predeterminado es null.  
  
`[ @destination_length = ] destination_length` Es la longitud del tipo de datos del DBMS de destino. *destination_length* es **bigint**, su valor predeterminado es null.  
  
`[ @destination_precision = ] destination_precision` Es la precisión del tipo de datos del DBMS de destino. *destination_precision* es **bigint**, su valor predeterminado es null.  
  
`[ @destination_scale = ] destination_scale` Es la escala del tipo de datos del DBMS de destino. *destination_scale* es **int**, su valor predeterminado es null.  
  
`[ @destination_nullable = ] destination_nullable` Indica si el tipo de datos del DBMS de destino admite un valor null. *destination_nullable* es **bit**, su valor predeterminado es null. **1** significa que se admiten valores NULL.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_setdefaultdatatypemapping** se utiliza en todos los tipos de replicación entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y que no es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS.  
  
 Las asignaciones de tipos de datos predeterminados se aplican a todas las topologías de replicación que incluyen el DBMS especificado.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede ejecutar **sp_setdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Vea también  
 [Especificar asignaciones de tipo de datos para un publicador de Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
