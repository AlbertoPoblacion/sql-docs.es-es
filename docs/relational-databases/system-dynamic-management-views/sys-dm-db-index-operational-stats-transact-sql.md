---
title: sys.dm_db_index_operational_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_operational_stats
- sys.dm_db_index_operational_stats_TSQL
- sys.dm_db_index_operational_stats
- dm_db_index_operational_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_operational_stats dynamic management function
ms.assetid: 13adf2e5-2150-40a6-b346-e74a33ce29c6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3d52fb28dd1093b81d8a46ec6a8d2dd3cce49807
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62684293"
---
# <a name="sysdmdbindexoperationalstats-transact-sql"></a>sys.dm_db_index_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve actuales de E/S de bajo nivel, el bloqueo temporal y la actividad de método de acceso para cada partición de una tabla o índice en la base de datos.    
    
 Los índices con optimización para memoria no aparecen en esta DMV.    
    
> [!NOTE]    
>  **Sys.dm_db_index_operational_stats** no devuelve información acerca de los índices optimizados para memoria. Para obtener información sobre el uso de índices optimizados para memoria, vea [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).    
        
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Sintaxis    
    
```    
    
sys.dm_db_index_operational_stats (    
    { database_id | NULL | 0 | DEFAULT }    
  , { object_id | NULL | 0 | DEFAULT }    
  , { index_id | 0 | NULL | -1 | DEFAULT }    
  , { partition_number | NULL | 0 | DEFAULT }    
)    
```    
    
## <a name="arguments"></a>Argumentos    
 *database_id* | NULL | 0 | DEFAULT    
 Identificador de la base de datos. *database_id* es **smallint**. Las entradas válidas son el número de identificador de una base de datos, NULL, 0 y DEFAULT. El valor predeterminado es 0. NULL, 0 y DEFAULT son valores equivalentes en este contexto.    
    
 Especifique NULL para devolver información de todas las bases de datos en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si especifica NULL para *database_id*, también debe especificar NULL para *object_id*, *index_id*, y *partition_number*.    
    
 La función integrada [DB_ID](../../t-sql/functions/db-id-transact-sql.md) se pueden especificar.    
    
 *object_id* | NULL | 0 | VALOR PREDETERMINADO    
 Identificador de objeto de la tabla o vista donde está activado el índice. *object_id* es **int**.    
    
 Las entradas válidas son el número de identificador de una tabla o vista, NULL, 0 y DEFAULT. El valor predeterminado es 0. NULL, 0 y DEFAULT son valores equivalentes en este contexto.    
    
 Especifique NULL para devolver información en memoria caché de todas las tablas y vistas de la base de datos especificada. Si especifica NULL para *object_id*, también debe especificar NULL para *index_id* y *partition_number*.    
    
 *index_id* | 0 | NULL | -1 | VALOR PREDETERMINADO    
 Id. del índice. *index_id* es **int**. Las entradas válidas son el número de identificación de un índice, 0 si *object_id* es un montón, NULL, -1 y DEFAULT. El valor predeterminado es -1. NULL, -1 y DEFAULT son valores equivalentes en este contexto.    
    
 Especifique NULL para devolver información en memoria caché de todos los índices de una tabla o vista base. Si especifica NULL para *index_id*, también debe especificar NULL para *partition_number*.    
    
 *partition_number* | NULL | 0 | VALOR PREDETERMINADO    
 Número de partición en el objeto. *partition_number* es **int**. Las entradas válidas son el *partion_number* de un índice o montón, NULL, 0 o DEFAULT. El valor predeterminado es 0. NULL, 0 y DEFAULT son valores equivalentes en este contexto.    
    
 Especifique NULL para devolver información en memoria caché de todas las particiones del índice o montón.    
    
 *partition_number* está basado en 1. Un montón o un índice sin particiones tiene *partition_number* establecido en 1.    
    
## <a name="table-returned"></a>Tabla devuelta    
    
|Nombre de columna|Tipo de datos|Descripción|    
|-----------------|---------------|-----------------|    
|**database_id**|**smallint**|Id. de la base de datos.|    
|**object_id**|**int**|Identificador de la tabla o vista.|    
|**index_id**|**int**|Identificador del índice o montón.<br /><br /> 0 = Montón| 
|**partition_number**|**int**|Número de partición en base 1 en el índice o montón.| 
|**hobt_id**|**bigint**|**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (hasta la [versión actual](https://go.microsoft.com/fwlink/p/?LinkId=299658)) [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Id. del montón de datos o conjunto de filas de árbol B que realiza el seguimiento de los datos internos para un índice de almacén de columnas.<br /><br /> NULL: esto no es un conjunto de filas del almacén de columnas interno.<br /><br /> Para obtener más información, consulte [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)|       
|**leaf_insert_count**|**bigint**|Recuento acumulado de inserciones en el nivel hoja.|    
|**leaf_delete_count**|**bigint**|Recuento acumulado de eliminaciones en el nivel hoja. leaf_delete_count sólo se incrementa para los registros eliminados que no están marcados como fantasma en primer lugar. Para los registros eliminados se reflejó en primer lugar, **leaf_ghost_count** se incrementa en su lugar.|    
|**leaf_update_count**|**bigint**|Recuento acumulado de actualizaciones en el nivel hoja.|    
|**leaf_ghost_count**|**bigint**|Recuento acumulado de filas en el nivel hoja marcadas como eliminadas, pero que aún no se han quitado. Este recuento no incluye los registros que se eliminan inmediatamente sin que se marcara como fantasma. Estas filas se quitan mediante un subproceso de limpieza a intervalos establecidos. En este valor no se incluyen las filas retenidas a causa de una transacción de aislamiento de instantánea pendiente.|    
|**nonleaf_insert_count**|**bigint**|Recuento acumulado de inserciones por encima del nivel hoja.<br /><br /> 0 = Montón o almacén de columnas|    
|**nonleaf_delete_count**|**bigint**|Recuento acumulado de eliminaciones por encima del nivel hoja.<br /><br /> 0 = Montón o almacén de columnas|    
|**nonleaf_update_count**|**bigint**|Recuento acumulado de actualizaciones por encima del nivel hoja.<br /><br /> 0 = Montón o almacén de columnas|    
|**leaf_allocation_count**|**bigint**|Recuento acumulado de asignaciones de página en el nivel hoja en el índice o el montón.<br /><br /> En un índice, una asignación de página corresponde a una división de página.|    
|**nonleaf_allocation_count**|**bigint**|Recuento acumulado de asignaciones de página ocasionadas por divisiones de página por encima del nivel hoja.<br /><br /> 0 = Montón o almacén de columnas|    
|**leaf_page_merge_count**|**bigint**|Recuento acumulado de combinaciones de página en el nivel hoja. Siempre es 0 para el índice de almacén de columnas.|    
|**nonleaf_page_merge_count**|**bigint**|Recuento acumulado de combinaciones de página por encima del nivel hoja.<br /><br /> 0 = Montón o almacén de columnas|    
|**range_scan_count**|**bigint**|Recuento acumulado de recorridos de tabla e intervalo iniciados en el índice o el montón.|    
|**singleton_lookup_count**|**bigint**|Recuento acumulado de recuperaciones de filas únicas del índice o montón.|    
|**forwarded_fetch_count**|**bigint**|Recuento de filas que se capturan mediante un registro de reenvío.<br /><br /> 0 = Índices|    
|**lob_fetch_in_pages**|**bigint**|Recuento acumulado de páginas de objetos grandes (LOB) recuperadas desde la unidad de asignación LOB_DATA. Estas páginas contienen datos que se almacenan en columnas de tipo **texto**, **ntext**, **imagen**, **varchar (max)**, **(nvarchar max)**, **varbinary (max)**, y **xml**. Para obtener más información, vea [Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|    
|**lob_fetch_in_bytes**|**bigint**|Recuento acumulado de bytes de datos de LOB recuperados.|    
|**lob_orphan_create_count**|**bigint**|Recuento acumulado de valores de LOB huérfanos creados para operaciones masivas.<br /><br /> 0 = Índice no clúster|    
|**lob_orphan_insert_count**|**bigint**|Recuento acumulado de valores de LOB huérfanos insertados durante operaciones masivas.<br /><br /> 0 = Índice no clúster|    
|**row_overflow_fetch_in_pages**|**bigint**|Recuento acumulado de páginas de datos de desbordamiento de fila recuperadas desde la unidad de asignación ROW_OVERFLOW_DATA.<br /><br /> Estas páginas contienen datos almacenados en columnas de tipo **varchar**, **nvarchar (n)**, **varbinary**, y **sql_variant** que ha sido inserción no consecutiva.|    
|**row_overflow_fetch_in_bytes**|**bigint**|Recuento acumulado de bytes de datos de desbordamiento de fila recuperados.|    
|**column_value_push_off_row_count**|**bigint**|Recuento acumulado de valores de columna de datos de LOB y datos de desbordamiento de fila que se han insertado de manera no consecutiva para que una fila insertada o actualizada entre en una página.|    
|**column_value_pull_in_row_count**|**bigint**|Recuento acumulado de valores de columna de datos de LOB y datos de desbordamiento de fila que se han extraído de manera consecutiva. Esto ocurre cuando una operación de actualización libera espacio en un registro y proporciona una oportunidad para trasladar uno o más valores de manera no consecutiva de las unidades de asignación LOB_DATA o ROW_OVERFLOW_DATA a la unidad de asignación IN_ROW_DATA.|    
|**row_lock_count**|**bigint**|Número acumulado de bloqueos de fila solicitados.|    
|**row_lock_wait_count**|**bigint**|Número acumulado de veces que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado en un bloqueo de fila.|    
|**row_lock_wait_in_ms**|**bigint**|Número total de milisegundos que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado en un bloqueo de fila.|    
|**page_lock_count**|**bigint**|Número acumulado de bloqueos de página solicitados.|    
|**page_lock_wait_count**|**bigint**|Número acumulado de veces que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado en un bloqueo de página.|    
|**page_lock_wait_in_ms**|**bigint**|Número total de milisegundos que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado en un bloqueo de página.|    
|**index_lock_promotion_attempt_count**|**bigint**|Número acumulado de veces que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha intentado concentrar bloqueos.|    
|**index_lock_promotion_count**|**bigint**|Número acumulado de veces que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha concentrado bloqueos.|    
|**page_latch_wait_count**|**bigint**|Número acumulado de veces que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado a causa de la contención de bloqueos temporales.|    
|**page_latch_wait_in_ms**|**bigint**|Número acumulado de milisegundos que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado a causa de la contención de bloqueos temporales.|    
|**page_io_latch_wait_count**|**bigint**|Número acumulado de veces que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado en un bloqueo temporal de E/S de páginas.|    
|**page_io_latch_wait_in_ms**|**bigint**|Número acumulado de milisegundos que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha esperado en un bloqueo temporal de E/S de páginas.|    
|**tree_page_latch_wait_count**|**bigint**|Subconjunto de **page_latch_wait_count** que incluye solamente las páginas de árbol B de nivel superior. Siempre es 0 para un índice de montón o de almacén de columnas.|    
|**tree_page_latch_wait_in_ms**|**bigint**|Subconjunto de **page_latch_wait_in_ms** que incluye solamente las páginas de árbol B de nivel superior. Siempre es 0 para un índice de montón o de almacén de columnas.|    
|**tree_page_io_latch_wait_count**|**bigint**|Subconjunto de **page_io_latch_wait_count** que incluye solamente las páginas de árbol B de nivel superior. Siempre es 0 para un índice de montón o de almacén de columnas.|    
|**tree_page_io_latch_wait_in_ms**|**bigint**|Subconjunto de **page_io_latch_wait_in_ms** que incluye solamente las páginas de árbol B de nivel superior. Siempre es 0 para un índice de montón o de almacén de columnas.|    
|**page_compression_attempt_count**|**bigint**|Número de páginas que se evaluaron para la compresión en el nivel de página para particiones específicas de una tabla, un índice o una vista indizada. Incluye páginas que no se comprimieron porque no se consiguieron ahorros de espacio significativos. Siempre es 0 para el índice de almacén de columnas.|    
|**page_compression_success_count**|**bigint**|Número de páginas de datos que se comprimieron utilizando la compresión de páginas para particiones específicas de una tabla, un índice o una vista indizada. Siempre es 0 para el índice de almacén de columnas.|    
    
## <a name="remarks"></a>Comentarios    
 Este objeto de administración dinámica no acepta parámetros correlacionado de CROSS APPLY y OUTER APPLY.    
    
 Puede usar **sys.dm_db_index_operational_stats** para realizar el seguimiento de la cantidad de tiempo que los usuarios deben esperar para leer o escribir en una tabla, índice o partición e identificar las tablas o índices que se están produciendo la actividad de E/S importante o "n" zonas.    
    
 Use las columnas siguientes para identificar áreas de contención.    
    
 **Para analizar un patrón común de acceso a la partición de tabla o índice**, utilice estas columnas:    
    
-   **leaf_insert_count**    
    
-   **leaf_delete_count**    
    
-   **leaf_update_count**    
    
-   **leaf_ghost_count**    
    
-   **range_scan_count**    
    
-   **singleton_lookup_count**    
    
 Para identificar la contención de bloqueos y bloqueos temporales, utilice estas columnas:    
    
-   **page_latch_wait_count** y **page_latch_wait_in_ms**    
    
     Estas columnas indican si existe una contención de bloqueos temporales en el índice o montón, y la importancia de la misma.    
    
-   **row_lock_count** y **page_lock_count**    
    
     Estas columnas indican cuántas veces el [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha intentado adquirir bloqueos de página y fila.    
    
-   **row_lock_wait_in_ms** y **page_lock_wait_in_ms**    
    
     Estas columnas indican si existe una contención de bloqueos en el índice o montón y la importancia de la misma.    
    
 **Para analizar las estadísticas de E/s físicas en una partición de índice o montón**    
    
-   **page_io_latch_wait_count** y **page_io_latch_wait_in_ms**    
    
     Estas columnas indican si las operaciones de E/S físicas tuvieron problemas para traer las páginas de índice o montón a memoria y cuántas operaciones de E/S tuvieron problemas.    
    
## <a name="column-remarks"></a>Comentarios de columna    
 Los valores de **lob_orphan_create_count** y **lob_orphan_insert_count** siempre deben ser iguales.    
    
 El valor de las columnas **lob_fetch_in_pages** y **lob_fetch_in_bytes** puede ser mayor que cero para índices no clúster que contienen una o varias columnas LOB como columnas incluidas. Para más información, consulte [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md). De forma similar, el valor de las columnas **row_overflow_fetch_in_pages** y **row_overflow_fetch_in_bytes** puede ser mayor que 0 para los índices no clúster si el índice contiene columnas que se pueden insertar no consecutiva.    
    
## <a name="how-the-counters-in-the-metadata-cache-are-reset"></a>Restablecer los contadores en la memoria caché de metadatos    
 Los datos devueltos por **sys.dm_db_index_operational_stats** existe solo mientras está disponible el objeto de caché de metadatos que representa el índice o montón. Estos datos nunca son permanentes ni transaccionalmente coherentes. Esto significa que no se pueden utilizar estos contadores para determinar si se ha utilizado un índice o cuándo se usó por última vez. Para obtener información acerca de esto, consulte [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md).    
    
 Los valores de cada columna se establecerán en cero siempre que los metadatos del montón o índice se incorporen a la memoria caché de metadatos y las estadísticas se acumulen hasta que el objeto de la memoria caché se quite de la memoria caché de metadatos. Por tanto, es probable que un índice o montón activo tenga siempre sus metadatos en la memoria caché, y los recuentos acumulados puedan reflejar la actividad desde la última vez que se inició la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los metadatos de un índice o montón menos activo entrarán y saldrán de la memoria caché según se utilicen. Como resultado, sus valores pueden estar disponibles o no. La eliminación de un índice hará que las estadísticas correspondientes se quiten de la memoria y que la función ya no informe de las mismas. Otras operaciones DDL en el índice pueden hacer que el valor de las estadísticas se restablezca en cero.    
    
## <a name="using-system-functions-to-specify-parameter-values"></a>Usar funciones del sistema para especificar valores de parámetros    
 Puede usar el [!INCLUDE[tsql](../../includes/tsql-md.md)] funciones [DB_ID](../../t-sql/functions/db-id-transact-sql.md) y [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md) para especificar un valor para el *database_id* y *object_id* parámetros. Sin embargo, el envío de valores no válidos a estas funciones puede provocar resultados no deseados. Asegúrese de que se devuelva un identificador válido cuando utilice DB_ID u OBJECT_ID. Para obtener más información, vea la sección Comentarios de [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).    
    
## <a name="permissions"></a>Permisos    
 Necesita los siguientes permisos:    
    
-   Permiso CONTROL en el objeto especificado en la base de datos    
    
-   Permiso VIEW DATABASE STATE para devolver información sobre todos los objetos dentro de la base de datos especificada mediante el carácter comodín de objeto @*object_id* = NULL    
    
-   Permiso VIEW SERVER STATE para devolver información acerca de todas las bases de datos, utilizando el carácter comodín de base de datos @*database_id* = NULL    
    
 El permiso VIEW DATABASE STATE permite devolver todos los objetos de la base de datos, independientemente de los permisos CONTROL denegados en objetos específicos.    
    
 Si se deniega el permiso VIEW DATABASE STATE, no se puede devolver ningún objeto de la base de datos, independientemente de que se hayan concedido permisos CONTROL a objetos específicos. También, cuando el carácter comodín de base de datos @*database_id*= se especifica NULL, se omite la base de datos.    
    
 Para obtener más información, consulte [funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).    
    
## <a name="examples"></a>Ejemplos    
    
### <a name="a-returning-information-for-a-specified-table"></a>A. Devolver información de una tabla especificada    
 En el siguiente ejemplo se devuelve información de todos los índices y particiones de la tabla `Person.Address` en la base de datos [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La ejecución de esta consulta requiere, como mínimo, permiso CONTROL en la tabla `Person.Address`.    
    
> [!IMPORTANT]    
>  Cuando utilice las funciones DB_ID y OBJECT_ID de [!INCLUDE[tsql](../../includes/tsql-md.md)] para devolver un valor de parámetro, asegúrese de que siempre se devuelva un identificador válido. Si el nombre de objeto o base de datos no se puede encontrar, por ejemplo, cuando no existe o se ha escrito incorrectamente, las dos funciones devolverán NULL. La función **sys.dm_db_index_operational_stats** interpreta NULL como un valor de carácter comodín que especifica todas las bases de datos o todos los objetos. Puesto que ésta puede ser una operación accidental, los ejemplos de esta sección demuestran una forma segura para determinar los Id. de bases de datos y objetos.    
    
```    
DECLARE @db_id int;    
DECLARE @object_id int;    
SET @db_id = DB_ID(N'AdventureWorks2012');    
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');    
IF @db_id IS NULL     
  BEGIN;    
    PRINT N'Invalid database';    
  END;    
ELSE IF @object_id IS NULL    
  BEGIN;    
    PRINT N'Invalid object';    
  END;    
ELSE    
  BEGIN;    
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);    
  END;    
GO    
    
```    
    
### <a name="b-returning-information-for-all-tables-and-indexes"></a>b. Devolver información de todas las tablas e índices    
 En el siguiente ejemplo se devuelve información de todas las tablas e índices en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para ejecutar esta consulta requiere el permiso VIEW SERVER STATE.    
    
```    
SELECT * FROM sys.dm_db_index_operational_stats( NULL, NULL, NULL, NULL);    
GO    
    
```    
    
## <a name="see-also"></a>Vea también    
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)     
 [Funciones y vistas de administración dinámica relacionadas con índices &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)     
 [Supervisión y optimización del rendimiento](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)     
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)     
 [sys.dm_os_latch_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)     
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)     
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)     
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)    
    
  

