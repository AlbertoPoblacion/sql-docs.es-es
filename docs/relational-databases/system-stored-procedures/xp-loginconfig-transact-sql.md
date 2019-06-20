---
title: xp_loginconfig (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_loginconfig_TSQL
- xp_loginconfig
dev_langs:
- TSQL
helpviewer_keywords:
- xp_loginconfig
ms.assetid: d380e799-2857-408a-bcbf-5e73a8e6aa5a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8590a33f870dc14ac34118ce5e655acc6e67f257
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62645104"
---
# <a name="xploginconfig-transact-sql"></a>xp_loginconfig (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Informa de la configuración de seguridad de inicio de sesión de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
xp_loginconfig ['config_name']  
```  
  
## <a name="arguments"></a>Argumentos  
 **'** *config_name* **'**  
 Es el valor de configuración que se va a mostrar. Si *config_name* no es se especifica, se notifican todos los valores de configuración. *config_name* es **sysname**, su valor predeterminado es null, y puede tener uno de estos valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**modo de inicio de sesión**|Modo de seguridad de inicio de sesión. Los valores posibles son **mixto** y **Windows autenticación**.<br /><br /> Se reemplaza por:<br /><br /> `SELECT SERVERPROPERTY('IsIntegratedSecurityOnly'); GO`|  
|**inicio de sesión predeterminado**|Nombre del Id. de inicio de sesión predeterminado de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para usuarios autorizados de conexiones de confianza (para usuarios sin nombre de inicio de sesión). El inicio de sesión predeterminado es **invitado**. Este valor se proporciona por motivos de compatibilidad con versiones anteriores.|  
|**Dominio predeterminado**|Nombre del dominio de Windows predeterminado para los usuarios de red de conexiones de confianza. El dominio predeterminado es el dominio del que es miembro el equipo de Windows que ejecuta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Este valor se proporciona por motivos de compatibilidad con versiones anteriores.|  
|**nivel de auditoría**|Nivel de auditoría. Los valores posibles son **ninguno**, **éxito**, **error**, y **todas**. Las auditorías se escriben en el registro de errores y en el Visor de eventos de Windows.|  
|**nombre de host de conjunto**|Indica si el nombre del host desde el que se registra el cliente se sustituye por el nombre de usuario de la red de Windows. Los valores posibles son **true** o **false**. Si se establece, el nombre de usuario de red aparece en la salida de **sp_who**.|  
|**map _**|Informa de los caracteres especiales de Windows asignados al carácter de subrayado (_) válido en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los valores posibles son **separador dominio** (valor predeterminado), **espacio**, **null**, o cualquier carácter individual. Este valor se proporciona por motivos de compatibilidad con versiones anteriores.|  
|**asignar $**|Informa de los caracteres especiales de Windows asignados al carácter de dólar ($) válido en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los valores posibles son **separador dominio**, **espacio**, **null**, o cualquier carácter individual. El valor predeterminado es **espacio**. Este valor se proporciona por motivos de compatibilidad con versiones anteriores.|  
|**asignar #**|Informa de los caracteres especiales de Windows asignados al carácter de número (#) válido en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los valores posibles son **separador dominio**, **espacio**, **null**, o cualquier carácter individual. El valor predeterminado es el guión. Este valor se proporciona por motivos de compatibilidad con versiones anteriores.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**Nombre**|**sysname**|Valor de configuración|  
|**valor de configuración**|**sysname**|Ajuste de valor de configuración|  
  
## <a name="remarks"></a>Comentarios  
 **xp_loginconfig** no se puede usar para establecer los valores de configuración.  
  
 Para establecer el modo de inicio de sesión y el nivel de auditoría, utilice [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso CONTROL en el **maestro** base de datos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-how-to-report-all-configuration-values"></a>A. Cómo presentar todos los valores de configuración  
 En el ejemplo siguiente se muestran todos los valores de configuración actuales.  
  
```  
EXEC xp_loginconfig;  
GO  
```  
  
### <a name="b-how-to-report-a-specific-configuration-value"></a>b. Cómo presentar un valor de configuración específico  
 En el ejemplo siguiente solo se muestra la configuración del modo de inicio de sesión.  
  
```  
EXEC xp_loginconfig 'login mode';  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
