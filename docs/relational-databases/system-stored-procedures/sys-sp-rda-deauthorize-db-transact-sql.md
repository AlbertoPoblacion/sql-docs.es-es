---
title: sys.sp_rda_deauthorize_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6aeb27d4fb452a4ed5b7f45086f601eacb4f0339
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905110"
---
# <a name="syssprdadeauthorizedb-transact-sql"></a>sys.sp_rda_deauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Quita la conexión autenticada entre una base de datos local habilitada para Stretch y la base de datos de Azure remota. Ejecute **sp_rda_deauthorize_db** cuando la base de datos remoto no está accesible o en un estado incoherente y desea cambiar el comportamiento de la consulta para todas las tablas habilitadas para Stretch en la base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o > 0 (error)  
  
## <a name="permissions"></a>Permisos  
 Se requieren permisos db_owner.  
  
## <a name="remarks"></a>Comentarios  
 Después de ejecutar **sp_rda_deauthorize_db** , producirá un error en todas las consultas en tablas y bases de datos habilitadas para Stretch. Es decir, el modo de consulta está establecido en deshabilitado. Para salir de este modo, realice una de las siguientes acciones.  
  
-   Ejecute [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) para volver a conectarse a la base de datos de Azure remota. Esta operación restablece automáticamente el modo de consulta LOCAL_AND_REMOTE, que es el comportamiento predeterminado para Stretch Database. Es decir, las consultas devuelven los resultados de datos locales y remotos.  
  
-   Ejecute [sys.sp_rda_set_query_mode &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) con el argumento LOCAL_ONLY para permitir que las consultas continúan ejecutándose con solo los datos locales.  
  
## <a name="see-also"></a>Vea también  
 [sys.sp_rda_set_query_mode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
