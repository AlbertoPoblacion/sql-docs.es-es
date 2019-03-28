---
title: sp_get_redirected_publisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_get_redirected_publisher_TSQL
- sp_get_redirected_publisher
ms.assetid: d47a9ab5-f2cc-42a8-8be9-a33895ce44f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 49bffb24c5ddc45c1c6b88fb424ab419445819fb
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529973"
---
# <a name="spgetredirectedpublisher-transact-sql"></a>sp_get_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Lo utilizan los agentes de replicación para consultar a un distribuidor a fin de determinar si se ha redirigido el publicador original.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_get_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @bypass_publisher_validation = ] [0 | 1 ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @original_publisher = ] 'original_publisher'` El nombre de la base de datos que se está publicando. *publisher_db* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @publisher_db = ] 'publisher_db'` El nombre de la base de datos que se está publicando. *publisher_db* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @bypass_publisher_validation = ] [0 | 1 ]` Se utiliza para omitir la validación del publicador redirigido. Si es 0, se realiza la validación. Si es 1, no se realiza la validación. *bypass_publisher_validation* es **bit**, su valor predeterminado es 0.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**redirected_publisher**|**sysname**|El nombre del publicador después de la redirección.|  
|**error_number**|**int**|El número de error del error de validación.|  
|**error_severity**|**int**|La gravedad del error de validación.|  
|**error_message**|**nvarchar(4000)**|El texto del mensaje de error de validación.|  
  
## <a name="remarks"></a>Comentarios  
 *redirected_publisher* devuelve el nombre del publicador actual. Devuelve null si el publicador y publicar bases de datos no se han redirigido mediante **sp_redirect_publisher**.  
  
 Si no se solicita la validación o si no existe ninguna entrada para el publicador y la base de datos de publicación, *error_number* y *error_severity* devuelven 0 y *error_message* Devuelve null.  
  
 Si se solicita la validación, la validación del procedimiento almacenado [sp_validate_redirected_publisher &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md) se llama para comprobar que el destino de la redirección es un host adecuado para la publicación base de datos. Si la validación es correcta, **sp_get_redirected_publisher** devuelve el nombre del publicador redirigido, 0 para el *error_number* y *error_severity* columnas y el valor null el *error_message* columna.  
  
 Si se solicita la validación y se produce un error, se devuelve el nombre del publicador redirigido junto con información sobre el error.  
  
## <a name="permissions"></a>Permisos  
 Autor de la llamada debe ser un miembro de la **sysadmin** rol fijo de servidor, el **db_owner** rol fijo de base de datos para la base de datos de distribución o un miembro de una lista de acceso de publicación para una publicación definida asociado a la base de datos del publicador.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
