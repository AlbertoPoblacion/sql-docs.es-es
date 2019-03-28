---
title: sp_mergearticlecolumn (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergearticlecolumn
- sp_mergearticlecolumn_TSQL
helpviewer_keywords:
- sp_mergearticlecolumn
ms.assetid: b4f2b888-e094-4759-a472-d893638995eb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2cb929ffc3506d6dcb4a0745c53b47a45fdb469
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538617"
---
# <a name="spmergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea particiones verticales en una publicación de combinación. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_mergearticlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column'  
    [ , [ @operation = ] 'operation'   
    [ , [ @schema_replication = ] 'schema_replication' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publication = ] 'publication'` Es el nombre de la publicación. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @article = ] 'article'` Es el nombre del artículo de la publicación. *artículo* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @column = ] 'column'` Identifica las columnas que se va a crear la partición vertical. *columna* es **sysname**, su valor predeterminado es null. Si es NULL y `@operation = N'add'`, de manera predeterminada se agregan al artículo todas las columnas de la tabla de origen. *columna* no puede ser NULL cuando *operación* está establecido en **drop**. Para excluir las columnas de un artículo, ejecute **sp_mergearticlecolumn** y especifique *columna* y `@operation = N'drop'` para cada columna que se va a quitar de la especificada *artículo*.  
  
`[ @operation = ] 'operation'` Es el estado de replicación. *operación* es **nvarchar (4)**, con el valor predeterminado es ADD. **agregar** marca la columna para la replicación. **quitar** borra la columna.  
  
`[ @schema_replication = ] 'schema_replication'` Especifica que un cambio de esquema se propagará cuando se ejecuta el agente de mezcla. *el argumento schema_replication* es **nvarchar (5)**, su valor predeterminado es False.  
  
> [!NOTE]  
>  Solo **FALSE** es compatible con *el argumento schema_replication*.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Habilita o deshabilita la capacidad de invalidar una instantánea. *force_invalidate_snapshot* es un **bit**, su valor predeterminado es **0**.  
  
 **0** especifica que los cambios realizados en el artículo de mezcla no invalidarán la instantánea no es válido.  
  
 **1** especifica que los cambios realizados en el artículo de mezcla pueden invalidar la instantánea no es válido, y si es así, un valor de **1** concede permiso para la nueva instantánea que se produzca.  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_` Habilita o deshabilita la capacidad de reinicializar la suscripción. *force_reinit_subscription* es un poco con un valor predeterminado de **0**.  
  
 **0** especifica que los cambios realizados en el artículo de mezcla no invalidarán la suscripción para reinicializarla.  
  
 **1** especifica que los cambios realizados en el artículo de mezcla pueden causar la suscripción para reinicializarla, y si es así, un valor de **1** concede permiso para que se produzca la reinicialización de suscripción.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_mergearticlecolumn** se utiliza en la replicación de mezcla.  
  
 No es posible quitar una columna de identidad del artículo si se está utilizando la administración automática del intervalo de identidad. Para más información, vea [Replicar columnas de identidad](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Si una aplicación establece una nueva partición vertical después de crear la instantánea inicial, es necesario generar una instantánea nueva y volverla a aplicar a cada suscripción. Las instantáneas se aplican al ejecutar el siguiente Agente de instantáneas, distribución o mezcla programado.  
  
 Si se utiliza el seguimiento por fila en la detección de conflictos (valor predeterminado), la tabla base puede incluir un máximo de 1024 columnas, pero en el artículo deben filtrarse las columnas de forma que se publique un máximo de 246 columnas. Si se utiliza el seguimiento por columna, la tabla base puede incluir 246 columnas como máximo.  
  
## <a name="example"></a>Ejemplo  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_mergearticlecolumn**.  
  
## <a name="see-also"></a>Vea también  
 [Definir y modificar un filtro de combinación entre artículos de mezcla](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definir y modificar un filtro de fila con parámetros para un artículo de mezcla](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtrar datos publicados](../../relational-databases/replication/publish/filter-published-data.md)   
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
