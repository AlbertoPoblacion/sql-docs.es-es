---
title: sp_helpmergearticleconflicts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85e75e1ce52866eb04b3c410f021db8de392239a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122325"
---
# <a name="sphelpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve los artículos de la publicación que tienen conflictos. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicaciones o en el suscriptor de la base de datos de suscripciones de mezcla.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publication = ] 'publication'` Es el nombre de la publicación de combinación. *publicación* es **sysname**, su valor predeterminado es **%** , que devuelve todos los artículos de la base de datos que tienen conflictos.  
  
`[ @publisher = ] 'publisher'` Es el nombre del publicador. *publisher* es **sysname**, su valor predeterminado es null.  
  
`[ @publisher_db = ] 'publisher_db'` Es el nombre de la base de datos del publicador. *publisher_db* es **sysname**, su valor predeterminado es null.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**article**|**sysname**|Nombre del artículo.|  
|**source_owner**|**sysname**|Propietario del objeto de origen.|  
|**source_object**|**nvarchar(386)**|Nombre del objeto de origen.|  
|**conflict_table**|**nvarchar(258)**|Nombre de la tabla que almacena los conflictos de inserción o actualización.|  
|**guidcolname**|**sysname**|Nombre de la propiedad RowGuidCol para el objeto de origen.|  
|**centralized_conflicts**|**int**|Indica si los registros de conflictos se almacenan en el publicador dado.|  
  
 Si el artículo tiene únicamente los conflictos de eliminación y no **conflict_table** filas, el nombre de la **conflict_table** en el resultado de conjunto es NULL.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_helpmergearticleconflicts** se utiliza en la replicación de mezcla.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor y el **db_owner** rol fijo de base de datos se puede ejecutar **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
