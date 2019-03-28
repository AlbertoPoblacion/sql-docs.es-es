---
title: sp_registercustomresolver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_registercustomresolver
- sp_registercustomresolver_TSQL
helpviewer_keywords:
- sp_registercustomresolver
ms.assetid: 6d2b0472-0e1f-4005-833c-735d1940fe93
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0187853dcf0fc16fe88feb7e2731414a69fdd183
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536987"
---
# <a name="spregistercustomresolver-transact-sql"></a>sp_registercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registra un controlador de lógica de negocios o un solucionador personalizado basado en COM que se pueda invocar durante el proceso de sincronización de replicación de mezcla. Este procedimiento almacenado se ejecuta en el distribuidor.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_registercustomresolver [ @article_resolver = ] 'article_resolver'   
    [ , [ @resolver_clsid = ] 'resolver_clsid' ]  
    [ , [ @is_dotnet_assembly = ] 'is_dotnet_assembly' ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @article_resolver = ] 'article_resolver'` Especifica el nombre descriptivo para la lógica de negocios personalizada que se está registrando. *article_resolver* es **nvarchar (255)**, no tiene ningún valor predeterminado.  
  
`[ @resolver_clsid = ] 'resolver_clsid'` Especifica el valor CLSID del objeto COM que va a registrar. Lógica de negocios personalizada *resolver_clsid* es **nvarchar (50)**, su valor predeterminado es null. Este parámetro debe estar establecido en un valor CLSID válido o en NULL cuando se registre un ensamblado de controlador de lógica de negocios.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly'` Especifica el tipo de lógica de negocios personalizada que se va a registrar. *is_dotnet_assembly* es **nvarchar (50)**, su valor predeterminado es False. **True** indica que la lógica de negocios personalizada que se va a registrar es un controlador de lógica de negocios de ensamblado; **false** indica que es un componente COM.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name'` Es el nombre del ensamblado que implementa el controlador de lógica de negocios. *dotnet_assembly_name* es **nvarchar (255)**, su valor predeterminado es null. Debe especificar la ruta de acceso completa al ensamblado si no está implementado en el mismo directorio que el ejecutable del Agente de mezcla, en el mismo directorio que la aplicación que inicia de forma sincrónica el Agente de mezcla o en la caché de ensamblados global (GAC).  
  
`[ @dotnet_class_name = ] 'dotnet_class_name'` Es el nombre de la clase que invalida <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> para implementar el controlador de lógica de negocios. El nombre debe especificarse en el formulario **EspacioDeNombres.nombreDeClase**. *dotnet_class_name* es **nvarchar (255)**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_registercustomresolver** se utiliza en la replicación de mezcla.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_registercustomresolver**.  
  
## <a name="see-also"></a>Vea también  
 [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  (Implementar un controlador de lógica de negocios para un artículo de mezcla)  
 [Implementar un solucionador de conflictos personalizado para un artículo de mezcla](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
