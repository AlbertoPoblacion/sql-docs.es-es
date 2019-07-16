---
title: Sys.change_tracking_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- change_tracking_tables_TSQL
- sys.change_tracking_tables
- change_tracking_tables
- sys.change_tracking_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], sys.change_tracking_tables
- sys.change_tracking_tables
ms.assetid: 97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 158203b7dedfec3228821f6368c8f6c92b8041f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050871"
---
# <a name="change-tracking-catalog-views---syschangetrackingtables"></a>Cambiar las vistas de catálogo de seguimiento - sys.change_tracking_tables
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Devuelve una fila por cada tabla en la base de datos actual que tiene habilitado el seguimiento de cambios.  
   
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Id. de una tabla que contiene un diario de cambios. La tabla puede contener un diario de cambios aun cuando el seguimiento de cambios esté actualmente deshabilitado.<br /><br /> El Id. de tabla es único en la base de datos.|  
|is_track_columns_updated_on|**bit**|El estado actual de seguimiento de cambios en la tabla:<br /><br /> 0 = OFF<br /><br /> 1 = ON|  
|begin_version|**bigint**|Versión de la base de datos cuando se inició el seguimiento de cambios para la tabla. Normalmente, esta versión indica si el seguimiento de cambios estaba habilitado, pero se restablece este valor si se trunca la tabla.|  
|cleanup_version|**bigint**|Versión hasta la que el proceso de limpieza podría haber quitado la información de seguimiento de cambios.|  
|min_valid_version|**bigint**|Versión válida mínima de la información de seguimiento de cambios disponible para la tabla.<br /><br /> Al obtener los cambios de la tabla asociada a esta fila, el valor de last_sync_version debe ser mayor o igual que la versión indicada por la columna. Para obtener más información, consulte [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md).|  
  
## <a name="permissions"></a>Permisos  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [Vistas de catálogo de seguimiento de cambios &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Seguimiento de cambios de datos &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
