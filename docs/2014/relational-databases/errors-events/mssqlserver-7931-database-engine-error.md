---
title: MSSQLSERVER_7931 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7931 (Database Engine error)
ms.assetid: 18e7a3dc-7d8a-41b9-8724-d2a8587b6903
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b05013b888978d268d30a31dc6375b0f70d625d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62762106"
---
# <a name="mssqlserver7931"></a>MSSQLSERVER_7931
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|7931|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC2_FS_DOUBLE_ROWSET_ACTUAL_FACT|  
|Texto del mensaje|Error de base de datos: El directorio FileStream F_ID de identificador para una partición se ha visto dos veces.|  
  
## <a name="explanation"></a>Explicación  
 Se ha encontrado en los metadatos el mismo identificador de partición para un directorio FILESTREAM.  
  
## <a name="user-action"></a>Acción del usuario  
  
### <a name="look-for-hardware-failure"></a>Busque un error de hardware  
 Ejecute un diagnóstico de hardware y corrija cualquier problema. Examine también los registros del sistema y de aplicación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows así como el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ver si el error se produjo como resultado de un error de hardware. Arregle cualquier problema relacionado con el hardware que encuentre en estos registros.  
  
 Si sigue teniendo problemas de datos dañados, intente intercambiar diferentes componentes de hardware para aislar el problema. Asegúrese de que el sistema no tiene habilitada la memoria caché de escritura en el controlador de disco. Si cree que el problema se debe a la caché de escritura, póngase en contacto con su proveedor de hardware.  
  
 Finalmente, puede resultarle útil cambiar a un nuevo sistema de hardware. Este cambio puede incluir volver a formatear las unidades de disco y volver a instalar el sistema operativo.  
  
### <a name="restore-from-backup"></a>Restaure mediante la copia de seguridad  
 Si el problema no está relacionado con el hardware y tiene una copia de seguridad limpia disponible, úsela para restaurar la base de datos.  
  
### <a name="run-dbcc-checkdb"></a>Ejecute DBCC CHECKDB  
 No aplicable. Este error no puede repararse automáticamente. Si no puede restaurar la base de datos a partir de una copia de seguridad, póngase en contacto con el servicio de soporte técnico y atención al cliente (CSS) de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
