---
title: Sys.database_role_members (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.database_role_members_TSQL
- sys.database_role_members
- database_role_members_TSQL
- database_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_role_members catalog view
ms.assetid: ed1b019d-ca48-4db3-85df-cf6d2db591cf
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: abe12465ae80a9373475a0158cdacc663b8f00fa
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sysdatabaserolemembers-transact-sql"></a>sys.database_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve una fila por cada miembro de cada rol de base de datos.  Los usuarios de base de datos, roles de aplicación y otras funciones de base de datos pueden ser miembros de un rol de base de datos. Para agregar miembros a un rol, use la [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) instrucción con el `ADD MEMBER` opción. Combinar con [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) para devolver los nombres de los `principal_id` valores.
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|Identificador de entidad de seguridad de base de datos de la función.|  
|**member_principal_id**|**int**|Identificador de entidad de seguridad de base de datos del miembro.|  
  
## <a name="permissions"></a>Permissions  
 Cualquier usuario puede ver su propia pertenencia a roles. Para ver otro rol pertenencias requiere la pertenencia a la `db_securityadmin` rol fijo de base de datos o `VIEW DEFINITION` en la base de datos.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="example"></a>Ejemplo  
 La consulta siguiente devuelve a los miembros de los roles de base de datos.  
  
```  
SELECT DP1.name AS DatabaseRoleName,   
   isnull (DP2.name, 'No members') AS DatabaseUserName   
 FROM sys.database_role_members AS DRM  
 RIGHT OUTER JOIN sys.database_principals AS DP1  
   ON DRM.role_principal_id = DP1.principal_id  
 LEFT OUTER JOIN sys.database_principals AS DP2  
   ON DRM.member_principal_id = DP2.principal_id  
WHERE DP1.type = 'R'
ORDER BY DP1.name;  
```  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Entidades de seguridad &#40;motor de base de datos&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
[MODIFICAR rol (Transact-SQLL)](../../t-sql/statements/alter-role-transact-sql.md)      
[Sys.server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
  


