---
title: sys.dm_server_registry (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_registry_TSQL
- sys.dm_server_registry
- dm_server_registry
- sys.dm_server_registry_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_registry dynamic management view
ms.assetid: 9b3e0c74-2e99-4996-a383-104d51831e97
author: stevestein
ms.author: sstein
ms.openlocfilehash: d8b91540724b30ac42f0f8c4302e58b3d40ec066
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090724"
---
# <a name="sysdmserverregistry-transact-sql"></a>sys.dm_server_registry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve instalación de configuración y información que se almacena en el Registro de Windows para la instancia actual de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Devuelve una fila por cada clave del Registro. Use esta vista de administración dinámica para devolver información como los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles en el equipo host o los valores de configuración de red para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|registry_key|**nvarchar(256)**|Nombre de clave del Registro. Acepta valores NULL.|  
|value_name|**nvarchar(256)**|Nombre del valor de clave. Este es el elemento que se muestra en el **nombre** del Editor del registro de la columna. Acepta valores NULL.|  
|value_data|**sql_variant**|Valor de los datos de la clave. Este es el valor se muestra en el **datos** columna del Editor del registro para una entrada determinada. Acepta valores NULL.|  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permisos  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-display-the-sql-server-services"></a>A. Mostrar los servicios SQL Server  
 En el ejemplo siguiente se devuelven los valores de clave del Registro para los servicios SQL Server y Agente SQL Server para la instancia actual de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%ControlSet%';  
```  
  
### <a name="b-display-the-sql-server-agent-registry-key-values"></a>b. Mostrar los valores de clave del Registro del Agente SQL Server  
 En el ejemplo siguiente se devuelven los valores de clave del Registro del Agente SQL Server para la instancia actual de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SQLAgent%';  
```  
  
### <a name="c-display-the-current-version-of-the-instance-of-sql-server"></a>C. Mostrar la versión actual de la instancia de SQL Server  
 En el ejemplo siguiente se devuelve la versión de la instancia actual de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key = N'CurrentVersion';  
```  
  
### <a name="d-display-the-parameters-passed-to-the-instance-of-sql-server-during-startup"></a>D. Mostrar los parámetros pasados a la instancia de SQL Server durante el inicio  
 En el ejemplo siguiente se devuelven los parámetros que se pasan a la instancia de SQL Server durante el inicio.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%Parameters';  
```  
  
### <a name="e-return-network-configuration-information-for-the-instance-of-sql-server"></a>E. Devolver información de configuración de red para la instancia de SQL Server  
 En el ejemplo siguiente se devuelven los valores de configuración de red para la instancia actual de SQL Server.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SuperSocketNetLib%';  
```  
  
## <a name="see-also"></a>Vea también  
 [sys.dm_server_services &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md)  
  
  
