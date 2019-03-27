---
title: sp_addsynctriggers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords:
- sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3ae733d560c227ccf282dfe4caed3935d9ffaebe
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493647"
---
# <a name="spaddsynctriggers-transact-sql"></a>sp_addsynctriggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea desencadenadores en el suscriptor utilizado con todos los tipos de suscripciones actualizables (actualización inmediata, actualización en cola, actualización inmediata con actualización en cola como conmutación por error). Este procedimiento almacenado se ejecuta en el suscriptor de la base de datos de suscripción.  
  
> [!IMPORTANT]  
>  El [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) procedimiento debe usarse en lugar de **sp_addsynctrigger**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) genera un script que contiene el **sp_addsynctrigger** llamadas.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_addsynctriggers [ @sub_table = ] 'sub_table'  
        , [ @sub_table_owner = ] 'sub_table_owner'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @ins_proc = ] 'ins_proc'   
        , [ @upd_proc = ] 'upd_proc'   
        , [ @del_proc = ] 'del_proc'   
        , [ @cftproc = ] 'cftproc'  
        , [ @proc_owner = ] 'proc_owner'  
    [ , [ @identity_col = ] 'identity_col' ]  
    [ , [ @ts_col = ] 'timestamp_col' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]   
        , [ @primary_key_bitmap = ] 'primary_key_bitmap'  
    [ , [ @identity_support = ] identity_support ]  
    [ , [ @independent_agent = ] independent_agent ]  
        , [ @distributor = ] 'distributor'   
    [ , [ @pubversion = ] pubversion  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @sub_table = ] 'sub_table'` Es el nombre de la tabla del suscriptor. *sub_table* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @sub_table_owner = ] 'sub_table_owner'` Es el nombre del propietario de la tabla del suscriptor. *sub_table_owner* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @publisher = ] 'publisher'` Es el nombre del servidor del publicador. *publicador* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @publisher_db = ] 'publisher_db'` Es el nombre de la base de datos del publicador. *publisher_db* es **sysname**, no tiene ningún valor predeterminado. Si es NULL, se utiliza la base de datos actual.  
  
`[ @publication = ] 'publication'` Es el nombre de la publicación. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @ins_proc = ] 'ins_proc'` Es el nombre del procedimiento almacenado que admite inserciones de transacciones sincrónicas en el publicador. *ins_proc* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @upd_proc = ] 'upd_proc'` Es el nombre del procedimiento almacenado que admite actualizaciones de transacciones sincrónicas en el publicador. *ins_proc* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @del_proc = ] 'del_proc'` Es el nombre del procedimiento almacenado que admite eliminaciones de transacciones sincrónicas en el publicador. *ins_proc* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @cftproc = ] 'cftproc'` Es el nombre del procedimiento generado automáticamente usado por las publicaciones que permiten la actualización en cola. *cftproc* es **sysname**, no tiene ningún valor predeterminado. En las publicaciones que permiten la actualización inmediata, este valor es NULL. Este parámetro se aplica a las publicaciones que permiten la actualización en cola (actualización en cola y actualización inmediata con actualización en cola como conmutación por error).  
  
`[ @proc_owner = ] 'proc_owner'` Especifica la cuenta de usuario en el publicador con el que se crearon los procedimientos almacenados generados automáticamente para la actualización de publicación (en cola e inmediata). *proc_owner* es **sysname** no tiene ningún valor predeterminado.  
  
`[ @identity_col = ] 'identity_col'` Es el nombre de la columna de identidad en el publicador. *identity_col* es **sysname**, su valor predeterminado es null.  
  
`[ @ts_col = ] 'timestamp_col'` Es el nombre de la **timestamp** columna en el publicador. *timestamp_col* es **sysname**, su valor predeterminado es null.  
  
`[ @filter_clause = ] 'filter_clause'` Es una restricción cláusula (WHERE) que define un filtro horizontal. Al especificar la cláusula de restricción, omita la palabra clave WHERE. *filter_clause*es **nvarchar (4000)**, su valor predeterminado es null.  
  
`[ @primary_key_bitmap = ] 'primary_key_bitmap'` Es un mapa de bits de las columnas de clave principal en la tabla. *primary_key_bitmap* es **varbinary (4000)**, no tiene ningún valor predeterminado.  
  
`[ @identity_support = ] identity_support` Habilita y deshabilita la administración del intervalo automático de identidad cuando se utiliza la actualización en cola. *identity_support* es un **bit**, su valor predeterminado es **0**. **0** significa que no hay ninguna identidad de intervalo de soporte técnico, **1** permite la administración de intervalos de identidad automáticos.  
  
`[ @independent_agent = ] independent_agent` Indica si hay un único agente de distribución (un agente independiente) para esta publicación, o un agente de distribución por publicación base de datos y suscripción pareja base de datos (un agente compartido). Este valor refleja el valor de la propiedad independent_agent de la publicación definida en el publicador. *independent_agent* es un poco con un valor predeterminado de **0**. Si **0**, se trata de un agente compartido. Si **1**, el agente es un agente independiente.  
  
`[ @distributor = ] 'distributor'` Es el nombre del distribuidor. *distribuidor* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @pubversion = ] pubversion` Indica la versión del publicador. *pubversion* es **int**, su valor predeterminado es 1. **1** significa que la versión del publicador es [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 2 o anterior; **2** significa que el publicador es [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 3 (SP3) o posterior. *pubversion* debe establecerse explícitamente en **2** cuando la versión del publicador es [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SP3 o posterior.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_addsynctriggers** es utilizado por el agente de distribución como parte de la inicialización de la suscripción. Este procedimiento almacenado no lo suelen ejecutar los usuarios, pero puede resultar útil si el usuario debe configurar manualmente una suscripción de tipo no sync.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_addsynctriggers**.  
  
## <a name="see-also"></a>Vea también  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
