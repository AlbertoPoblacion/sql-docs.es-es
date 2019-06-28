---
title: sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7fc6025cae0c0b265553b8380de27699d4cb1cba
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413023"
---
# <a name="sppdwdatabaseencryptionregeneratesystemkeys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Use **sp_pdw_database_encryption_regenerate_system_keys** rotar la clave de cifrado del certificado y la base de datos para bases de datos internas que se cifran cuando TDE está habilitado en el dispositivo. incluidos `tempdb`. Esto se realizará correctamente solo si TDE está habilitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 El procedimiento no tiene parámetros.  
  
 Este procedimiento debe usarse cuando el tráfico en el dispositivo sea bajo.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer a la **sysadmin** fijo de base de datos, o **CONTROL SERVER** permiso.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente se vuelve a generar las claves de cifrado de base de datos.  
  
```sql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>Vea también  
 [sp_pdw_database_encryption para &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
