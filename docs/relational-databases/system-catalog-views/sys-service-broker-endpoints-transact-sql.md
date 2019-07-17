---
title: Sys.service_broker_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.service_broker_endpoints_TSQL
- service_broker_endpoints
- service_broker_endpoints_TSQL
- sys.service_broker_endpoints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_broker_endpoints catalog view
ms.assetid: 6979ec9b-0043-411e-aafb-0226fa26c5ba
author: stevestein
ms.author: sstein
ms.openlocfilehash: 33d94bf5a709c2581c6ee99a1e019f4eebcabe0d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132957"
---
# <a name="sysservicebrokerendpoints-transact-sql"></a>sys.service_broker_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esta vista de catálogo contiene una fila por cada extremo de Service Broker. Para cada fila de esta vista, hay una fila correspondiente con el mismo **endpoint_id** en el **sys.tcp_endpoints** vista que contiene los metadatos de configuración de TCP. TCP es el único protocolo permitido para Service Broker.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**\<hereda columnas >**|**--**|Hereda columnas de [sys.endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**is_message_forwarding_enabled**|**bit**|El extremo admite el reenvío de mensajes. Esto se establece inicialmente en **0** (deshabilitado). No acepta valores NULL.|  
|**message_forwarding_size**|**int**|El número máximo de megabytes de **tempdb** permite el espacio que se usará para la que se va a reenviar mensajes. Esto se establece inicialmente en **10**. No acepta valores NULL.|  
|**connection_auth**|**tinyint**|Tipo de autenticación de la conexión necesario para las conexiones con este extremo; uno de los siguientes:<br /><br /> **1** - NTLM<br /><br /> **2** - KERBEROS<br /><br /> **3** -NEGOCIAR<br /><br /> **4** -CERTIFICADO<br /><br /> **5** -NTLM, EL CERTIFICADO<br /><br /> **6** -KERBEROS, CERTIFICADO<br /><br /> **7** -NEGOTIATE, CERTIFICADOS<br /><br /> **8** -CERTIFICADO, NTLM<br /><br /> **9** -CERTIFICADO, KERBEROS<br /><br /> **10** -CERTIFICADO, NEGOTIATE<br /><br /> No acepta valores NULL.|  
|**connection_auth_desc**|**nvarchar(60)**|Descripción del tipo de autenticación de conexión requerido para conexiones a este extremo. Es una de las opciones siguientes:<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM, CERTIFICATE<br /><br /> KERBEROS, CERTIFICATE<br /><br /> NEGOTIATE, CERTIFICATE<br /><br /> CERTIFICATE, NTLM<br /><br /> CERTIFICATE, KERBEROS<br /><br /> CERTIFICATE, NEGOTIATE<br /><br /> QUE ACEPTA VALORES NULL.|  
|**certificate_id**|**int**|Identificador del certificado utilizado para la autenticación, si lo hay.<br /><br /> 0 = Se está utilizando la Autenticación de Windows.|  
|**encryption_algorithm**|**tinyint**|Algoritmo de cifrado. Los siguientes son los valores posibles con sus descripciones y las opciones correspondientes de DDL.<br /><br /> **0** : NONE. Opción DDL correspondiente: Deshabilitado.<br /><br /> **1** :  RC4. Opción DDL correspondiente: {necesario &#124; necesita el algoritmo RC4}.<br /><br /> **2** : AES. Opción DDL correspondiente: Necesita el algoritmo AES.<br /><br /> **3** : NONE, RC4. Opción DDL correspondiente: {admitidas &#124; admite el algoritmo RC4}.<br /><br /> **4** : NINGUNO, AES. Opción DDL correspondiente: Se admite el algoritmo AES.<br /><br /> **5** : RC4, AES. Opción DDL correspondiente: Requiere el algoritmo RC4 AES.<br /><br /> **6** : AES, RC4. Opción DDL correspondiente: Se necesita el algoritmo AES RC4.<br /><br /> **7** : NONE, RC4, AES. Opción DDL correspondiente: Admite el algoritmo RC4 AES.<br /><br /> **8** : NINGUNO, AES, RC4. Opción DDL correspondiente: Se admite el algoritmo AES RC4.<br /><br /> No acepta valores NULL.|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Descripción del algoritmo de cifrado. Los valores posibles y sus opciones correspondientes de DDL se enumeran a continuación:<br /><br /> NINGUNO: Disabled<br /><br /> RC4: {necesario &#124; requiere el algoritmo RC4}<br /><br /> AES: Necesita el algoritmo AES<br /><br /> NONE, RC4: {admite &#124; admite el algoritmo RC4}<br /><br /> NINGUNO, AES: Se admite el algoritmo AES<br /><br /> RC4, AES : Requiere el algoritmo RC4 AES<br /><br /> AES, RC4: Se necesita el algoritmo AES RC4<br /><br /> NONE, RC4, AES: Admite el algoritmo RC4 AES<br /><br /> NINGUNO, AES, RC4: Se admite el algoritmo AES RC4<br /><br /> QUE ACEPTA VALORES NULL.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]  
>  El algoritmo RC4 se admite únicamente por razones de compatibilidad con versiones anteriores. El material nuevo solo se puede cifrar con RC4 o RC4_128 cuando la base de datos tenga el nivel de compatibilidad 90 o 100. (No se recomienda). Use un algoritmo más reciente como uno de los algoritmos AES en su lugar. En [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] y versiones posteriores, el material cifrado con RC4 o RC4_128 se puede descifrar en cualquier nivel de compatibilidad.  
  
## <a name="permissions"></a>Permisos  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)  
  
  
