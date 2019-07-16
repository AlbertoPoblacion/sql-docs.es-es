---
title: sp_vupgrade_mergeobjects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_mergeobjects
- sp_vupgrade_mergeobjects_TSQL
helpviewer_keywords:
- sp_vupgrade_mergeobjects
ms.assetid: 73257c2e-cc4c-48e7-9d66-7ef045bdd4f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed0992ff1b6b7de6f93213b612ff05ebcbdb3df5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042699"
---
# <a name="spvupgrademergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vuelve a generar los desencadenadores específicos de artículo, los procedimientos almacenados y las vistas que se usan para realizar un seguimiento y aplicar los cambios de datos para la replicación de mezcla. Ejecute este procedimiento en las siguientes situaciones:  
  
-   Cuando se elimina accidentalmente un objeto necesario para la replicación.  
  
-   Cuando se aplica una actualización, por ejemplo, una revisión, que requiere efectuar modificaciones en uno o más objetos de la replicación. Ejecute el procedimiento en cada nodo después de aplicar la actualización.  
  
 Para la ejecución de este procedimiento almacenado no es necesario reinicializar las suscripciones. Este procedimiento no es necesario si se instala un Service Pack o una actualización en una versión nueva de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @login = ] 'login'` Es el inicio de sesión del administrador del sistema a usar al crear nuevos objetos del sistema en la base de datos de distribución. *login* es de tipo **sysname** y su valor predeterminado es NULL. Este parámetro no es necesario si *security_mode* está establecido en **1**, es decir, autenticación de Windows.  
  
`[ @password = ] 'password'` Es la contraseña de administrador del sistema a usar al crear nuevos objetos del sistema en la base de datos de distribución. *contraseña* es **sysname**, su valor predeterminado es **''** (cadena vacía). Este parámetro no es necesario si *security_mode* está establecido en **1**, es decir, autenticación de Windows.  
  
`[ @security_mode = ] 'security_mode'` Es el modo de seguridad de inicio de sesión que se usará al crear nuevos objetos del sistema en la base de datos de distribución. *security_mode* es **bit** con un valor predeterminado de **1**. Si **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se usará autenticación. Si **1**, se usará la autenticación de Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_vupgrade_mergeobjects** solo se usa para la replicación de mezcla.  
  
## <a name="permissions"></a>Permisos  
 Requiere la pertenencia al rol fijo de servidor **sysadmin** .  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Actualizar bases de datos replicadas](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
