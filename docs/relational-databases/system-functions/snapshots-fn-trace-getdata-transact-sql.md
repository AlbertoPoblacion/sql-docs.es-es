---
title: Snapshots.fn_trace_getdata (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
author: rothja
ms.author: jroth
ms.openlocfilehash: a85a911d4c9f5cd4565e9839f3be44a4e2366079
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067752"
---
# <a name="snapshotsfntracegetdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esta función devuelve todos los eventos capturados para el seguimiento especificado.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Argumentos  
 *trace_info_id*  
 El identificador único para la clave principal en la tabla snapshots.trace_info de los datos de administración de almacenamiento de base de datos. *trace_info_id* es **int**.  
  
 *start_time*  
 Hora a la que empezó el seguimiento. *start_time* es **datetime**.  
  
 *end_time*  
 Hora a la que finalizó el seguimiento. *end_time* es **datetime**.  
  
## <a name="table-returned"></a>Tabla devuelta  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|\<Todas las columnas de seguimiento >|\<Varía >|Datos de seguimiento de la tabla snapshots.trace_data de la base de datos del almacén de administración de datos.<br /><br /> Una lista de las columnas para el objeto trace especificado se puede obtener mediante el uso de la consulta siguiente:<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Nota:** Las columnas devueltas por la función snapshots.fn_trace_gettable corresponden a los valores de la columna de nombre de la vista del sistema sys.trace_columns. La única diferencia es que la función no devuelve la columna GroupID.|  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso SELECT para mdw_reader.  
  
## <a name="see-also"></a>Vea también  
 [Recopilación de datos](../../relational-databases/data-collection/data-collection.md)  
  
  
