---
title: sp_set_firewall_rule (base de datos de SQL Azure) | Microsoft Docs
ms.custom: ''
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_set_firewall_rule
- sp_set_firewall_rule_TSQL
- sys.sp_set_firewall_rule
- sys.sp_set_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_firewall_rule
- firewall_rules, setting server rules
ms.assetid: a974a561-5382-4039-8499-3a56767bcefe
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 436396ed0982b12fffd5b894cb4c2a4006484ab0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104433"
---
# <a name="spsetfirewallrule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Crea o actualiza la configuración del firewall de nivel de servidor para el servidor [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Este procedimiento almacenado solo está disponible en la base de datos maestra para el inicio de sesión principal de nivel de servidor o la entidad de seguridad de Azure Active Directory asignado.  
  
  
## <a name="syntax"></a>Sintaxis  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 En la tabla siguiente se muestran los argumentos admitidos y opciones en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
|Name|Datatype|Descripción|  
|----------|--------------|-----------------|  
|[@name =] 'name'|**NVARCHAR (128)**|El nombre utilizado para describir y distinguir la configuración del firewall de nivel de servidor.|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR (50)**|La dirección IP más baja en el intervalo de la configuración del firewall de nivel de servidor. Las direcciones IP iguales o superiores a esta pueden intentar conectarse con el servidor [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. La dirección IP más baja posible es `0.0.0.0`.|  
|[@end_ip_address =] 'end_ip_address'|**VARCHAR (50)**|La dirección IP más alta en el intervalo de la configuración del firewall de nivel de servidor. Las direcciones IP iguales o inferiores a esta pueden intentar conectarse con el servidor [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. La dirección IP más alta posible es `255.255.255.255`.<br /><br /> Nota: Se permiten los intentos de conexión de Azure cuando este campo y el *start_ip_address* campo equals `0.0.0.0`.|  
  
## <a name="remarks"></a>Comentarios  
 Los nombres de la configuración del firewall de nivel de servidor deben ser únicos. Si el nombre del valor proporcionado para el procedimiento almacenado ya existe en la tabla de configuración del firewall, las direcciones IP inicial y final se actualizarán. De lo contrario, se creará una nueva configuración del firewall de nivel de servidor.  
  
 Cuando se agrega una configuración de firewall de nivel de servidor donde el principio y final de las direcciones IP son iguales a `0.0.0.0`, habilitar el acceso a su [!INCLUDE[ssSDS](../../includes/sssds-md.md)] servidor de Azure. Proporcione un valor para el *nombre* parámetro que le ayudarán a recordar lo que es la configuración del firewall de nivel de servidor para.  
  
 En [!INCLUDE[ssSDS](../../includes/sssds-md.md)], los datos de inicio de sesión necesarios para autenticar una conexión y reglas de firewall de nivel de servidor se almacenan temporalmente en caché en cada base de datos. Esta caché se actualiza regularmente. Para forzar una actualización de la caché de autenticación y garantizar que una base de datos tenga la versión más reciente de la tabla de inicios de sesión, ejecute [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permisos  
 Solo el nivel de servidor de inicio de sesión principal creados por el proceso de aprovisionamiento o una entidad de Azure Active Directory asignado como administrador puede crear o modificar las reglas de firewall de nivel de servidor. El usuario debe estar conectado a la base de datos maestra para ejecutar sp_set_firewall_rule.  
  
## <a name="examples"></a>Ejemplos  
 El código siguiente crea un firewall de nivel de servidor llamada `Allow Azure` que habilita el acceso de Azure. Ejecute lo siguiente en la base de datos maestra virtual.  
  
```  
-- Enable Windows Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 El código siguiente crea una configuración del firewall de nivel de servidor denominada `Example setting 1` solo para la dirección IP `0.0.0.2`. A continuación, la `sp_set_firewall_rule` se llama al procedimiento almacenado nuevo para actualizar la dirección IP final `0.0.0.4`, ya que la configuración de firewall. Esto crea un intervalo que permite a las direcciones IP `0.0.0.2`, `0.0.0.3`, y `0.0.0.4` para acceder al servidor.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Firewall de base de datos SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Cómo: Configurar el Firewall (Azure SQL Database)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [Sys.firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
