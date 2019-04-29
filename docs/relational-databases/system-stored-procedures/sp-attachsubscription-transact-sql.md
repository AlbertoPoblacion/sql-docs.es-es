---
title: sp_attachsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e1eec1aaa8162565f481b2d82982781e1a3c8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996102"
---
# <a name="spattachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Adjunta una base de datos de suscripciones existente a cualquier suscriptor. Este procedimiento almacenado se ejecuta en el nuevo suscriptor de la base de datos maestra.  
  
> [!IMPORTANT]  
>  Esta característica ha quedado desusada y se retirará en versiones posteriores. Esta característica no se debe utilizar en nuevos trabajos de desarrollo. En las publicaciones de combinación en las que se han creado particiones mediante filtros con parámetros, se recomienda utilizar las nuevas características de las instantáneas con particiones, que simplifican la inicialización de un gran número de suscripciones. Para más información, consulte [Instantáneas para publicaciones de combinación con filtros con parámetros](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). En las publicaciones que no están divididas en particiones, puede inicializar una suscripción con una copia de seguridad. Para obtener más información, consulte [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @dbname = ] 'dbname'` Es la cadena que especifica la base de datos de suscripción de destino por nombre. *dbname* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @filename = ] 'filename'` Es el nombre y la ubicación física del MDF principal (**maestro** archivo de datos). *nombre de archivo* es **nvarchar (260)**, no tiene ningún valor predeterminado.  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'` Es el modo de seguridad del suscriptor que se utilizará al conectarse a un suscriptor durante la sincronización. *subscriber_security_mode* es **int**, su valor predeterminado es null.  
  
> [!NOTE]  
>  Es necesario utilizar Autenticación de Windows. Si *subscriber_security_mode* no **1** (autenticación de Windows), se devuelve un error.  
  
`[ @subscriber_login = ] 'subscriber_login'` Es el nombre de inicio de sesión del suscriptor que se utilizará al conectarse a un suscriptor durante la sincronización. *subscriber_login* es **sysname**, su valor predeterminado es null.  
  
> [!NOTE]  
>  Este parámetro ha quedado en desuso y se mantiene solo permitir la compatibilidad de las secuencias de comandos. Si *subscriber_security_mode* no **1** y *subscriber_login* está especificado, se devuelve un error.  
  
`[ @subscriber_password = ] 'subscriber_password'` Es la contraseña del suscriptor. *subscriber_password* es **sysname**, su valor predeterminado es null.  
  
> [!NOTE]  
>  Este parámetro ha quedado en desuso y se mantiene solo permitir la compatibilidad de las secuencias de comandos. Si *subscriber_security_mode* no **1** y *subscriber_password* está especificado, se devuelve un error.  
  
`[ @distributor_security_mode = ] distributor_security_mode` Es el modo de seguridad que se utilizará al conectarse a un distribuidor durante la sincronización. *distributor_security_mode* es **int**, su valor predeterminado es **0**. **0** especifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticación. **1** especifica autenticación de Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` Es el inicio de sesión del distribuidor que se utilizará al conectarse a un distribuidor durante la sincronización. *distributor_login* es necesaria si *distributor_security_mode* está establecido en **0**. *distributor_login* es **sysname**, su valor predeterminado es null.  
  
`[ @distributor_password = ] 'distributor_password'` Es la contraseña del distribuidor. *distributor_password* es necesaria si *distributor_security_mode* está establecido en **0**. *distributor_password* es **sysname**, su valor predeterminado es null. El valor de *distributor_password* debe tener menos de 120 caracteres Unicode.  
  
> [!IMPORTANT]  
>  No utilice una contraseña en blanco. Utilice una contraseña segura. Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Es el modo de seguridad que se utilizará al conectarse a un publicador durante la sincronización. *publisher_security_mode* es **int**, su valor predeterminado es **1**. Si **0**, especifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticación. Si **1**, especifica la autenticación de Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Es el inicio de sesión que se utilizará al conectarse a un publicador durante la sincronización. *publisher_login* es **sysname**, su valor predeterminado es null.  
  
`[ @publisher_password = ] 'publisher_password'` Es la contraseña utilizada al conectarse al publicador. *publisher_password* es **sysname**, su valor predeterminado es null. El valor de *publisher_password* debe tener menos de 120 caracteres Unicode.  
  
> [!IMPORTANT]  
>  No utilice una contraseña en blanco. Utilice una contraseña segura. Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
`[ @job_login = ] 'job_login'` Es el inicio de sesión para la cuenta de Windows que se ejecuta el agente. *job_login* es **nvarchar (257)**, no tiene ningún valor predeterminado. Esta cuenta de Windows siempre se utiliza para conexiones del agente con el distribuidor.  
  
`[ @job_password = ] 'job_password'` Es la contraseña de la cuenta de Windows que se ejecuta el agente. *job_password* es **sysname**, no tiene ningún valor predeterminado. El valor de *job_password* debe tener menos de 120 caracteres Unicode.  
  
> [!IMPORTANT]  
>  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
`[ @db_master_key_password = ] 'db_master_key_password'` Es la contraseña de una definida por el usuario clave maestra. *db_master_key_password* es **nvarchar (524)**, su valor predeterminado es null. Si *db_master_key_password* no se especifica, se puede quitar y volver a crear una clave maestra de base de datos existente.  
  
> [!IMPORTANT]  
>  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_attachsubscription** se utiliza en la replicación de instantáneas, transaccional y de mezcla.  
  
 No se puede adjuntar una suscripción a la publicación si el período de retención de la publicación ha expirado. Si se especifica una suscripción con un período de retención transcurrido, se produce un error cuando se adjunta la suscripción o cuando se sincroniza por primera vez. Las publicaciones con un período de retención de publicación de **0** (nunca expiran) se omiten.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor puede ejecutar **sp_attachsubscription**.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
