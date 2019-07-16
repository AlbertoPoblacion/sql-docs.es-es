---
title: Sys.sysdatabases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b0dab1ca5f21ced6a54192a4b0173ead68fd6f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089164"
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contiene una fila por cada base de datos en una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cuando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se instala por primera vez, **sysdatabases** contiene entradas para el **maestro**, **modelo**, **msdb**y **tempdb** bases de datos.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nombre de la base de datos|  
|**dbid**|**smallint**|Id. de base de datos|  
|**sid**|**varbinary(85)**|Id. de sistema del creador de la base de datos|  
|**mode**|**smallint**|Utilizado internamente para bloquear una base de datos mientras se crea.|  
|**status**|**int**|Bits de estado, algunos de los cuales se pueden establecer mediante el uso de [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) como se indica:<br /><br /> 1 = **autoclose** (ALTER DATABASE)<br /><br /> 4 = **select / into** (ALTER DATABASE con SET RECOVERY)<br /><br /> 8 = **trunc. log en chkpt** (ALTER DATABASE con SET RECOVERY)<br /><br /> 16 = **rasgado la detección de página** (ALTER DATABASE)<br /><br /> 32 = **cargar**<br /><br /> 64 = **recuperación previa**<br /><br /> 128 = **recuperación**<br /><br /> 256 = **no ha recuperado**<br /><br /> 512 = **sin conexión** (ALTER DATABASE)<br /><br /> 1024 = **de sólo lectura** (ALTER DATABASE)<br /><br /> 2048 = **sólo para uso dbo** (ALTER DATABASE con SET RESTRICTED_USER)<br /><br /> 4096 = **solo usuario** (ALTER DATABASE)<br /><br /> 32768 = **modo de emergencia**<br /><br /> 65536 = **SUMA DE COMPROBACIÓN** (ALTER DATABASE)<br /><br /> 4194304 = **autoshrink** (ALTER DATABASE)<br /><br /> 1073741824 = **cerrado**<br /><br /> Puede haber varios bits establecidos en ON a la vez.|  
|**status2**|**int**|16384 = **null ANSI predeterminado** (ALTER DATABASE)<br /><br /> 65536 = **concatenar valores null produce null** (ALTER DATABASE)<br /><br /> 131072 = **los desencadenadores recursivos** (ALTER DATABASE)<br /><br /> 1048576 = **predeterminado al cursor local** (ALTER DATABASE)<br /><br /> 8388608 = **identificador entrecomillado** (ALTER DATABASE)<br /><br /> 33554432 = **cierre del cursor al confirmar** (ALTER DATABASE)<br /><br /> 67108864 = **valores NULL ANSI** (ALTER DATABASE)<br /><br /> 268435456 = **advertencias ANSI** (ALTER DATABASE)<br /><br /> 536870912 = **habilitado de texto completo** (establecer mediante **sp_fulltext_database**)|  
|**crdate**|**datetime**|Fecha de creación|  
|**reserved**|**datetime**|Reservado para uso futuro.|  
|**category**|**int**|Contiene un mapa de bits de información utilizado en la replicación:<br /><br /> 1 = Publicado para réplica de instantáneas o replicación transaccional.<br /><br /> 2 = Suscrito a una publicación de instantáneas o transaccional.<br /><br /> 4 = Publicado para replicación de mezcla.<br /><br /> 8 = Suscrito a una publicación de combinación.<br /><br /> 16 = Base de datos de distribución.|  
|**cmptlevel**|**tinyint**|Nivel de compatibilidad para la base de datos. Para obtener más información, vea [Nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|  
|**filename**|**nvarchar(260)**|Ruta de acceso y nombre en el sistema operativo del archivo principal de la base de datos.<br /><br /> **nombre de archivo** es visible para **dbcreator**, **sysadmin**, el propietario de la base de datos con permisos CREATE ANY DATABASE o receptores que dispongan de uno de los siguientes permisos: MODIFICAR CUALQUIER BASE DE DATOS, CREAR CUALQUIER BASE DE DATOS, VER CUALQUIER DEFINICIÓN. Para devolver la ruta de acceso y nombre de archivo, consulte el [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md) vista de compatibilidad, o la [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) vista.|  
|**version**|**smallint**|Número interno de versión del código de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con el que se creó la base de datos. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Asignar tablas del sistema a vistas del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vistas de compatibilidad &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
