---
title: IHarticles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHarticles
- IHarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHarticles system table
ms.assetid: 773ef9b7-c993-4629-9516-70c47b9dcf65
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc1a800ff61bde8e4d446462143bf0d333a16fe7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817138"
---
# <a name="iharticles-transact-sql"></a>IHarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **IHarticles** tabla del sistema contiene una fila por cada artículo replicado desde un no publicador de SQL Server utilizando el distribuidor actual. Esta tabla se almacena en la base de datos de distribución.  
  
## <a name="definition"></a>Definición  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|La columna de identidad que proporciona un número de identificación único para el artículo.|  
|**Nombre**|**sysname**|El nombre asociado al artículo, único en la publicación.|  
|**publication_id**|**smallint**|Id. de la publicación a la que pertenece el artículo.|  
|**table_id**|**int**|El identificador de la tabla que se publica desde [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md).|  
|**publisher_id**|**smallint**|El identificador del publicador que no sea de SQL Server.|  
|**creation_script**|**nvarchar(255)**|El script de esquema del artículo.|  
|**del_cmd**|**nvarchar(255)**|El tipo de comando de replicación utilizado al replicar eliminaciones con artículos de la tabla. Para más información, vea [Especificar cómo se propagan los cambios para los artículos transaccionales](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**filter**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**filter_clause**|**ntext**|Cláusula WHERE del artículo, utilizada para el filtrado horizontal y escrita en Transact-SQL estándar que puede interpretar un publicador que no sea de SQL.|  
|**ins_cmd**|**nvarchar(255)**|El tipo de comando de replicación utilizado al replicar inserciones con artículos de la tabla. Para más información, vea [Especificar cómo se propagan los cambios para los artículos transaccionales](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**pre_creation_cmd**|**tinyint**|Comando para ejecutar antes de que la instantánea inicial se aplique cuando ya existe un objeto con el mismo nombre en el suscriptor.<br /><br /> **0** = none: no se ejecuta un comando.<br /><br /> **1** = DROP: quita la tabla de destino.<br /><br /> **2** = DELETE: elimina los datos de la tabla de destino.<br /><br /> **3** = TRUNCATE: trunca la tabla de destino.|  
|**status**|**tinyint**|Máscara de bits para las opciones y estado del artículo; puede ser el resultado OR lógico bit a bit de uno o más de estos valores:<br /><br /> **0** no = propiedades adicionales.<br /><br /> **1** = activo.<br /><br /> **8** = incluir el nombre de columna en las instrucciones INSERT.<br /><br /> **16** = usar instrucciones con parámetros.<br /><br /> Por ejemplo, un artículo activo que utilice instrucciones con parámetros tendrá un valor de 17 en esta columna. Un valor de 0 significa que el artículo no está activo y no tiene otras propiedades definidas.|  
|**Tipo**|**tinyint**|Tipo de artículo:<br /><br /> **1** = artículo basado en registro.|  
|**upd_cmd**|**nvarchar(255)**|El tipo de comando de replicación utilizado al replicar actualizaciones con artículos de la tabla. Para más información, vea [Especificar cómo se propagan los cambios para los artículos transaccionales](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**schema_option**|**binary(8)**|Mapa de bits de la opción de generación de esquema del artículo dado, que puede ser el resultado OR lógico bit a bit de uno o varios de estos valores:<br /><br /> **0 x 00** = disable scripting del agente de instantáneas y utiliza la secuencia CreationScript.<br /><br /> **0 x 01** = genera la creación del objeto (CREATE TABLE, CREATE PROCEDURE etc.).<br /><br /> **0 x 10** = generar un índice clúster correspondiente.<br /><br /> **0 x 40** = generar los índices no clúster correspondientes.<br /><br /> **0 x 80** = incluir la integridad referencial declarada en las claves principales.<br /><br /> **0 x 1000** = replica la intercalación de nivel de columna. Nota: Esta opción se establece de forma predeterminada para los publicadores de Oracle habilitar las comparaciones entre mayúsculas y minúsculas.<br /><br /> **0 x 4000** = claves únicas de replicación si se define en un artículo de tabla.<br /><br /> **0 x 8000** = replica artículo de una clave principal y las claves únicas en una tabla como restricciones mediante instrucciones ALTER TABLE.|  
|**dest_owner**|**sysname**|Propietario de la tabla de la base de datos de destino.|  
|**dest_table**|**sysname**|Nombre de la tabla de destino.|  
|**tablespace_name**|**nvarchar(255)**|Identifica el espacio de tablas utilizado por la tabla de registro del artículo.|  
|**objid**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**sync_objid**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**description**|**nvarchar(255)**|La entrada descriptiva del artículo.|  
|**publisher_status**|**int**|Se utiliza para indicar si se ha definido la vista que define el artículo publicado mediante una llamada a [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md).<br /><br /> **0** = [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) se ha llamado.<br /><br /> **1** = [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) no se ha llamado.|  
|**article_view_owner**|**nvarchar(255)**|El propietario del objeto de sincronización del publicador utilizado por el Agente de registro del LOG.|  
|**article_view**|**nvarchar(255)**|El objeto de sincronización del publicador utilizado por el Agente de registro del LOG.|  
|**ins_scripting_proc**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**del_scripting_proc**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**upd_scripting_proc**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**custom_script**|**int**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**fire_triggers_on_snapshot**|**bit**|Esta columna no se utiliza y se incluye solo para hacer el [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) ver de la **IHarticles** tabla compatible con la [sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md) vista utilizada para SQL Server (de artículos [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md)).|  
|**instance_id**|**int**|Identifica la instancia actual del registro del artículo para la tabla publicada.|  
|**use_default_datatypes**|**bit**|Indica si el artículo utiliza asignaciones de tipos de datos de forma predeterminada; un valor de **1** indica que se utilizan asignaciones de tipos de datos de forma predeterminada.|  
  
## <a name="see-also"></a>Vea también  
 [Replicación de bases de datos heterogéneas](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Las tablas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)  
  
  
