---
title: column encryption enclave type (opción de configuración del servidor) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: ec0b088d7ed1f32661a9ca171eb5f889c09ae5d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68012798"
---
# <a name="column-encryption-enclave-type-server-configuration-option"></a>column encryption enclave type (opción de configuración del servidor)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Use la opción **column encryption enclave type** para habilitar o deshabilitar un enclave seguro para Always Encrypted.  Para obtener más información, consulte [Always Encrypted con enclaves seguros](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

 En la tabla siguiente se enumeran los posibles valores de **column encryption enclave type**:  
  
|Valor|Descripción|  
|-------------------|-----------------|  
|0|**Sin enclave seguro**. El [!INCLUDE[ssDE](../../includes/ssde-md.md)] no inicializará el enclave seguro para Always Encrypted. Como resultado, la funcionalidad de Always Encrypted con enclaves seguros no estará disponible.|  
|1|**Seguridad basada en la virtualización (VBS)** . El [!INCLUDE[ssDE](../../includes/ssde-md.md)] inicializará el enclave seguro (un enclave de memoria seguro de VBS) para Always Encrypted.|    

> [!IMPORTANT]
> Los cambios efectuados en la opción **column encryption enclave type** no surtirán efecto hasta que reinicie la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
   
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se habilita el enclave seguro:  

```sql  
sp_configure 'column encryption enclave type', 1;  
GO  
RECONFIGURE;  
GO  
```  

En el ejemplo siguiente se deshabilita el enclave seguro:  

```sql  
sp_configure 'column encryption enclave type', 0;  
GO  
RECONFIGURE;  
GO  
```  

## <a name="see-also"></a>Consulte también  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
