---
title: restorefile (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
author: stevestein
ms.author: sstein
ms.openlocfilehash: 788d0296087ee8980be0b0ecf56c43f09fb3780c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910190"
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una fila por cada archivo restaurado, incluidos los restaurados indirectamente por el nombre de grupo de archivos. Esta tabla se almacena en el **msdb** base de datos.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Número de identificación único que identifica la operación de restauración correspondiente. Referencias **RestoreHistory (restore_history_id)** .|  
|**file_number**|**numeric(10,0)**|Número de identificación de archivo del archivo restaurado. Este número debe ser único en cada base de datos. Puede ser NULL.<br /><br /> Si una base de datos se revierte a una instantánea de base de datos, este valor se llena del mismo modo que en una restauración completa.|  
|**destination_phys_drive**|**nvarchar(260)**|Unidad o partición en la que se ha restaurado el archivo. Puede ser NULL.<br /><br /> Si una base de datos se revierte a una instantánea de base de datos, este valor se llena del mismo modo que en una restauración completa.|  
|**destination_phys_name**|**nvarchar(260)**|Nombre de archivo, sin la información de unidad o partición, en el que se ha restaurado el archivo. Puede ser NULL.<br /><br /> Si una base de datos se revierte a una instantánea de base de datos, este valor se llena del mismo modo que en una restauración completa.|  
  
## <a name="remarks"></a>Comentarios  
 Para reducir el número de filas en esta tabla y de otras tablas de copia de seguridad y el historial, ejecute el [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procedimiento almacenado.  
  
## <a name="see-also"></a>Vea también  
 [Copia de seguridad y restaurar tablas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [Tablas del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
