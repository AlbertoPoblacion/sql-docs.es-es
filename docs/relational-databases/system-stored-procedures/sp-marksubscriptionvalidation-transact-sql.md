---
title: sp_marksubscriptionvalidation (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aad2574457285208b47af26d0729c725a22c05b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62629180"
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Marca la transacción abierta actual para que sea una transacción de validación de nivel de suscripción del suscriptor especificado. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @publication = ] 'publication'` Es el nombre de la publicación. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @subscriber = ] 'subscriber'` Es el nombre del suscriptor. *suscriptor* es de tipo sysname y no tiene ningún valor predeterminado.  
  
`[ @destination_db = ] 'destination_db'` Es el nombre de la base de datos de destino. *destination_db* es **sysname**, no tiene ningún valor predeterminado.  
  
`[ @publisher = ] 'publisher'` Especifica que no es [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher. *publicador* es **sysname**, su valor predeterminado es null.  
  
> [!NOTE]  
>  *publicador* no debe usarse para una publicación que pertenece a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_marksubscriptionvalidation** se utiliza en la replicación transaccional.  
  
 **sp_marksubscriptionvalidation** no admite que no sean de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] los suscriptores.  
  
 Para que no sean de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publicadores, no se puede ejecutar **sp_marksubscriptionvalidation** desde dentro de una transacción explícita. Esto se debe a que las transacciones explícitas no se admiten en la conexión al servidor vinculado que se utiliza para obtener acceso al publicador.  
  
 **sp_marksubscriptionvalidation** debe utilizarse junto con [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), especificando un valor de **1** para  *subscription_level*y puede utilizarse con otras llamadas a **sp_marksubscriptionvalidation** para marcar la transacción abierta actual para otros suscriptores.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Ejemplo  
 La siguiente consulta puede aplicarse a la base de datos de publicaciones para exponer comandos de validación de suscripción. Los Agentes de distribución de los suscriptores especificados recogen estos comandos. Tenga en cuenta que la primera transacción valida el artículo '**art1**', mientras que la segunda transacción valida'**art2**'. Tenga en cuenta también que las llamadas a **sp_marksubscriptionvalidation** y [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) se han encapsulado en una transacción. Se recomienda sólo una llamada a [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) por transacción. Esto es porque [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) mantiene un bloqueo de tabla compartida en la tabla de origen para la duración de la transacción. Debe mantener la transacción corta para maximizar la simultaneidad.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Validar datos replicados](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
