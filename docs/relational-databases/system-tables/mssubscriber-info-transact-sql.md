---
title: MSsubscriber_info (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: acbbf203509f1d2ddd4c3604e8cfce8067132d76
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriberinfo-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El **MSsubscriber_info** tabla contiene una fila por cada par de publicador y suscriptor que se insertan suscripciones desde el distribuidor local. Esta tabla se almacena en la base de datos de distribución.  
  
 **Tenga en cuenta** esta tabla del sistema ha quedado desusada y se mantiene para admitir las versiones anteriores de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="definition"></a>Definición  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**publicador**|**sysname**|El nombre del publicador.|  
|**suscriptor**|**sysname**|Nombre del suscriptor.|  
|**tipo**|**tinyint**|El tipo de suscriptor:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suscriptor.<br /><br /> **1** = origen de datos ODBC.|  
|**inicio de sesión**|**sysname**|Inicio de sesión para la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se almacena en formato cifrado si se agrega el suscriptor con el modo de autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**contraseña**|**nvarchar (524)**|Contraseña para la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se almacena en formato cifrado si se agrega el suscriptor con el modo de autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Descripción**|**nvarchar(255)**|La descripción del suscriptor.|  
|**security_mode**|**int**|Modo de seguridad implementado:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticación.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] autenticación de Windows.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
