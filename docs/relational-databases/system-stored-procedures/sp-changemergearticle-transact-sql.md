---
title: sp_changemergearticle (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/09/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergearticle_TSQL
- sp_changemergearticle
helpviewer_keywords:
- sp_changemergearticle
ms.assetid: 0dc3da5c-4af6-45be-b5f0-074da182def2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e9d2baf65dedf1116a85f7271b1929e0ead4ca23
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493719"
---
# <a name="spchangemergearticle-transact-sql"></a>sp_changemergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia las propiedades de un artículo de mezcla. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_changemergearticle [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publication = ] 'publication'` Es el nombre de la publicación en el que existe el artículo. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @article = ] 'article'` Es el nombre del artículo que se va a cambiar. *artículo* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @property = ] 'property'` Es la propiedad para cambiar para el artículo dado y la publicación. *propiedad* es **nvarchar (30)**, y puede ser uno de los valores que aparecen en la tabla.  
  
`[ @value = ] 'value'` Es el nuevo valor para la propiedad especificada. *valor* es **nvarchar (1000)**, y puede ser uno de los valores que aparecen en la tabla.  
  
 En esta tabla se describen las propiedades de los artículos y los valores de esas propiedades.  
  
|Property|Valores|Descripción|  
|--------------|------------|-----------------|  
|**allow_interactive_resolver**|**true**|Habilita el uso de un solucionador interactivo para el artículo.|  
||**False**|Deshabilita el uso de un solucionador interactivo para el artículo.|  
|**article_resolver**||Solucionador personalizado para el artículo. Solo se aplica a un artículo de tabla.|  
|**check_permissions** (mapa de bits)|**0x00**|Los permisos de tabla no se comprueban.|  
||**0x10**|Los permisos de tabla se comprueban en el publicador antes de que las instrucciones INSERT realizadas en el suscriptor se apliquen en el publicador.|  
||**0x20**|Los permisos de tabla se comprueban en el publicador antes de que las instrucciones UPDATE realizadas en el suscriptor se apliquen en el publicador.|  
||**0x40**|Los permisos de tabla se comprueban en el publicador antes de que las instrucciones DELETE realizadas en el suscriptor se apliquen en el publicador.|  
|**column_tracking**|**true**|Activa el seguimiento por columna. Solo se aplica a un artículo de tabla.<br /><br /> Nota: El seguimiento por columna no se puede utilizar cuando se publican tablas con más de 246 columnas.|  
||**False**|Desactiva el seguimiento por columna y deja la detección de conflictos a nivel de fila. Solo se aplica a un artículo de tabla.|  
|**compensate_for_errors**|**true**|Las acciones de compensación se ejecutan cuando se producen errores durante la sincronización. Para obtener más información, consulte [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
||**False**|Las acciones de compensación no se ejecutan; éste es el comportamiento predeterminado. Para obtener más información, consulte [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).<br /><br /> **\*\* Importante \* \***  aunque estén fuera de convergencia, tan pronto como los corrija los errores, puede que aparezcan datos en las filas afectadas, se pueden aplicar los cambios y datos convergerán. Si la tabla de origen para un artículo ya está publicada en otra publicación y, a continuación, el valor de *compensate_for_errors* debe ser el mismo para ambos artículos.|  
|**creation_script**||Ruta de acceso y nombre de un script opcional del esquema del artículo que se utiliza para crear el artículo en la base de datos de suscripciones.|  
|**delete_tracking**|**true**|Las instrucciones DELETE se replican; éste es el comportamiento predeterminado.|  
||**False**|Las instrucciones DELETE no se replican.<br /><br /> **\*\* Importante \* \***  configuración **delete_tracking** a **false** resultados de no convergencia y eliminadas las filas deben quitarse manualmente.|  
|**description**||Entrada descriptiva del artículo.|  
|**destination_owner**||Nombre del propietario del objeto en la base de datos de suscripción, si no **dbo**.|  
|**identity_range**||**bigint** que especifica el tamaño del intervalo que se usará al asignar nuevos valores de identidad si el artículo tiene **identityrangemanagementoption** establecido en **automática** o **auto_identity_ intervalo** establecido en **true**. Solamente se aplica en un artículo de la tabla. Para obtener más información, vea la sección "Replicación de mezcla" de [replicar columnas de identidad](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**identityrangemanagementoption**|**manual**|Deshabilita la administración automática de intervalos de identidad. Marca las columnas de identidad utilizando NOT FOR REPLICATION para habilitar la administración manual de intervalos de identidad. Para más información, vea [Replicar columnas de identidad](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
||**Ninguno**|Deshabilita toda la administración de intervalos de identidad.|  
|**logical_record_level_conflict_detection**|**true**|Se detecta un conflicto si se realizan cambios en cualquier parte del registro lógico. Requiere que **logical_record_level_conflict_resolution** establecerse **true**.|  
||**False**|Se utiliza la detección de conflictos predeterminada tal y como especifica **column_tracking**.|  
|**logical_record_level_conflict_resolution**|**true**|Todo el registro lógico ganador reemplaza el registro lógico perdedor.|  
||**False**|Las filas ganadoras no se restringen al registro lógico.|  
|**partition_options**|**0**|El filtro para el artículo es estático o no produce un subconjunto de datos único para cada partición, es decir, es una partición "superpuesta".|  
||**1**|Las particiones se superponen y las actualizaciones del lenguaje DML realizadas en el suscriptor no pueden cambiar la partición a la que pertenece una fila.|  
||**2**|El filtro para el artículo produce particiones no superpuestas, pero varios suscriptores pueden recibir la misma partición.|  
||**3**|El filtro para el artículo produce particiones no superpuestas que son exclusivas para cada suscripción.<br /><br /> Nota: Si especifica un valor de **3** para **partition_options**, puede haber solo una suscripción para cada partición de datos de ese artículo. Si se crea una segunda partición en la que el criterio de filtrado de la nueva suscripción se resuelve en la misma partición que la suscripción existente, se quitará la suscripción existente.|  
|**pre_creation_command**|**Ninguno**|Si la tabla ya existe en el suscriptor, no se lleva a cabo ninguna acción.|  
||**delete**|Emite una eliminación basada en la cláusula WHERE del filtro de subconjunto.|  
||**drop**|Quita la tabla antes de volver a crearla.|  
||**truncate**|Trunca la tabla de destino.|  
|**processing_order**||**int** que indica el orden de procesamiento de artículos en una publicación de combinación.|  
|**pub_identity_range**||**bigint** que especifica el tamaño del intervalo asignado a un suscriptor con una suscripción de servidor si el artículo tiene **identityrangemanagementoption** establecido en **automática** o **auto_ identity_range** establecido en **true**. Este rango de identidad se reserva para que un suscriptor de republicación pueda realizar asignaciones a sus propios suscriptores. Solamente se aplica en un artículo de la tabla. Para obtener más información, vea la sección "Replicación de mezcla" de [replicar columnas de identidad](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**published_in_tran_pub**|**true**|El artículo también está publicado en una publicación transaccional.|  
||**False**|El artículo no está publicado en una publicación transaccional.|  
|**resolver_info**||Se utiliza para especificar información adicional necesaria para un solucionador personalizado. Algunos de los solucionadores de [!INCLUDE[msCoName](../../includes/msconame-md.md)] requieren que se proporcione una columna como entrada para el solucionador. **resolver_info** es **nvarchar (255)**, su valor predeterminado es null. Para obtener más información, consulte [Solucionadores basados en Microsoft COM](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md).|  
|**schema_option** (bitmap)||Para obtener más información, vea la sección Comentarios más adelante en este tema.|  
||**0x00**|Deshabilita el scripting del agente de instantáneas y utiliza el script proporcionado en **creation_script**.|  
||**0x01**|Genera el script de creación del objeto (CREATE TABLE, CREATE PROCEDURE, etc.).|  
||**0x10**|Genera el índice clúster correspondiente.|  
||**0x20**|Convierte los tipos de datos definidos por el usuario en tipos de datos base en el suscriptor. Esta opción no se puede utilizar si existe una restricción CHECK o DEFAULT en una columna de tipo definido por el usuario (UDT), si una columna UDT forma parte de la clave principal o si una columna calculada hace referencia a una columna UDT.|  
||**0x40**|Genera los índices no clúster correspondientes.|  
||**0x80**|Incluye la integridad referencial declarada para las claves principales.|  
||**0x100**|Replica los desencadenadores de usuario en un artículo de tabla, si se han definido.|  
||**0x200**|Replica restricciones FOREIGN KEY. Si la tabla a la que se hace referencia no forma parte de una publicación, no se replica ninguna restricción FOREIGN KEY en una tabla publicada.|  
||**0x400**|Replica las restricciones CHECK.|  
||**0x800**|Replica los valores predeterminados.|  
||**0x1000**|Replica la intercalación de columna.|  
||**0x2000**|Replica las propiedades extendidas asociadas con el objeto de origen del artículo publicado.|  
||**0x4000**|Replica las claves únicas si están definidas en un artículo de tabla.|  
||**0x8000**|Genera instrucciones ALTER TABLE al incluir restricciones en scripting.|  
||**0x10000**|Replica las restricciones CHECK como NOT FOR REPLICATION de manera que no se impongan durante la sincronización.|  
||**0x20000**|Replica las restricciones FOREIGN KEY como NOT FOR REPLICATION de manera que no se impongan durante la sincronización.|  
||**0x40000**|Replica grupos de archivos asociados con un índice o una tabla con particiones.|  
||**0x80000**|Replica el esquema de partición de una tabla con particiones.|  
||**0x100000**|Replica el esquema de partición de un índice con particiones.|  
||**0x200000**|Replica las estadísticas de tabla.|  
||**0x400000**|Replica los enlaces predeterminados|  
||**0x800000**|Replica los enlaces de reglas.|  
||**0x1000000**|Replica el índice de texto completo.|  
||**0x2000000**|Colecciones de esquemas XML enlazado a **xml** columnas no se replican.|  
||**0x4000000**|Replica índices en **xml** columnas.|  
||**0x8000000**|Crea esquemas que aún no existen en el suscriptor.|  
||**0x10000000**|Convierte **xml** columnas a **ntext** en el suscriptor.|  
||**0x20000000**|Convierte objetos grandes tipos de datos (**nvarchar (max)**, **varchar (max)**, y **varbinary (max)**) que se introdujeron en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a tipos de datos que son compatibles en [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
||**0x40000000**|Replica permisos.|  
||**0x80000000**|Intenta quitar dependencias a objetos que no forman parte de la publicación.|  
||**0x100000000**|Use esta opción para replicar el atributo FILESTREAM si se especifica en **varbinary (max)** columnas. No especifique esta opción si replica tablas en suscriptores de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Replicación de tablas que incluyen columnas FILESTREAM en [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] no es compatible con suscriptores, independientemente de cómo se establece esta opción de esquema. Vea la opción relacionada **0 x 800000000**.|  
||**0x200000000**|Convierte los tipos de datos de fecha y hora (**fecha**, **tiempo**, **datetimeoffset**, y **datetime2**) que se introducen en [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tipos de datos que se admiten en versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
||**0x400000000**|Replica la opción de compresión para los datos y los índices. Para obtener más información, consulte [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
||**0x800000000**|Establezca esta opción para almacenar los datos de FILESTREAM en su propio grupo de archivos en el suscriptor. Si no se establece esta opción, los datos de FILESTREAM se almacenan en el grupo de archivos predeterminado. La replicación no crea grupos de archivos; por tanto, si establece esta opción, debe crear el grupo de archivos antes de aplicar la instantánea en el suscriptor. Para obtener más información sobre cómo crear objetos antes de aplicar la instantánea, vea [ejecutar Scripts antes y después de aplicar la instantánea](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).<br /><br /> Vea la opción relacionada **0 x 100000000**.|  
||**0x1000000000**|Convierte los tipos common language runtime (CLR) definido por el usuario (UDT) en **varbinary (max)** para que las columnas de tipo UDT se pueden replicar en suscriptores que ejecutan [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||**0x2000000000**|Convierte el **hierarchyid** tipo de datos que **varbinary (max)** para que las columnas de tipo **hierarchyid** se pueden replicar en suscriptores que ejecutan [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Para obtener más información sobre cómo usar **hierarchyid** columnas en las tablas replicadas, vea [hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
||**0x4000000000**|Replica los índices filtrados de la tabla. Para obtener más información sobre los índices filtrados, vea [crear índices filtrados](../../relational-databases/indexes/create-filtered-indexes.md).|  
||**0x8000000000**|Convierte el **geography** y **geometría** tipos de datos **varbinary (max)** para que las columnas de estos tipos se pueden replicar en suscriptores que ejecutan [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||**0x10000000000**|Replica índices en columnas de tipo **geography** y **geometría**.|  
||NULL|El sistema genera automáticamente una opción de esquema válida para el artículo.|  
|**status**|**active**|Se ejecuta el script inicial de proceso para publicar la tabla.|  
||**unsynced**|El script de procesos inicial para publicar la tabla se ejecuta la próxima vez que se ejecute el Agente de instantáneas.|  
|**stream_blob_columns**|**true**|Se utiliza una optimización del flujo de datos al replicar columnas de objetos binarios grandes. No obstante, ciertas funciones de la replicación de mezcla, como los registros lógicos, pueden impedir que se utilice la optimización de flujos. *stream_blob_columns* se establece en true cuando FILESTREAM está habilitado. Esto permite que la replicación de datos FILESTREAM se realice de forma óptima y que se reduzca el uso de memoria. Para forzar los artículos de tabla FILESTREAM no usen transmisión de datos blob, establezca *stream_blob_columns* en false.<br /><br /> **\*\* Importante \* \***  habilitar esta optimización de memoria puede perjudicar el rendimiento del agente de mezcla durante la sincronización. Esta opción solo se debe utilizar al replicar columnas que contienen megabytes de datos.|  
||**False**|La optimización no se utiliza al replicar columnas de objetos binarios grandes.|  
|**subscriber_upload_options**|**0**|No existen restricciones en actualizaciones realizadas en el suscriptor con una suscripción de cliente; los cambios se cargan en el publicador. Si cambia esta propiedad puede que sea necesaria la reinicialización de suscriptores existentes.|  
||**1**|Se permiten cambios en un suscriptor con una suscripción de cliente, pero no se cargan en el publicador.|  
||**2**|No se permiten cambios en un suscriptor con una suscripción de cliente.|  
|**subset_filterclause**||Cláusula WHERE que especifica el filtrado horizontal. Solo se aplica a un artículo de tabla.<br /><br /> **\*\* Importante \* \***  por motivos de rendimiento, se recomienda no aplicar funciones a nombres de columna en las cláusulas de filtro de fila con parámetros, tales como `LEFT([MyColumn]) = SUSER_SNAME()`. Si usas [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) en una cláusula de filtro y reemplazar el valor de HOST_NAME, es posible que deba convertir tipos de datos mediante el uso de [convertir](../../t-sql/functions/cast-and-convert-transact-sql.md). Para obtener más información sobre los procedimientos recomendados para este caso, vea la sección "Reemplazar el valor de HOST_NAME ()" en [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
|**threshold**||Valor de porcentaje utilizado para los suscriptores que ejecuten [!INCLUDE[ssEW](../../includes/ssew-md.md)] o versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **umbral** controla cuándo el agente de mezcla asigna un nuevo intervalo de identidad. Si se utiliza el porcentaje de valores especificado en el umbral, el Agente de mezcla crea un nuevo intervalo de identidad. Se usa cuando **identityrangemanagementoption** está establecido en **automática** o **auto_identity_range** está establecido en **true**. Solamente se aplica en un artículo de la tabla. Para obtener más información, vea la sección "Replicación de mezcla" de [replicar columnas de identidad](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**verify_resolver_signature**|**1**|La firma digital en un solucionador personalizado se comprueba para determinar si proviene de una fuente confiable.|  
||**0**|La firma digital en un solucionador personalizado no se comprueba para determinar si proviene de una fuente confiable.|  
|NULL (predeterminado)||Devuelve la lista de valores admitidos para *propiedad*.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Confirma que la acción realizada por este procedimiento almacenado puede invalidar una instantánea existente. *force_invalidate_snapshot* es un **bit**, su valor predeterminado es **0**.  
  
 **0** especifica que los cambios realizados en el artículo de mezcla no invalidarán la instantánea no es válido. Si el procedimiento almacenado detecta que el cambio requiere una nueva instantánea, se producirá un error y no se realizarán cambios.  
  
 **1** significa que los cambios realizados en el artículo de mezcla pueden invalidar la instantánea no es válido y, si hay suscripciones existentes que requieran una nueva instantánea, concede el permiso necesario para marcar como obsoleta la instantánea existente y generado una nueva.  
  
 Vea en la sección de Notas las propiedades que, si se cambian, requieren que se genere una instantánea nueva.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Confirma que la acción realizada por este procedimiento almacenado puede requerir la reinicialización de las suscripciones existentes. *force_reinit_subscription* es un **bit**, su valor predeterminado es **0**.  
  
 **0** especifica que los cambios realizados en el artículo de mezcla no invalidarán la suscripción para reinicializarla. Si el procedimiento almacenado detecta que el cambio requiere la reinicialización de las suscripciones existentes, se producirá un error y no se realizarán cambios.  
  
 **1** hacer los cambios realizados en el artículo de mezcla que se reinicialicen las suscripciones existentes y concede permiso para que se produzca la reinicialización de suscripción.  
  
 Vea en la sección de Notas las propiedades que, si se cambian, requieren que se reinicialicen todas las suscripciones existentes.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_changemergearticle** se utiliza en la replicación de mezcla.  
  
 Dado que **sp_changemergearticle** se utiliza para cambiar las propiedades del artículo que se especificaron inicialmente mediante el uso de [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), consulte [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Para obtener más información acerca de estas propiedades.  
  
 Cambiar las propiedades siguientes requiere que se genera una nueva instantánea, y debe especificar un valor de **1** para el *force_invalidate_snapshot* parámetro:  
  
-   **check_permissions**  
  
-   **column_tracking**  
  
-   **destination_owner**  
  
-   **pre_creation_command**  
  
-   **schema_options**  
  
-   **subset_filterclause**  
  
 Cambiar las propiedades siguientes requiere existentes se reinicialicen las suscripciones, y debe especificar un valor de **1** para el *force_reinit_subscription* parámetro:  
  
-   **check_permissions**  
  
-   **column_tracking**  
  
-   **destination_owner**  
  
-   **pre_creation_command**  
  
-   **identityrangemanagementoption**  
  
-   **subscriber_upload_options**  
  
-   **subset_filterclause**  
  
-   **creation_script**  
  
-   **schema_option**  
  
-   **logical_record_level_conflict_detection**  
  
-   **logical_record_level_conflict_resolution**  
  
 Al especificar un valor de 3 para **partition_options**, los metadatos se limpian cada vez que se ejecuta el agente de mezcla y la instantánea con particiones expira más rápidamente. Al utilizar esta opción, debe considerar la habilitación de la instantánea con particiones solicitada por el suscriptor. Para más información, consulte [Instantáneas para publicaciones de combinación con filtros con parámetros](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Al establecer el **column_tracking** propiedad, si la tabla ya está publicada en otras publicaciones de mezcla, el seguimiento por columna debe ser el mismo que el valor utilizado por los artículos existentes basados en esta tabla. Este parámetro es específico solamente de los artículos de tabla.  
  
 Si varias publicaciones publican artículos basados en la misma tabla subyacente, cambiando el **delete_tracking** propiedad o el **compensate_for_errors** propiedad para un artículo hace que el mismo cambio se intentó el resto de artículos se basa en la misma tabla.  
  
 Si la cuenta de inicio de sesión o usuario del publicador que utiliza el proceso de mezcla no dispone de los permisos de tabla correctos, los cambios no válidos se registran como conflictos.  
  
 Al cambiar el valor de **schema_option**, el sistema no lleva a cabo una actualización bit a bit. Esto significa que al establecer **schema_option** mediante **sp_changemergearticle**existente puede desactivarse la configuración de bits. Para conservar la configuración existente, debe realizar [& (AND bit a bit)](../../t-sql/language-elements/bitwise-and-transact-sql.md) entre el valor que se está estableciendo y el valor actual de *schema_option*, que se puede determinar mediante la ejecución de [sp_helpmergearticle](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md).  
  
> [!CAUTION]  
>  Cuando es muchos (quizá hasta centenares) de artículos en una publicación y ejecute **sp_changemergearticle** uno de los artículos, puede tardar mucho tiempo en Finalizar la ejecución.  
  
## <a name="valid-schema-option-table"></a>Tabla Opciones de esquema válidas  
 La tabla siguiente describen los permitidos *schema_option*valores, según el tipo de artículo.  
  
|Tipo de artículo|Valores de las opciones de esquema|  
|------------------|--------------------------|  
|**solo esquema Func**|**0 x 01** y **0 x 2000**|  
|**solo esquema de vista indizada**|**0 x 01**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0x1000000**y **0x200000**|  
|**solo esquema de procedimiento**|**0 x 01** y **0 x 2000**|  
|**table**|Todas las opciones.|  
|**solo esquema de vista**|**0 x 01**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0x1000000**y **0x200000**|  
  
## <a name="example"></a>Ejemplo  
 [!code-sql[HowTo#sp_changemergearticle](../../relational-databases/replication/codesnippet/tsql/sp-changemergearticle-tr_1.sql)]  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_changemergearticle**.  
  
## <a name="see-also"></a>Vea también  
 [Ver y modificar las propiedades del artículo](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [Cambiar las propiedades de la publicación y de los artículos](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_dropmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
