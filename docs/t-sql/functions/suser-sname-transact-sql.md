---
title: SUSER_SNAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SUSER_SNAME_TSQL
- SUSER_SNAME
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- SIDs [SQL Server]
- SUSER_SNAME function
- users [SQL Server], logins
- logins [SQL Server], names
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- names [SQL Server], logins
ms.assetid: 11ec7d86-d429-4004-a436-da25df9f8761
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80defa93fb82a5a6b451acd00c8336a74a06ba34
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948198"
---
# <a name="susersname-transact-sql"></a>SUSER_SNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve el nombre de inicio de sesión asociado a un número de identificación de seguridad (SID).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SUSER_SNAME ( [ server_user_sid ] )   
```  
  
## <a name="arguments"></a>Argumentos  
 *server_user_sid*  
**Se aplica a**: de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Se trata del número de identificación opcional de seguridad del inicio de sesión. *server_user_sid* es **varbinary(85)**. *server_user_sid* puede ser el número de identificación de seguridad de cualquier inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], o de un usuario o grupo de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Si no se especifica *server_user_sid*, se devuelve información acerca del usuario actual. Si el parámetro contiene la palabra NULL, se devolverá NULL.  
  
## <a name="return-types"></a>Tipos devueltos  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Notas  
 SUSER_SNAME puede usarse como una restricción DEFAULT en ALTER TABLE o CREATE TABLE. Se puede utilizar SUSER_SNAME en una lista de selección, en la cláusula WHERE y en cualquier lugar en el que se permita una expresión. SUSER_SNAME siempre debe ir seguida de paréntesis, aunque no se especifique ningún parámetro.  
  
 Si se llama sin un argumento, SUSER_SNAME devuelve el nombre del contexto de seguridad actual. Si se llama sin un argumento en un lote que ha cambiado de contexto mediante EXECUTE AS, SUSER_SNAME devuelve el nombre del contexto suplantado. Si se llama desde un contexto suplantado, ORIGINAL_LOGIN devuelve el nombre del contexto original.  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-remarks"></a>Comentarios para [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 SUSER_NAME siempre devuelve el nombre de inicio de sesión para el contexto de seguridad actual.  
  
 La instrucción SUSER_SNAME no admite la ejecución con un contexto de seguridad suplantado a través de EXECUTE AS.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-susersname"></a>A. Usar SUSER_SNAME  
 En el ejemplo siguiente se devuelve el nombre de inicio de sesión para el contexto de seguridad actual.  
  
```  
SELECT SUSER_SNAME();  
GO  
```  
  
### <a name="b-using-susersname-with-a-windows-user-security-id"></a>B. Usar SUSER_SNAME con un identificador de seguridad de usuario de Windows  
 En el siguiente ejemplo se devuelve el nombre de inicio de sesión asociado a un número de identificación de seguridad de Windows.  
  
**Se aplica a**: de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(0x010500000000000515000000a065cf7e784b9b5fe77c87705a2e0000);  
GO  
```  
  
### <a name="c-using-susersname-as-a-default-constraint"></a>C. Usar SUSER_SNAME como una restricción DEFAULT  
 En el ejemplo siguiente se utiliza `SUSER_SNAME` como restricción `DEFAULT` en una instrucción `CREATE TABLE`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sname_example  
(  
login_sname sysname DEFAULT SUSER_SNAME(),  
employee_id uniqueidentifier DEFAULT NEWID(),  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sname_example DEFAULT VALUES;  
GO  
```  
  
### <a name="d-calling-susersname-in-combination-with-execute-as"></a>D. Llamar a SUSER_SNAME junto con EXECUTE AS  
 En este ejemplo se muestra el comportamiento de SUSER_SNAME si se llama desde un contexto suplantado.  
  
**Se aplica a**: de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME();  
GO  
EXECUTE AS LOGIN = 'WanidaBenShoof';  
SELECT SUSER_SNAME();  
REVERT;  
GO  
SELECT SUSER_SNAME();  
GO  
  
```  
  
 Este es el resultado.  
  
 ```
sa  
WanidaBenShoof  
sa
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-susersname"></a>E. Usar SUSER_SNAME  
 En el ejemplo siguiente se obtiene el nombre de inicio de sesión que corresponde al número de identificación de seguridad con un valor de `0x01`.  
  
```  
SELECT SUSER_SNAME(0x01);  
GO  
```  
  
### <a name="f-returning-the-current-login"></a>F. Devolución de inicio de sesión actual  
 En el ejemplo siguiente se devuelve el nombre de inicio de sesión del inicio de sesión actual.  
  
```  
SELECT SUSER_SNAME() AS CurrentLogin;  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [SUSER_SID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Entidades de seguridad &#40;motor de base de datos&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  

