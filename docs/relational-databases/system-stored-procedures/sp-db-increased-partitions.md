---
title: sp_db_increased_partitions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73f3eca2a2e7943d8911144a3657e4f826d9739c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62506727"
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Habilita o deshabilita la compatibilidad con hasta 15.000 particiones de la base de datos especificada.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @dbname= ] '*database_name*'  
 Es el nombre de la base de datos. *dbname* es **sysname** con un valor predeterminado es null. Si *dbname* no se especifica, se usa la base de datos actual.  
  
 [ @increased_partitions=] '*increased_partitions*'  
 Habilita o deshabilita la compatibilidad con 15.000 particiones en la base de datos especificada. *increased_partitions* es **varchar(6)** con el valor predeterminado es NULL. Los valores aceptados son 'ON' o 'TRUE' para habilitar la compatibilidad y 'OFF' o 'FALSE' para deshabilitarla. Si *increased_partitions* no se especifica, el procedimiento devuelve 1 para indicar la compatibilidad está habilitada para la base de datos especificada o 0 para indicar la compatibilidad está deshabilitada.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="permissions"></a>Permisos  
 Necesita el permiso ALTER DATABASE en la base de datos especificada.  
  
  
