---
title: MSSQLSERVER_1457 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4f45545212b494f955c6b9be97ccf0df7efeb622
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62869917"
---
# <a name="mssqlserver1457"></a>MSSQLSERVER_1457
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|1457|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBM_PAGE_UNDO_PENDING|  
|Texto del mensaje|Se interrumpió la sincronización de la base de datos reflejada, '%.*ls' y ésta quedó en un estado incoherente. Error del comando ALTER DATABASE. Asegúrese de que hay una copia de seguridad la base de datos reflejada y de que la base de datos está en línea, y vuelva a conectar la instancia del servidor reflejado y permita que la base de datos reflejada finalice la sincronización.|  
  
## <a name="explanation"></a>Explicación  
 Este mensaje indica un error en la instrucción ALTER DATABASE *nombreDeBaseDeDatos* SET PARTNER OFF. El error al intentar quitar el reflejo de la base de datos ha interrumpido la sincronización de la base de datos reflejada. La base de datos se encuentra en un estado incoherente.  
  
## <a name="user-action"></a>Acción del usuario  
 Para solucionar este error, puede realizar una de las siguientes acciones:  
  
-   Restaure el contacto entre el servidor reflejado y el principal para permitir la sincronización de la base de datos reflejada.  
  
-   Quite la base de datos reflejada.  
  
     Después de quitar la base de datos reflejada, puede crear una nueva base de datos reflejada a partir de las copias de seguridad.  
  
    > [!NOTE]  
    >  Puede quitar la base de datos reflejada cuando está todavía habilitada la creación de reflejo solo después de un error de instrucción SET PARTNER OFF.  
  
## <a name="see-also"></a>Vea también  
 [Creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Configurar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)   
 [Quitar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md)   
 [Preparar una base de datos reflejada para la creación de reflejo &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
