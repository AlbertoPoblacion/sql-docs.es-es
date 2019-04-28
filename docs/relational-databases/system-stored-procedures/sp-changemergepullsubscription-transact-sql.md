---
title: sp_changemergepullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepullsubscription
- sp_changemergepullsubscription_TSQL
helpviewer_keywords:
- sp_changemergepullsubscription
ms.assetid: 5e0d04f2-6175-44a2-ad96-a8e2986ce4c9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cf650c095e27fe3a270ad9610e959bd6f5f1a6a3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997094"
---
# <a name="spchangemergepullsubscription-transact-sql"></a>sp_changemergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia las propiedades de la suscripción de extracción de mezcla. Este procedimiento almacenado se ejecuta en el suscriptor de la base de datos de suscripción.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_changemergepullsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @publisher= ] 'publisher' ]  
    [ , [ @publisher_db= ] 'publisher_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publication = ] 'publication'` Es el nombre de la publicación. *publicación* es **sysname**, su valor predeterminado es %.  
  
`[ @publisher = ] 'publisher'` Es el nombre del publicador. *publicador*es **sysname**, su valor predeterminado es %.  
  
`[ @publisher_db = ] 'publisher_db'` Es el nombre de la base de datos del publicador. *publisher_db*es **sysname**, su valor predeterminado es %.  
  
`[ @property = ] 'property'` Es el nombre de la propiedad que se va a cambiar. *propiedad* es **sysname**, y puede tener uno de los valores de la tabla.  
  
`[ @value = ] 'value'` Es el nuevo valor para la propiedad especificada. *valor*es **nvarchar (255)**, y puede tener uno de los valores de la tabla.  
  
|Property|Valor|Descripción|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Ubicación donde se almacena la carpeta de instantáneas si la ubicación es distinto o además en la ubicación predeterminada.|  
|**description**||Descripción de esta suscripción de extracción de mezcla.|  
|**distributor**||Nombre del distribuidor.|  
|**distributor_login**||Id. de inicio de sesión utilizado en el distribuidor para la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_password**||Contraseña (cifrada) utilizada en el distribuidor para la Autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_security_mode**|**1**|Se utiliza la autenticación de Windows para la conexión con el distribuidor.|  
||**0**|Se utiliza la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la conexión con el distribuidor.|  
|**dynamic_snapshot_location**||Ruta de acceso a la carpeta donde se guardan los archivos de instantáneas.|  
|**ftp_address**||Disponible únicamente por compatibilidad con versiones anteriores. Es la dirección de red del servicio FTP (Protocolo de transferencia de archivos) del distribuidor.|  
|**ftp_login**||Disponible únicamente por compatibilidad con versiones anteriores. Se usa el nombre de usuario para conectarse al servicio FTP.|  
|**ftp_password**||Disponible únicamente por compatibilidad con versiones anteriores. Es la contraseña del usuario que se utiliza para conectarse al servicio FTP.|  
|**ftp_port**||Disponible únicamente por compatibilidad con versiones anteriores. Es el número de puerto del servicio FTP para el distribuidor.|  
|**hostname**||Especifica el valor de HOST_NAME() cuando esta función se utiliza en la cláusula WHERE de un filtro de combinación o relación de registros lógicos.|  
|**internet_login**||Inicio de sesión que utiliza el Agente de mezcla al conectarse al servidor web que hospeda la sincronización web utilizando autenticación básica.|  
|**internet_password**||Contraseña para el Inicio de sesión que utiliza el Agente de mezcla al conectarse al servidor web que hospeda la sincronización web utilizando autenticación básica.|  
|**internet_security_mode**|**1**|Para la conexión con el servidor web que hospeda la sincronización web se utiliza la autenticación de Windows.|  
||**0**|Para la conexión con el servidor web que hospeda la sincronización web se utiliza la autenticación básica.|  
|**internet_timeout**||Período de tiempo, en segundos, antes de que expire una solicitud de sincronización Web.|  
|**internet_url**||URL que representa la ubicación de la escucha de replicación para la sincronización web.|  
|**merge_job_login**||Inicio de sesión de la cuenta de Windows con la que se ejecuta el agente.|  
|**merge_job_password**||Contraseña de la cuenta de Windows con la que se ejecuta el agente.|  
|**priority**||Disponible para la compatibilidad con versiones anteriores; ejecute [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md) en el publicador en su lugar, para modificar la prioridad de una suscripción.|  
|**publisher_login**||Id. de inicio de sesión utilizado en el publicador para la Autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_password**||Contraseña (cifrada) utilizada en el publicador para la Autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_security_mode**|**0**|Se utiliza la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la conexión con el publicador.|  
||**1**|Se utiliza la autenticación de Windows para la conexión con el publicador.|  
||**2**|Desencadenadores de sincronización utilizan una estática **sysservers** entrada para realizar la llamada a procedimiento remoto (RPC) y el publicador debe estar definido en el **sysservers** tabla como un servidor remoto o vinculado.|  
|**sync_type**|**automatic**|El esquema y los datos iniciales de las tablas publicadas se transfieren primero al suscriptor.|  
||**Ninguno**|El suscriptor ya tiene el esquema y los datos iniciales de las tablas publicadas; los datos y las tablas del sistema se transfieren siempre.|  
|**use_ftp**|**true**|Se utiliza FTP en lugar del protocolo habitual para recuperar instantáneas.|  
||**False**|Utiliza el protocolo habitual para recuperar instantáneas.|  
|**use_web_sync**|**true**|La suscripción se puede sincronizar a través de HTTP.|  
||**False**|La suscripción no se puede sincronizar a través de HTTP.|  
|**use_interactive_resolver**|**true**|Durante la reconciliación se utiliza el Solucionador interactivo.|  
||**False**|No se utiliza el Solucionador interactivo.|  
|**working_directory**||Ruta de acceso completa al directorio donde se transfieren los archivos de instantáneas por medio de FTP, cuando se especifica esa opción.|  
|NULL (predeterminado)||Devuelve la lista de valores admitidos para *propiedad*.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_changemergepullsubscription** se utiliza en la replicación de mezcla.  
  
 Se considera que el servidor y la base de datos actuales son el suscriptor y la base de datos del suscriptor.  
  
 Después de cambiar un inicio de sesión o una contraseña de agente, debe detener y reiniciar el agente para que el cambio surta efecto.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_changemergepullsubscription**.  
  
## <a name="see-also"></a>Vea también  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  (Ver y modificar las propiedades de una suscripción de extracción)  
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
