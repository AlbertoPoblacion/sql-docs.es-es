---
title: sp_getapplock (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getapplock_TSQL
- sp_getapplock
dev_langs:
- TSQL
helpviewer_keywords:
- application locks
- sp_getapplock
ms.assetid: e1e85908-9f31-47cf-8af6-88c77e6f24c9
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f87a62e744bcd6032c58cdb3b327b747e5343d2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124020"
---
# <a name="spgetapplock-transact-sql"></a>sp_getapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Coloca un bloqueo en un recurso de la aplicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_getapplock [ @Resource = ] 'resource_name' ,  
     [ @LockMode = ] 'lock_mode'   
     [ , [ @LockOwner = ] 'lock_owner' ]   
     [ , [ @LockTimeout = ] 'value' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @Resource=] '*resource_name*'  
 Cadena que indica un nombre que identifica al recurso de bloqueo. La aplicación debe asegurar que el nombre del recurso sea exclusivo. El nombre especificado se convierte internamente mediante un algoritmo hash en un valor que puede almacenarse en el administrador de bloqueos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* es **nvarchar (255)** no tiene ningún valor predeterminado. Si tiene más de una cadena de recurso **nvarchar (255)** , se truncará a **nvarchar (255)** .  
  
 *resource_name* es binario en comparación y, por tanto, distingue mayúsculas de minúsculas, independientemente de la configuración de intercalación de la base de datos actual.  
  
> [!NOTE]  
>  Una vez que se ha adquirido un bloqueo de aplicación, solo los primeros 32 caracteres pueden recuperarse como texto simple; al resto se le aplicará el algoritmo hash.  
  
 [ @LockMode=] '*lock_mode*'  
 Es el modo de bloqueo que se va a obtener para un recurso determinado. *lock_mode* es **nvarchar(32)** y carece de valor predeterminado. El valor puede ser cualquiera de las siguientes acciones: **Compartido**, **actualización**, **IntentShared**, **IntentExclusive**, o **exclusivo**.  
  
 [ @LockOwner=] '*lock_owner*'  
 Es el propietario del bloqueo, que es el valor de *lock_owner* cuando se solicitó el bloqueo. *lock_owner* es **nvarchar(32)** . El valor puede ser **Transaction** (predeterminado) o **Session**. Cuando el *lock_owner* valor es **transacciones**, de manera predeterminada o especificándolo explícitamente, sp_getapplock debe ejecutarse desde dentro de una transacción.  
  
 [ @LockTimeout=] '*valor*'  
 Es un valor de tiempo de espera de los bloqueos, en milisegundos. El valor predeterminado es el mismo que el valor devuelto por@LOCK_TIMEOUT. Para indicar que una solicitud de bloqueo debe devolver un código de retorno de -1 en lugar de esperar el bloqueo cuando la solicitud no pueden concederse inmediatamente, especifique 0.  
  
 [ @DbPrincipal=] '*database_principal*'  
 Es el usuario, el rol o el rol de aplicación que tiene permisos para un objeto de una base de datos. El llamador de la función debe ser un miembro de *database_principal*, dbo o db_owner fijo de base de datos para llamar correctamente a la función. El valor predeterminado es public.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 \>= 0 (correcto) o < 0 (error)  
  
|Valor|Resultado|  
|-----------|------------|  
|0|Se concedió el bloqueo de forma sincrónica.|  
|1|Se concedió el bloqueo después de esperar a que se liberaran otros bloqueos no compatibles.|  
|-1|Se agotó el tiempo de espera de la solicitud de bloqueo.|  
|-2|Se canceló la solicitud de bloqueo.|  
|-3|La solicitud de bloqueo fue objeto del propio bloqueo.|  
|-999|Indica un error de llamada o de validación de parámetros.|  
  
## <a name="remarks"></a>Comentarios  
 Los bloqueos colocados en un recurso se asocian a la transacción o a la sesión actuales. Los bloqueos asociados con la transacción actual se liberan cuando ésta se confirma o se revierte. Los bloqueos asociados con la sesión se liberan cuando se haya cerrado la sesión. Cuando el servidor se cierra por cualquier motivo, se liberan todos los bloqueos.  
  
 El bloqueo de recurso creado por sp_getapplock se crea en la base de datos actual para la sesión. Cada recurso de bloqueo se identifica mediante la combinación de los siguientes valores:  
  
-   El Id. de la base de datos que contiene el recurso de bloqueo.  
  
-   La entidad de seguridad de la base de datos indicada en el parámetro @DbPrincipal.  
  
-   El nombre del bloqueo indicado en el parámetro @Resource.  
  
 Solo un miembro de la entidad de seguridad de base de datos indicado en el parámetro @DbPrincipal puede adquirir bloqueos de aplicación que especifiquen dicha entidad de seguridad. Los miembros de los roles dbo y db_owner se consideran, de manera implícita, miembros de todos los roles.  
  
 Es posible liberar los bloqueos de forma explícita con sp_releaseapplock. Si una aplicación llama a sp_getapplock varias veces para el mismo recurso de bloqueo, es necesario llamar a sp_releaseapplock el mismo número de veces para liberar el bloqueo.  Cuando se abre un bloqueo con el `Transaction` propietario de bloqueo, que se libere el bloqueo cuando se confirma o revierte la transacción.
  
 Si se llama al parámetro sp_getapplock varias veces para el mismo recurso de bloqueo, pero el modo de bloqueo especificado en cualquiera de las solicitudes es diferente del modo existente, el efecto sobre el recurso es la unión de los dos modos de bloqueo. En la mayoría de los casos, esto significa que el modo de bloqueo se promociona al más fuerte de los modos: el modo existente o el recién solicitado. Este modo de bloqueo más fuerte se mantiene hasta su liberación, incluso si anteriormente se han efectuado llamadas para liberar. Por ejemplo, en la siguiente secuencia de llamadas, el recurso se mantiene en modo `Exclusive`, en lugar de `Shared`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
EXEC @result = sp_releaseapplock @Resource = 'Form1';  
COMMIT TRANSACTION;  
GO  
```  
  
 Un interbloqueo con un bloqueo de aplicación no revierte la transacción que solicitó el bloqueo de aplicación. Cualquier reversión que pueda solicitarse como resultado del valor devuelto debe realizarse manualmente. Por tanto, se recomienda incluir la comprobación de errores en el código de forma que si se devuelven determinados valores (por ejemplo, -3), se inicie una acción ROLLBACK TRANSACTION u otra alternativa.  
  
 A continuación, se muestra un ejemplo:  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
IF @result = -3  
BEGIN  
    ROLLBACK TRANSACTION;  
END  
ELSE  
BEGIN  
    EXEC @result = sp_releaseapplock @Resource = 'Form1';  
    COMMIT TRANSACTION;  
END;  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa el Id. de la base de datos activa para calificar el recurso. Por lo tanto, si se ejecuta sp_getapplock, incluso con los mismos valores de parámetros en bases de datos diferentes, el resultado es bloqueos separados en recursos separados.  
  
 Utilice la vista de administración dinámica sys.dm_tran_locks o el procedimiento almacenado sp_lock system o utilice [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para supervisar los bloqueos.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer al rol public.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se coloca un bloqueo compartido, asociado a la transacción actual, en el recurso `Form1` de la base de datos `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
 En el siguiente ejemplo se especifica `dbo` como la entidad de seguridad de base de datos.  
  
```  
BEGIN TRAN;  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'AdventureWorks2012',   
     @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [APPLOCK_MODE &#40;Transact-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;Transact-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_releaseapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)  
  
  
