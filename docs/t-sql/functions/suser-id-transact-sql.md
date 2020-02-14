---
title: SUSER_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs:
- TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: e9bad34cf3d195e4038d794fac913bdb3d16bc91
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "73843562"
---
# <a name="suser_id-transact-sql"></a>SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Devuelve el número de identificación de inicio de sesión del usuario.  
  
> [!NOTE]  
>  A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], SUSER_ID devuelve el valor incluido como **principal_id** en la vista de catálogo **sys.server_principals**.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>Argumentos  
 **'** *login* **'**  
 Nombre de inicio de sesión del usuario. *login* es **nchar**. Si se especifica *login* como **char**, *login* se convierte implícitamente en **nchar**. *login* puede ser cualquier inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o cualquier grupo o usuario de Windows con permiso para conectarse con una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si no se especifica *login*, se devuelve el número de identificación de inicio de sesión para el usuario actual. Si el parámetro contiene la palabra NULL, se devolverá NULL.  
  
## <a name="return-types"></a>Tipos de valor devuelto  
 **int**  
  
## <a name="remarks"></a>Observaciones  
 SUSER_ID devuelve un número de identificación solo para los inicios de sesión aprovisionados de forma explícita en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Este Id. se utiliza en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para realizar un seguimiento de la propiedad y los permisos. Este Id. no equivale al SID del inicio de sesión devuelto por SUSER_SID. Si *login* es un inicio de sesión de SQL Server, el SID se asigna a un GUID. Si *login* es un inicio de sesión o un grupo de Windows, el SID se asigna a un identificador de seguridad de Windows.  
  
 SUSER_SID solo devuelve el SUID de los inicios de sesión que tengan una entrada en la tabla de sistema **syslogins**.  
  
 Es posible utilizar funciones de sistema en la lista de selección, en la cláusula WHERE y en cualquier lugar donde se admita una expresión, pero deberán ir seguidas siempre de paréntesis incluso si no se especifica ningún parámetro.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se obtiene el número de identificación del nombre de inicio de sesión `sa`.  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>Consulte también  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Funciones del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
