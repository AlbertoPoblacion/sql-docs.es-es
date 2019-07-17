---
title: Sys.column_store_row_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_row_groups_TSQL
- column_store_row_groups
- sys.column_store_row_groups
- column_store_row_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_row_groups catalog view
ms.assetid: 76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c98acb87e180dce32a00e77ba6c1af9fbd48b6fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140009"
---
# <a name="syscolumnstorerowgroups-transact-sql"></a>sys.column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Proporciona información del índice clúster de almacén de columnas una vez por segmento para ayudar al administrador a tomar decisiones de administración del sistema. **Sys.column_store_row_groups** tiene una columna para el número total de filas almacenadas físicamente (incluidas las marcadas como eliminadas) y una columna para el número de filas marcadas como eliminadas. Use **sys.column_store_row_groups** para determinar qué fila grupos tienen un alto porcentaje de filas eliminadas y deben volver a generar.  
   
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|El identificador de la tabla en el que se define este índice.|  
|**index_id**|**int**|Identificador del índice de la tabla que contiene este índice de almacén de columnas.|  
|**partition_number**|**int**|Identificador de la partición de la tabla que contiene el grupo de filas row_group_id. Puede utilizar partition_number para unir esta DMV a sys.partitions.|  
|**row_group_id**|**int**|El número de grupo de filas asociado con este grupo de filas. Es único en la partición.<br /><br /> -1 = el final de una tabla en memoria.|  
|**delta_store_hobt_id**|**bigint**|El hobt_id para el grupo de filas abiertos en el almacén delta.<br /><br /> Es NULL si el grupo de filas no está en el almacén delta.<br /><br /> NULL para el final de una tabla en memoria.|  
|**state**|**tinyint**|Número de identificación asociado con el state_description.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED <br /><br /> 4 = OBJETO DE DESECHO|  
|**state_description**|**nvarchar(60)**|Descripción del estado persistente del grupo de filas:<br /><br /> INVISIBLE: un segmento comprimido oculto en el proceso de creación a partir de datos en un almacén delta. Las acciones de lectura utilizarán el almacén delta hasta que se complete el segmento comprimido invisible. Después, se hará visible el nuevo segmento y se quitará el almacén delta de origen.<br /><br /> Abra - un grupo de filas de lectura/escritura que acepta nuevos registros. Un grupo de filas abierto está todavía en formato de almacén de filas y no se ha comprimido al formato de almacén de columnas.<br /><br /> CERRADO: un grupo de filas que se ha rellenado, pero el proceso de tupla motriz aún no se han comprimido.<br /><br /> COMPRIMIR - un grupo de filas que se ha rellenado y comprimido.|  
|**total_rows**|**bigint**|Total de filas almacenadas físicamente en el grupo de filas. Es posible que se hayan eliminado algunas, pero estas se siguen almacenando. El número máximo de filas en un grupo de filas es 1.048.576 (hexadecimal FFFFF).|  
|**deleted_rows**|**bigint**|Total de filas del grupo de filas marcadas como eliminadas. Esto es siempre 0 para los grupos de filas DELTA.|  
|**size_in_bytes**|**bigint**|Tamaño en bytes de todos los datos de este grupo de filas (sin incluir metadatos o diccionarios compartidos), tanto para los grupos de filas DELTA como COLUMNSTORE.|  
  
## <a name="remarks"></a>Comentarios  
 Devuelve una fila para cada grupo de filas del almacén de columnas de cada tabla que tenga un índice clúster o no clúster de almacén de columnas.  
  
 Use **sys.column_store_row_groups** para determinar el número de filas incluido en el grupo de filas y el tamaño del grupo de filas.  
  
 Cuando el número de filas eliminadas de un grupo de filas alcanza un alto porcentaje de las filas totales, la tabla pierde eficiencia. Vuelva a generar el índice de almacén de columnas para reducir el tamaño de la tabla, reduciendo así la E/S de disco necesaria para leer la tabla. Para volver a generar el uso del índice de almacén de columnas el **RECOMPILAR** opción de la **ALTER INDEX** instrucción.  
  
 El almacén de columnas actualizable primero inserta nuevos datos en un **abierto** grupo de filas, que está en formato de almacén de filas y, a veces también se denomina tabla delta.  Una vez que un grupo de filas abierto está lleno, su estado cambia a **cerrado**. La tupla motriz comprime un grupo de filas cerrado en formato de almacén de columnas y el estado cambia a **comprimida**.  La tupla motriz es un proceso en segundo plano que de forma periódica se despierta y comprueba si hay grupos de filas cerrados listos para comprimirse en un grupo de filas de almacén de columnas.  La tupla motriz también cancela la asignación de los grupos de filas en los que se han borrado todas las filas. Desasignadas los grupos de filas se marcan como **DESECHO**. Para ejecutar la tupla motriz inmediatamente, use el **REORGANIZAR** opción de la **ALTER INDEX** instrucción.  
  
 Cuando se ha rellenado un grupo de filas de almacén de columnas, se comprime y ya no se aceptan filas nuevas. Cuando se eliminan filas de un grupo comprimido, siguen estando allí pero están marcadas como eliminadas. Las actualizaciones de un grupo comprimido se implementan como una eliminación del grupo comprimido, y como una inserción en un grupo abierto.  
  
## <a name="permissions"></a>Permisos  
 Devuelve información de una tabla si el usuario tiene **VIEW DEFINITION** permiso en la tabla.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente combina el **sys.column_store_row_groups** tabla con otras tablas del sistema para devolver información sobre tablas específicas. La columna `PercentFull` calculada es una estimación de la eficacia del grupo de filas. Para buscar información en un única tabla, quite el comentario guiones delante de la **donde** cláusula y proporcione un nombre de tabla.  
  
```  
SELECT i.object_id, object_name(i.object_id) AS TableName,   
i.name AS IndexName, i.index_id, i.type_desc,   
CSRowGroups.*,   
100*(total_rows - ISNULL(deleted_rows,0))/total_rows AS PercentFull    
FROM sys.indexes AS i  
JOIN sys.column_store_row_groups AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id  
AND i.index_id = CSRowGroups.index_id   
--WHERE object_name(i.object_id) = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>Vea también  
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Consultar el catálogo del sistema SQL Server preguntas más frecuentes](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guía de índices de almacén de columnas](~/relational-databases/indexes/columnstore-indexes-overview.md)     
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

