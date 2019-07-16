---
title: sysaltfiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysaltfiles_TSQL
- sys.sysaltfiles
- sysaltfiles_TSQL
- sysaltfiles
dev_langs:
- TSQL
helpviewer_keywords:
- sysaltfiles system table
- sys.sysaltfiles compatibility view
ms.assetid: 698dec23-5336-4108-87a5-f8e407f8da09
author: rothja
ms.author: jroth
ms.openlocfilehash: 891e88761cac47be83fb69debbbc5e4cb6c401c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006982"
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  En circunstancias especiales, contiene filas que corresponden a los archivos de una base de datos.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Número de identificación del archivo. Es un número único para cada base de datos.|  
|**groupid**|**smallint**|Número de identificación del grupo de archivos.|  
|**size**|**int**|Tamaño de archivo, en páginas de 8 kilobytes (KB).|  
|**maxsize**|**int**|Tamaño máximo de archivo, en páginas de 8 KB.<br /><br /> 0 = Sin aumento de tamaño.<br /><br /> -1 = El archivo crece hasta que el disco esté lleno.<br /><br /> 268435456 = El archivo de registro aumentará de tamaño hasta un tamaño máximo de 2 TB.<br /><br /> Nota: Las bases de datos que se actualizan con un tamaño de archivo ilimitado del registro indican -1 para el tamaño máximo del archivo de registro.|  
|**growth**|**int**|Tamaño de aumento de la base de datos.<br /><br /> 0 = Sin aumento de tamaño. Puede ser el número de páginas o el porcentaje del tamaño del archivo, dependiendo del valor de status. Si **estado** es 0 x 100000, **crecimiento** es el porcentaje de archivos de tamaño; en caso contrario, es el número de páginas.|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**perf**|**int**|Reservado.|  
|**dbid**|**smallint**|Número de identificación de la base de datos a la que pertenece este archivo.|  
|**name**|**sysname**|Nombre lógico del archivo.|  
|**filename**|**nvarchar(260)**|Nombre del dispositivo físico. Incluye la ruta de acceso completa al archivo.|  
  
## <a name="see-also"></a>Vea también  
 [Asignar tablas del sistema a vistas del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vistas de compatibilidad &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
