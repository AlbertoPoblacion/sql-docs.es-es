---
title: sp_syscollector_update_collection_set (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_set_TSQL
- sp_syscollector_update_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 2dccc3cd-0e93-4e3e-a4e5-8fe89b31bd63
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d77ec36f36260226a78136b46656b1e2e8187e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63004321"
---
# <a name="spsyscollectorupdatecollectionset-transact-sql"></a>sp_syscollector_update_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Se usa para modificar las propiedades o el nombre de un conjunto de recopilación definido por el usuario.  
  
> [!WARNING]  
>  En los casos en que la cuenta de Windows configurada como proxy pertenezca a un usuario no interactivo o interactivo que aún no se ha conectado, el directorio del perfil no existirá y se producirá un error al crear el directorio de almacenamiento temporal. Por tanto, si utiliza una cuenta de proxy en un controlador de dominio, debe especificar una cuenta interactiva que se haya utilizado al menos una vez para asegurarse de que se ha creado el directorio del perfil.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_syscollector_update_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @new_name = ] 'new_name' ]  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    ,[ [ @schedule_uid = ] 'schedule_uid' ]  
    ,[ [ @schedule_name = ] 'schedule_uid' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @collection_set_id = ] collection_set_id` Es el identificador local único del conjunto de recopilación. *collection_set_id* es **int** y debe tener un valor si *nombre* es NULL.  
  
`[ @name = ] 'name'` Es el nombre del conjunto de recopilación. *nombre* es **sysname** y debe tener un valor si *collection_set_id* es NULL.  
  
`[ @new_name = ] 'new_name'` Es el nuevo nombre del conjunto de recopilación. *new_name* es **sysname**, y si se utiliza, no puede ser una cadena vacía. *new_name* deben ser únicos. Para obtener una lista de los nombres de conjuntos de recopilación actuales, consulte la vista del sistema syscollector_collection_sets.  
  
`[ @target = ] 'target'` Reservado para uso futuro.  
  
`[ @collection_mode = ] collection_mode` Es el tipo de recopilación de datos para usar. *collection_mode* es **smallint** y puede tener uno de los siguientes valores:  
  
 0 - Modo de almacenamiento en caché. La recopilación y la carga de datos están en programaciones independientes. Especifique el modo de almacenamiento en caché para la recopilación continua.  
  
 1 - Modo sin almacenamiento en caché. Recopilación de datos y la carga se encuentra en la misma programación. Establezca el modo sin almacenamiento en caché para la recopilación ad hoc o la recopilación de instantáneas.  
  
 Al cambiar del modo sin almacenamiento en caché al modo en caché (0), debe especificar también *valor schedule_uid* o *schedule_name*.  
  
`[ @days_until_expiration = ] days_until_expiration` Es el número de días que los datos recopilados se guardan en el almacén de datos de administración. *days_until_expiration* es **smallint**. *days_until_expiration* debe ser 0 o un entero positivo.  
  
`[ @proxy_id = ] proxy_id` Es el identificador único para un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cuenta de proxy del agente. *proxy_id* es **int**.  
  
`[ @proxy_name = ] 'proxy_name'` Es el nombre del servidor proxy. *proxy_name* es **sysname** y admite valores NULL.  
  
`[ @schedule_uid = ] 'schedule_uid'` Es el GUID que apunta a una programación. *valor schedule_uid* es **uniqueidentifier**.  
  
 Para obtener *valor schedule_uid*, consulta la tabla del sistema sysschedules.  
  
 Cuando *collection_mode* se establece en 0, *valor schedule_uid* o *schedule_name* debe especificarse. Cuando *collection_mode* está establecido en 1, *valor schedule_uid* o *schedule_name* se omite si se especifica.  
  
`[ @schedule_name = ] 'schedule_name'` Es el nombre de la programación. *schedule_name* es **sysname** y admite valores NULL. Si se especifica, *valor schedule_uid* debe ser NULL. Para obtener *schedule_name*, consulta la tabla del sistema sysschedules.  
  
`[ @logging_level = ] logging_level` Es el nivel de registro. *LOGGING_LEVEL* es **smallint** con uno de los siguientes valores:  
  
 0 - información del registro de ejecución y [!INCLUDE[ssIS](../../includes/ssis-md.md)] eventos que realizan el seguimiento:  
  
-   Iniciar/detener los conjuntos de recopilaciones  
  
-   Iniciar/detener los paquetes  
  
-   Información de error  
  
 1 - nivel de registro 0 y:  
  
-   Estadísticas de ejecución  
  
-   Progreso de recopilaciones que se ejecutan continuamente  
  
-   Eventos de advertencia de [!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 2 - nivel de registro 1 e información detallada de eventos de [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 El valor predeterminado de *logging_level* es 1.  
  
`[ @description = ] 'description'` Es la descripción del conjunto de recopilación. *descripción* es **nvarchar (4000)** .  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 sp_syscollector_update_collection_set se debe ejecutar en el contexto de la base de datos del sistema msdb.  
  
 Cualquier *collection_set_id* o *nombre* debe tener un valor, no puede ser NULL. Para obtener estos valores, consulte la vista del sistema syscollector_collection_sets.  
  
 Si el conjunto de recopilación se está ejecutando, solo se puede actualizar *valor schedule_uid* y *descripción*. Para detener el conjunto de recopilación, use [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md).  
  
## <a name="permissions"></a>Permisos  
 Requiere la pertenencia a un rol fijo de base de datos dc_admin o dc_operator (con permiso EXECUTE) para ejecutar este procedimiento. Aunque dc_operator puede ejecutar este procedimiento almacenado, las propiedades que pueden cambiar los miembros de este rol son limitadas. Las propiedades siguientes solo puede cambiarlas dc_admin:  
  
-   @new_name  
  
-   @target  
  
-   @proxy_id  
  
-   @description  
  
-   @collection_mode  
  
-   @days_until_expiration  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-renaming-a-collection-set"></a>A. Cambiar el nombre de un conjunto de recopilación  
 En el ejemplo siguiente se cambia el nombre de un conjunto de recopilación definido por el usuario.  
  
```  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_update_collection_set  
@name = N'Simple collection set test 1',  
@new_name = N'Collection set test 1 in cached mode';  
GO  
```  
  
### <a name="b-changing-the-collection-mode-from-non-cached-to-cached"></a>b. Cambiar el modo de recopilación de sin almacenamiento en caché al modo de almacenamiento en caché  
 En el ejemplo siguiente se cambia el modo de recopilación de sin almacenamiento en caché al modo de almacenamiento en caché. Este cambio requiere que se especifique un identificador o un nombre para la programación.  
  
```  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_update_collection_set  
@name = N'Collection set test 1 in cached mode',  
@collection_mode = 0,  
@schedule_uid = 'C7022AF3-51B8-4011-B159-64C47C88FF70';  
-- alternatively, use @schedule_name.  
-- @schedule_name = N'CollectorSchedule_Every_15min;  
GO  
```  
  
### <a name="c-changing-other-collection-set-parameters"></a>C. Cambiar otros parámetros del conjunto de recopilación  
 En el ejemplo siguiente se actualizan varias propiedades del conjunto de recopilación denominado "Simple collection set test 2'.  
  
```  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_update_collection_set  
@name = N'Simple collection set test 2',  
@collection_mode = 1,  
@days_until_expiration = 5,  
@description = N'This is a test collection set that runs in noncached mode.',  
@logging_level = 0;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Recopilación de datos](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)   
 [dbo.sysschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
