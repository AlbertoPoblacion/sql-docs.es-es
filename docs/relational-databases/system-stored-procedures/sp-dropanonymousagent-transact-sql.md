---
title: sp_dropanonymousagent (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53f1cf56d422f615bca142276cf94306ada58a16
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quita un agente anónimo de la supervisión de replicación en el distribuidor del publicador. Este procedimiento almacenado se ejecuta en el publicador de cualquier base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@subid=**] *sub_id*  
 Es el identificador global de una suscripción anónima. *sub_id* es **uniqueidentifier**, no tiene ningún valor predeterminado. Este identificador se puede recuperar en el suscriptor mediante **sp_helppullsubscription**. El valor de la **subid** campo del conjunto de resultados devuelto es este identificador global.  
  
 [  **@type=**] *tipo*  
 Es el tipo de suscripción. *tipo de* es **int**, no tiene ningún valor predeterminado. Los valores válidos son **1** o **2**. Especifique **1**, si la duplicación de instantáneas o replicación transaccional con el agente de distribución. Especifique **2**, si utiliza el agente de mezcla de replicación de mezcla.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_dropanonymousagent** se utiliza en todos los tipos de replicación.  
  
 Este procedimiento almacenado solo se utiliza para quitar agentes de suscripción anónima y no se puede utilizar para quitar suscripciones conocidas.  
  
## <a name="permissions"></a>Permissions  
 Solo los miembros de la **db_owner** rol fijo de base de datos en la base de datos de distribución puede ejecutar **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
