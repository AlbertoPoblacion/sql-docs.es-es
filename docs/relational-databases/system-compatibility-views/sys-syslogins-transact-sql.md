---
title: Sys.syslogins (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1b5b0d9ec9b28236816062fefdb0d022a0c9a498
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una fila por cada cuenta de inicio de sesión.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a través de la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**sid**|**varbinary(85)**|Identificador de seguridad.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|Fecha en que se agregó el inicio de sesión.|  
|**updatedate**|**datetime**|Fecha en que se actualizó el inicio de sesión.|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**timelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Nombre**|**sysname**|Nombre de inicio de sesión del usuario.|  
|**dbname**|**sysname**|Nombre de la base de datos predeterminada del usuario al establecer una conexión.|  
|**password**|**nvarchar(128)**|Devuelve NULL.|  
|**idioma**|**sysname**|Idioma predeterminado del usuario.|  
|**denylogin**|**int**|1 = El inicio de sesión corresponde a un usuario o grupo de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows al que se le ha denegado el acceso.|  
|**hasaccess**|**int**|1 = El inicio de sesión tiene acceso al servidor.|  
|**isntname**|**int**|1 = El inicio de sesión corresponde a un usuario o grupo de Windows.<br /><br /> 0 = Es un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |  
|**isntgroup**|**int**|1 = El inicio de sesión corresponde a un grupo de Windows.|  
|**isntuser**|**int**|1 = El inicio de sesión corresponde a un usuario de Windows.|  
|**sysadmin**|**int**|1 = Inicio de sesión es miembro de la **sysadmin** rol de servidor.|  
|**securityadmin**|**int**|1 = Inicio de sesión es miembro de la **securityadmin** rol de servidor.|  
|**serveradmin**|**int**|1 = Inicio de sesión es miembro de la **serveradmin** rol fijo de servidor.|  
|**setupadmin**|**int**|1 = Inicio de sesión es miembro de la **setupadmin** rol fijo de servidor.|  
|**processadmin**|**int**|1 = Inicio de sesión es miembro de la **processadmin** rol fijo de servidor.|  
|**diskadmin**|**int**|1 = Inicio de sesión es miembro de la **diskadmin** rol fijo de servidor.|  
|**dbcreator**|**int**|1 = Inicio de sesión es miembro de la **dbcreator** rol fijo de servidor.|  
|**bulkadmin**|**int**|1 = Inicio de sesión es miembro de la **bulkadmin** rol fijo de servidor.|  
|**loginname**|**nvarchar(128)**|Nombre de inicio de sesión del usuario. Se proporciona para mantener la compatibilidad con versiones anteriores.|  
  
## <a name="see-also"></a>Vea también  
 [Asignar tablas del sistema a vistas del sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vistas de compatibilidad &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
