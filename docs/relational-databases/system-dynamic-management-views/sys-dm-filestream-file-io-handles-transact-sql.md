---
title: Sys.dm_filestream_file_io_handles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: a96bcedaa3922ebb0691ac949f9eb15ed28336b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103302"
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Muestra los identificadores de archivo que conoce el propietario del espacio de nombres (NSO). Controladores de FileStream que se obtuvo un cliente con **OpenSqlFilestream** se muestran en esta vista.  
  
|columna|Type|Descripción|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Muestra la dirección de la estructura NSO interna asociada con el identificador del cliente. Acepta valores NULL.|  
|**creation_request_id**|**int**|Muestra un campo desde la solicitud de E/S de REQ_PRE_CREATE usada para crear este controlador. No admite valores NULL.|  
|**creation_irp_id**|**int**|Muestra un campo desde la solicitud de E/S de REQ_PRE_CREATE usada para crear este controlador. No admite valores NULL|  
|**handle_id**|**int**|Muestra el identificador único de este controlador asignado por el controlador. No admite valores NULL.|  
|**creation_client_thread_id**|**varbinary(8)**|Muestra un campo desde la solicitud de E/S de REQ_PRE_CREATE usada para crear este controlador. Acepta valores NULL.|  
|**creation_client_process_id**|**varbinary(8)**|Muestra un campo desde la solicitud de E/S de REQ_PRE_CREATE usada para crear este controlador. Acepta valores NULL.|  
|**filestream_transaction_id**|**varbinary(128)**|Muestra el identificador de la transacción asociado con el controlador determinado. Este es el valor devuelto por la **get_filestream_transaction_context** función. Utilice este campo para unirse a la **sys.dm_filestream_file_io_requests** vista. Acepta valores NULL.|  
|**access_type**|**nvarchar(60)**|No admite valores NULL.|  
|**logical_path**|**nvarchar(256)**|Muestra el nombre de ruta de acceso lógico del archivo que abrió este controlador. Se trata de la misma ruta de acceso devuelta por la **. PathName** método **varbinary**(**max**) filestream. Acepta valores NULL.|  
|**physical_path**|**nvarchar(256)**|Muestra el nombre de ruta de acceso NTFS real del archivo. Se trata de la misma ruta de acceso devuelta por la **. PhysicalPathName** método de la **varbinary**(**max**) filestream. Lo habilita la marca de seguimiento 5556. Acepta valores NULL.|  
  
## <a name="permissions"></a>Permisos  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [FileStream y vistas de administración dinámica de FileTable &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
