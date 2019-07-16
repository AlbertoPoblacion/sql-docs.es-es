---
title: Sys.dm_db_xtp_checkpoint_files (Transact-SQL) | Microsoft Docs
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: in-memory-oltp
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_files
- sys.dm_db_xtp_checkpoint_files_TSQL
- dm_db_xtp_checkpoint_files_TSQL
- sys.dm_db_xtp_checkpoint_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_files dynamic management view
ms.assetid: ac8e6333-7a9f-478a-b446-5602283e81c9
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fb3aa62880de7013cf503e61eb2d86a3454c2350
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026911"
---
# <a name="sysdmdbxtpcheckpointfiles-transact-sql"></a>sys.dm_db_xtp_checkpoint_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Muestra información sobre los archivos de puntos de comprobación, incluidos el tamaño de archivo, la ubicación física y el identificador de transacción.  
  
> **NOTA:** El punto de comprobación actual que no ha cerrado, la columna de estado de s`ys.dm_db_xtp_checkpoint_files` será UNDER CONSTRUCTION para los nuevos archivos. Un punto de comprobación se cierra automáticamente cuando no hay suficientes crecimiento del registro de transacciones desde el último punto de comprobación o si emite el `CHECKPOINT` comando ([CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)).  
  
 Un grupo de archivos optimizados para memoria utiliza internamente archivos de solo anexar para almacenar las filas insertadas y eliminadas para las tablas en memoria. Hay dos tipos de archivos: Un archivo de datos contiene las filas insertadas mientras que un archivo delta contiene referencias a las filas eliminadas. 
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] es sustancialmente diferente de las versiones más recientes y se explica inferior en el tema en [SQL Server 2014](#bkmk_2014).  
  
 Para obtener más información, consulte [crear y administrar el almacenamiento para objetos con optimización para memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md).  
  
##  <a name="bkmk_2016"></a> [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] y versiones posteriores  
 En la tabla siguiente se describe las columnas para `sys.dm_db_xtp_checkpoint_files`, empezando por **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]** .  
  
|Nombre de columna|Type|Descripción|  
|-----------------|----------|-----------------|  
|container_id|**int**|Identificador del contenedor (representado como un archivo de tipo FILESTREAM en sys.database_files) del que forma parte el archivo de datos o delta. Combinaciones con file_id en [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).|  
|container_guid|**uniqueidentifier**|GUID del contenedor, que forma parte del archivo raíz, datos o delta. Combinaciones con file_guid en la tabla sys.database_files.|  
|checkpoint_file_id|**uniqueidentifier**|GUID del archivo de punto de comprobación.|  
|relative_file_path|**nvarchar(256)**|Ruta de acceso del archivo relativa al contenedor se asigna a.|  
|file_type|**smallint**|-1 para gratuitos<br /><br /> 0 para el archivo de datos.<br /><br /> 1 para el archivo DELTA.<br /><br /> 2 para el archivo raíz<br /><br /> 3 para el archivo de datos de gran tamaño|  
|file_type_desc|**nvarchar(60)**|Archivos de gratis, todo ello mantenerlos como libre están disponibles para la asignación. Archivos gratuita pueden variar de tamaño según las necesidades previstas por el sistema. El tamaño máximo es 1GB.<br /><br /> DATOS: los archivos de datos contienen las filas que se han insertado en las tablas optimizadas para memoria.<br /><br /> DELTA - archivos Delta contienen referencias a las filas de los archivos de datos que se han eliminado.<br /><br /> ROOT - archivos raíz contienen los metadatos del sistema para los objetos compilados de forma nativa y optimizadas para memoria.<br /><br /> DATOS de gran tamaño: grandes archivos de datos contienen los valores insertados en (columnas varchar y varbinary (max), así como los segmentos de columna que forman parte de los índices de almacén de columnas en tablas optimizadas para memoria.|  
|internal_storage_slot|**int**|El índice del archivo en la matriz de almacenamiento interno. NULL para la raíz o de estado que no sea 1.|  
|checkpoint_pair_file_id|**uniqueidentifier**|Archivo de datos correspondientes o DELTA. NULL para la raíz.|  
|file_size_in_bytes|**bigint**|Tamaño del archivo en el disco.|  
|file_size_used_in_bytes|**bigint**|Para los pares de archivos de punto de comprobación que todavía se están llenando, esta columna se actualizará después del punto de comprobación siguiente.|  
|logical_row_count|**bigint**|Para los datos, el número de filas insertadas.<br /><br /> Delta, número de filas se elimina después de contabilidad para la tabla de destino.<br /><br /> Para la raíz, es NULL.|  
|state|**smallint**|0 - CREADOS PREVIAMENTE<br /><br /> 1: EN CONSTRUCCIÓN<br /><br /> 2 - ACTIVE<br /><br /> 3 - COMBINAR DESTINO<br /><br /> 8 - ESPERANDO EL TRUNCAMIENTO DEL REGISTRO|  
|state_desc|**nvarchar(60)**|PRECREATED: un número de archivos de punto de comprobación se preasignan para minimizar o eliminar cualquier espera para asignar nuevos archivos mientras se ejecutan las transacciones. Los archivos previamente creados pueden variar de tamaño, según las necesidades estimadas de la carga de trabajo, pero no contienen ningún dato. Se trata de una sobrecarga de almacenamiento en bases de datos con un grupo de archivos MEMORY_OPTIMIZED_DATA.<br /><br /> EN construcción - estos archivos de punto de control están en construcción, lo que significa que se están actualizando en función de los registros generados por la base de datos y aún no forman parte de un punto de control.<br /><br /> ACTIVE: contienen las filas insertadas y eliminadas de puntos de control cerrados anteriores. Contienen el contenido de las tablas que se lee de área en la memoria antes de aplicar la parte activa del registro de transacciones en el reinicio de la base de datos. Se espera que el tamaño de estos archivos de punto de comprobación para ser de aproximadamente 2 x el tamaño en memoria de tablas optimizadas para memoria, suponiendo que la operación de combinación es mantenerse al día con la carga de trabajo transaccional.<br /><br /> DESTINO de mezcla: el destino de las operaciones de combinación: estos archivos de punto de comprobación almacenar las filas de datos consolidados de los archivos de origen que se han identificado por la directiva de combinación. Una vez instalada la mezcla, TARGET MERGE cambia al estado ACTIVE.<br /><br /> En espera de TRUNCAMIENTO del registro: una vez que se ha instalado la combinación y el CFP de combinar destino forma parte de un punto de comprobación durable, la transición de archivos mezcla punto de control de origen a este estado. Archivos en este estado son necesarios para el correcto funcionamiento de la base de datos con la tabla optimizada para memoria.  Por ejemplo, para recuperarse de un punto de comprobación durable para ir a un momento anterior en el tiempo.|  
|lower_bound_tsn|**bigint**|Límite inferior de la transacción en el archivo. null si no está en estado (1, 3).|  
|upper_bound_tsn|**bigint**|Límite superior de la transacción en el archivo. null si no está en estado (1, 3).|  
|begin_checkpoint_id|**bigint**|Id. del punto de comprobación de inicio.|  
|end_checkpoint_id|**bigint**|Id. del punto de comprobación final.|  
|last_updated_checkpoint_id|**bigint**|Id. del último punto de comprobación que actualizar este archivo.|  
|encryption_status|**smallint**|0, 1, 2|  
|encryption_status_desc|**nvarchar(60)**|0 = > UNENCRTPTED<br /><br /> 1 = > CIFRADA CON LA CLAVE 1<br /><br /> 2 = > CIFRADA CON LA CLAVE 2. Válido únicamente para los archivos activos.|  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 En la tabla siguiente se describe las columnas para `sys.dm_db_xtp_checkpoint_files`, para **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** .  
  
|Nombre de columna|Type|Descripción|  
|-----------------|----------|-----------------|  
|container_id|**int**|Identificador del contenedor (representado como un archivo de tipo FILESTREAM en sys.database_files) del que forma parte el archivo de datos o delta. Combinaciones con file_id en [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).|  
|container_guid|**uniqueidentifier**|GUID del contenedor del que forma parte el archivo de datos o delta.|  
|checkpoint_file_id|**GUID**|Identificador del archivo de datos o delta.|  
|relative_file_path|**nvarchar(256)**|Ruta de acceso al archivo de datos o delta, con respecto a la ubicación del contenedor.|  
|file_type|**tinyint**|0 para el archivo de datos.<br /><br /> 1 para el archivo delta.<br /><br /> Es NULL si la columna state está establecida en 7.|  
|file_type_desc|**nvarchar(60)**|El tipo de archivo: DATA_FILE, DELTA_FILE o NULL si la columna state está establecida en 7.|  
|internal_storage_slot|**int**|El índice del archivo en la matriz de almacenamiento interno. Es NULL si la columna state está establecida en 2 o 3.|  
|checkpoint_pair_file_id|**uniqueidentifier**|Archivo de datos o delta correspondiente.|  
|file_size_in_bytes|**bigint**|Tamaño del archivo que se usa. Es NULL si la columna state está establecida en 5, 6 o 7.|  
|file_size_used_in_bytes|**bigint**|Tamaño usado del archivo que se emplea. Es NULL si la columna state está establecida en 5, 6 o 7.<br /><br /> Para los pares de archivos de punto de comprobación que todavía se están llenando, esta columna se actualizará después del punto de comprobación siguiente.|  
|inserted_row_count|**bigint**|Número de filas del archivo de datos.|  
|deleted_row_count|**bigint**|Número de filas eliminadas del archivo delta.|  
|drop_table_deleted_row_count|**bigint**|Número de filas de los archivos de datos afectados por una operación de quitar tabla. Se aplica a los archivos de datos cuando la columna state es igual a 1.<br /><br /> Muestra los números de filas eliminadas de las tablas quitadas. Las estadísticas drop_table_deleted_row_count se compilan una vez que se completa la recolección de elementos no utilizados de memoria de las filas de las tablas quitadas y cuando se toma un punto de comprobación. Si reinicia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antes de que las estadísticas de tablas quitadas se reflejen en esta columna, se actualizarán las estadísticas como parte de la recuperación. El proceso de recuperación no carga filas de tablas quitadas. Las estadísticas de tablas quitadas se compilan durante la fase de carga y se muestran en esta columna cuando se completa la recuperación.|  
|state|**int**|0 - CREADOS PREVIAMENTE<br /><br /> 1: EN CONSTRUCCIÓN<br /><br /> 2 - ACTIVE<br /><br /> 3 - COMBINAR DESTINO<br /><br /> 4 - COMBINADO ORIGEN<br /><br /> 5 - REQUIERE FOR BACKUP/HA<br /><br /> 6: EN TRANSICIÓN A OBJETOS DE DESECHO<br /><br /> 7 - MARCADOR DE EXCLUSIÓN|  
|state_desc|**nvarchar(60)**|PRECREATED: un pequeño conjunto de pares de archivos delta y de datos, también conocido como pares de archivos de punto de comprobación (CFP) se conservan previamente asignados para minimizar o eliminar cualquier espera para asignar nuevos archivos mientras se ejecutan las transacciones. Son de tamaño completo con un tamaño de archivo de datos de 128 MB y un tamaño de archivo delta de 8 MB pero no contienen ningún dato. El número de CFP se calcula como el número de procesadores o programadores lógicos (uno por núcleo, sin valor máximo) con un mínimo de 8. Se trata de una sobrecarga de almacenamiento fija en bases de datos con tablas optimizadas para memoria.<br /><br /> UNDER CONSTRUCTION: conjunto de CFP que almacenan recién había insertado y posiblemente eliminadas las filas de datos desde el último punto de comprobación.<br /><br /> ACTIVE: contienen las filas insertadas y eliminadas de puntos de comprobación cerrados anteriores. Estos CFP contienen todas las filas insertadas y eliminadas necesarias antes de aplicar la parte activa del registro de transacciones en el reinicio de la base de datos. El tamaño de estos CFP será aproximadamente el doble del tamaño en memoria de las tablas optimizadas para memoria, siempre y cuando la operación de combinación esté actualizada con la carga de trabajo transaccional.<br /><br /> DESTINO de mezcla: el CFP almacena las filas de datos consolidados de los CFP identificados por la directiva de combinación. Una vez instalada la mezcla, TARGET MERGE cambia al estado ACTIVE.<br /><br /> ORIGEN combinado: una vez que la operación de combinación está instalado, los CFP de origen se marcan como MERGED SOURCE. Tenga en cuenta que el evaluador de la directiva de mezcla puede identificar varias mezclas pero un CFP solo puede participar en una operación de mezcla.<br /><br /> REQUIERE FOR BACKUP/HA: una vez que se ha instalado la combinación y el CFP de destino de combinación es parte del punto de comprobación durable, la mezcla CFP de origen a este estado. Los CFP que están en este estado son necesarios para el correcto funcionamiento de la base de datos con tablas optimizadas para memoria.  Por ejemplo, para recuperarse de un punto de comprobación durable para ir a un momento anterior en el tiempo. Un CFP se puede marcar para la recolección de elementos no utilizados una vez que el punto de truncamiento del registro sobrepasa los límites de su intervalo de transacción.<br /><br /> IN TRANSITION TO TOMBSTONE: estos CFP no son necesarias para el motor de OLTP en memoria y puede hacer su recolección. Este estado indica que estos CFP están esperando que el subproceso de fondo haga la transición al estado siguiente, que es TOMBSTONE.<br /><br /> Marcador de exclusión: estos CFP están esperando sea recolectado por el recolector de elementos no utilizados de filestream. ([sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md))|  
|lower_bound_tsn|**bigint**|El límite inferior de las transacciones contenidas en el archivo. Es NULL si la columna state no tiene el valor 2, 3 o 4.|  
|upper_bound_tsn|**bigint**|El límite superior de las transacciones contenidas en el archivo. Es NULL si la columna state no tiene el valor 2, 3 o 4.|  
|last_backup_page_count|**int**|Recuento de páginas lógicas que se determina en la última copia de seguridad. Se aplica cuando la columna state está establecida en 2, 3, 4 o 5. Es NULL si no se conoce el recuento de páginas.|  
|delta_watermark_tsn|**int**|Transacción del último punto de comprobación que escribió en este archivo delta. Es el límite para el archivo delta.|  
|last_checkpoint_recovery_lsn|**nvarchar(23)**|Número de secuencia de registro de recuperación del último punto de comprobación que todavía necesita el archivo.|  
|tombstone_operation_lsn|**nvarchar(23)**|El archivo se eliminará una vez que tombstone_operation_lsn esté detrás del número de secuencia de registro del truncamiento del registro.|  
|logical_deletion_log_block_id|**bigint**|Solo se aplica al estado 5.|  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso `VIEW DATABASE STATE` en el servidor.  
  
## <a name="use-cases"></a>Casos de uso  
 Puede calcular el almacenamiento utilizado por OLTP en memoria como sigue:  
  
```  
-- total storage used by In-Memory OLTP  
SELECT SUM (file_size_in_bytes)/(1024*1024) as file_size_in_MB  
FROM sys.dm_db_xtp_checkpoint_files  
```  
  
  
Para ver un desglose del uso del almacenamiento por estado y tipo de archivo ejecute la siguiente consulta:
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(file_size_in_bytes) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  

  
## <a name="see-also"></a>Vea también  
 [Vistas de administración dinámica de tabla optimizado para memoria &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
