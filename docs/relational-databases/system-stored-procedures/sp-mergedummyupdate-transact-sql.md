---
title: sp_mergedummyupdate (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_mergedummyupdate_TSQL
- sp_mergedummyupdate
helpviewer_keywords:
- sp_mergedummyupdate
ms.assetid: b834f7f6-9588-4d59-a3e2-83d8e8e722e1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46c1fb620db4c4bbe4dde9872897cad07553173a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="spmergedummyupdate-transact-sql"></a>sp_mergedummyupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Realiza una actualización ficticia en la fila especificada de forma que se envíe de nuevo durante la siguiente mezcla. Este procedimiento almacenado se puede ejecutar en el publicador de la base de datos de publicaciones o en el suscriptor de la base de datos de suscripciones.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_mergedummyupdate [ @source_object =] 'source_object', [ @rowguid =] 'rowguid'  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@source_object=**] **'***source_object***'**  
 Es el nombre del objeto de origen. *source_object*es **nvarchar (386)**, no tiene ningún valor predeterminado.  
  
 [  **@rowguid=**] **'***rowguid***'**  
 Es el identificador de fila. *ROWGUID* es **uniqueidentifier**, no tiene ningún valor predeterminado.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_mergedummyupdate** se utiliza en la replicación de mezcla.  
  
 **sp_mergedummyupdate** es útil cuando escriba su propia alternativa al Visor de conflictos de replicación (Wzcnflct.exe).  
  
## <a name="permissions"></a>Permissions  
 Solo los miembros de la **db_owner** rol fijo de base de datos puede ejecutar **sp_mergedummyupdate**.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
