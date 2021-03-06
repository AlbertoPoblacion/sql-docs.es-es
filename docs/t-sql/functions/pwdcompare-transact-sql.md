---
title: PWDCOMPARE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDCOMPARE
- PWDCOMPARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sa account
- passwords [SQL Server], blank
- PWDCOMPARE function [Transact-SQL]
ms.assetid: 5f84ff9e-c1ec-46aa-8501-50f854ebcc3a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 23b90a0d4a09fc2eb754dc5f298883ef4469ade5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Obtiene el valor hash de una contraseña y lo compara con el de otra existente. PWDCOMPARE se puede usar para buscar contraseñas de inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en blanco o contraseñas poco seguras comunes.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 **'** *clear_text_password* **'**  
 Es la contraseña sin cifrar. *clear_text_password* es **sysname** (**nvarchar(128)**).  
  
 *password_hash*  
 Es el valor hash de cifrado de una contraseña. *password_hash* es **varbinary(128)**.  
  
 *version*  
 Parámetro desusado que se puede establecer en 1 si *password_hash* representa un valor de un inicio de sesión anterior a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] que se migró a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o posterior, pero que nunca se convirtió al sistema de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. *version* es **int**.  
  
> [!CAUTION]  
>  Este parámetro se proporciona por compatibilidad con las versiones anteriores, pero se omite porque los blobs de hash de contraseña contienen ahora su propia descripción de versión. [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>Tipos devueltos  
 **int**  
  
 Devuelve 1 si el valor hash de *clear_text_password* coincide con el parámetro *password_hash* y 0 si no coincide.  
  
## <a name="remarks"></a>Notas  
 La función PWDCOMPARE no es una amenaza contra la seguridad de los valores hash de las contraseñas porque podría realizarse la misma prueba intentando iniciar sesión con la contraseña proporcionada como primer parámetro.  
  
 **PWDCOMPARE** no se puede usar con las contraseñas de usuarios de base de datos independiente. No hay una base de datos independiente equivalente.  
  
## <a name="permissions"></a>Permisos  
 PWDENCRYPT está disponible al público.  
  
 Se requiere el permiso CONTROL SERVER para examinar la columna password_hash de sys.sql_logins.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-identifying-logins-that-have-no-passwords"></a>A. Identificar los inicios de sesión que no tienen contraseñas  
 El ejemplo siguiente identifica los inicios de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que no tienen contraseñas.  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('', password_hash) = 1 ;  
```  
  
### <a name="b-searching-for-common-passwords"></a>B. Buscar contraseñas comunes  
 Para buscar contraseñas comunes que desee identificar y cambiar, especifique la contraseña como primer parámetro. Por ejemplo, ejecute la instrucción siguiente para buscar una contraseña especificada como `password`.  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('password', password_hash) = 1 ;  
```  
  
## <a name="see-also"></a>Ver también  
 [PWDENCRYPT &#40;Transact-SQL&#41;](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [Funciones de seguridad &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
