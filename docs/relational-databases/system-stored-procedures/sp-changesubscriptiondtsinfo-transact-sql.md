---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 55f5597af15a264d85cd31175d570cc33ee47f63
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081301"
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia las propiedades del paquete de Servicios de transformación de datos (DTS) de una suscripción. Este procedimiento almacenado se ejecuta en el suscriptor de la base de datos de suscripción.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @job_id = ] job_id` Es el Id. de trabajo del agente de distribución para la suscripción de inserción. *job_id* es **varbinary (16)** , no tiene ningún valor predeterminado. Para buscar el identificador de trabajo de distribución, ejecute **sp_helpsubscription** o **sp_helppullsubscription**.  
  
`[ @dts_package_name = ] 'dts_package_name'` Especifica el nombre del paquete DTS. *dts_package_name* es un **sysname**, su valor predeterminado es null. Por ejemplo, para especificar un paquete denominado **DTSPub_Package**, especificaría `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'` Especifica la contraseña del paquete. *dts_package_password* es **sysname** con el valor predeterminado es NULL, que especifica que la propiedad de contraseña se dejará sin cambios.  
  
> [!NOTE]  
>  Un paquete DTS debe tener una contraseña.  
  
`[ @dts_package_location = ] 'dts_package_location'` Especifica la ubicación del paquete. *dts_package_location* es un **tipo (12)** , su valor predeterminado es null, que especifica que la ubicación del paquete se debe dejar sin cambios. Puede cambiar la ubicación del paquete a **distribuidor** o **suscriptor**.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_changesubscriptiondtsinfo** se usa para la replicación de instantáneas y replicación transaccional que son las suscripciones de inserción.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor **db_owner** rol fijo de base de datos o el creador de la suscripción puede ejecutar **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
