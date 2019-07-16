---
title: sp_helplogreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
author: stevestein
ms.author: sstein
ms.openlocfilehash: b6ecac979077dd83d6549b408c8c9e4d2bd4402f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122439"
---
# <a name="sphelplogreaderagent-transact-sql"></a>sp_helplogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve las propiedades del trabajo del Agente de registro del LOG para la base de datos de publicaciones. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publisher = ] 'publisher'` Es el nombre del publicador. *publicador* es **sysname**, su valor predeterminado es null.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID. del agente.|  
|**name**|**nvarchar(100)**|Nombre del agente.|  
|**publisher_security_mode**|**smallint**|Modo de seguridad utilizado por el agente al conectarse al publicador, que puede ser uno de los siguientes:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticación<br /><br /> **1** = autenticación de Windows.|  
|**publisher_login**|**sysname**|Inicio de sesión utilizado para conectarse al publicador.|  
|**publisher_password**|**nvarchar(524)**|Por motivos de seguridad, un valor de **\* \* \* \* \* \* \* \* \* \*** siempre es Devuelve.|  
|**job_id**|**uniqueidentifier**|Id. único del trabajo del agente.|  
|**job_login**|**nvarchar(512)**|Es la cuenta de Windows bajo la que se ejecuta el agente de lector del registro, que se devuelve en el formato *dominio*\\*username*.|  
|**job_password**|**sysname**|Por motivos de seguridad, un valor de **\* \* \* \* \* \* \* \* \* \*** siempre es Devuelve.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_helplogreader_agent** se utiliza en la replicación transaccional.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor en el publicador o los miembros de la **db_owner** rol fijo de base de datos en la base de datos de publicación puede ejecutar **sp_helplogreader_agent**.  
  
## <a name="see-also"></a>Vea también  
 [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  (Ver y modificar la configuración de seguridad de la replicación)  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
