---
title: sp_audit_write (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_audit_write
- sp_audit_write_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 450b1cdde9185edee5eac41f52d209e43a7ae22f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62996259"
---
# <a name="spauditwrite-transact-sql"></a>sp_audit_write (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Agrega un evento de auditoría definido por el usuario a la **USER_DEFINED_AUDIT_GROUP**. Si **USER_DEFINED_AUDIT_GROUP** no está habilitado, **sp_audit_write** se omite.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
sp_audit_write [ @user_defined_event_id = ] user_defined_event_id
    [ , [ @succeeded = ] succeeded ]
    [ , [ @user_defined_information = ] 'user_defined_information' ]
    [ ; ]
```  
  
## <a name="arguments"></a>Argumentos  
 `[ @user_defined_event_id = ] user_defined_event_id`  
 Un parámetro definido por el usuario y registrado en el **user_defined_event_id** columna del registro de auditoría. *@user_defined_event_id* es de tipo **smallint**.  
  
 `[ @succeeded = ] succeeded`  
 Parámetro pasado por el usuario para indicar si el evento se realizó correctamente o no. Aparece en la columna "succeeded" del registro de auditoría. `@succeeded` es **bits**.  
  
 `[ @user_defined_information = ] 'user_defined_information'`  
 Es el texto definido por el usuario y registrado en la nueva columna user_defined_event_id column del registro de auditoría. `@user_defined_information` es **nvarchar (4000)** .  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
 Los errores los producen parámetros de entrada incorrectos o errores al escribir en el registro de auditoría de destino.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el **USER_DEFINED_AUDIT_GROUP** se agrega a una especificación de auditoría de servidor o una especificación de auditoría de base de datos, el evento desencadenado por **sp_audit_write** se incluirán en el registro de auditoría.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer a la **pública** rol de base de datos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-creating-a-user-defined-audit-event-with-informational-text"></a>A. Crear un evento de auditoría definido por el usuario con texto informativo  
 En el ejemplo siguiente se crea un evento de auditoría con el identificador 27, el valor "succeeded" 0 y la inclusión de texto informativo opcional.  
  
```  
EXEC sp_audit_write @user_defined_event_id =  27 ,   
              @succeeded =  0   
            , @user_defined_information = N'Access to a monitored object.' ;  
```  
  
### <a name="b--creating-a-user-defined-audit-event-without-informational-text"></a>b.  Crear un evento de auditoría definido por el usuario sin texto informativo  
 En el ejemplo siguiente se crea un evento de auditoría con identificador 27, el valor de "succeeded" 0 y sin incluir texto informativo opcional ni nombres de parámetro opcionales.  
  
```  
EXEC sp_audit_write 27, 0;  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
