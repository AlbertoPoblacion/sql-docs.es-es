---
title: sp_addqreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqreader_agent_TSQL
- sp_addqreader_agent
helpviewer_keywords:
- sp_addqreader_agent
ms.assetid: dc9f591a-e67e-4ba8-bf47-defd5eda0822
author: stevestein
ms.author: sstein
ms.openlocfilehash: a02082715dfc77384ebfde58d4c29f94cd3dd44c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769072"
---
# <a name="sp_addqreader_agent-transact-sql"></a>sp_addqreader_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Agrega un Agente de lectura de cola a un distribuidor específico. Este procedimiento almacenado se ejecuta en el distribuidor de la base de datos de distribución o en el publicador de la base de datos de publicaciones.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_addqreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name'  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>Argumentos  
`[ @job_login = ] 'job_login'`Es el inicio de sesión [!INCLUDE[msCoName](../../includes/msconame-md.md)] de la cuenta de Windows con la que se ejecuta el agente. *job_login* es de tipo **nvarchar (257)** y no tiene ningún valor predeterminado. Esta cuenta de Windows siempre se utiliza para conexiones del agente con el distribuidor.  
  
`[ @job_password = ] 'job_password'`Es la contraseña de la cuenta de Windows con la que se ejecuta el agente. *job_password* es de **tipo sysname**y no tiene ningún valor predeterminado.  
  
> [!IMPORTANT]  
>  No almacene información de autenticación en archivos de script. Para una mayor seguridad, los nombres de inicio de sesión y las contraseñas se deben proporcionar en tiempo de ejecución.  
  
`[ @job_name = ] 'job_name'`Es el nombre de un trabajo del agente existente. *job_name* es de **tipo sysname y su**valor predeterminado es NULL. Este parámetro solamente se especifica cuando se crea el agente a partir de un trabajo existente, en lugar de hacerlo con un trabajo recién creado (el valor predeterminado).  
  
`[ @frompublisher = ] frompublisher`Especifica si el procedimiento se ejecuta en el publicador. *frompublisher* es de bit y su valor predeterminado es **0**. Un valor de **1** significa que el procedimiento se ejecuta desde el publicador en la base de datos de publicación.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="remarks"></a>Observaciones  
 **sp_addqreader_agent** se utiliza en la replicación transaccional.  
  
 **sp_addqreader_agent** debe ejecutarse al menos una vez en un distribuidor que admita la actualización en cola después de [sp_adddistributiondb](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) pero antes de [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md).  
  
 El trabajo Agente de lectura de cola se quita al ejecutar [sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md).  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros del rol fijo de servidor **sysadmin** pueden ejecutar **sp_addqreader_agent**.  
  
## <a name="see-also"></a>Consulte también  
 [Habilitar suscripciones de actualización para publicaciones transaccionales](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Actualizar scripts de replicación &#40;programación de la replicación con Transact-SQL&#41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [Suscripciones actualizables para la replicación transaccional](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_changeqreader_agent &#40;&#41;de Transact-SQL](../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md)   
 [sp_helpqreader_agent &#40;&#41;de Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)  
  
  
