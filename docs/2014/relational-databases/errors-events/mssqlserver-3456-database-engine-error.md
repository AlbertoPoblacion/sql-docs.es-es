---
title: MSSQLSERVER_3456 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2077d736f15787fe35a4a18d5c03dbd9ddd36a4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2020
ms.locfileid: "62914303"
---
# <a name="mssqlserver_3456"></a>MSSQLSERVER_3456
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|3456|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|REC_REDOLSNMISMATCH|  
|Texto del mensaje|No se pudo rehacer la entrada de registro %S_LSN para el identificador de transacción %S_XID de la página %S_PGID, base de datos '%.*ls' (identificador de base de datos %d). Página: LSN = %S_LSN, tipo = %ld. Registro: OpCode = %ld, contexto %ld, PrevPageLSN: %S_LSN. Restaure la base de datos desde una copia de seguridad o repárela.|  
  
## <a name="explanation"></a>Explicación  
 La operación de restauración no pudo rehacer el registro de transacciones. Este error ha colocado la base de datos en el estado SUSPECT. El grupo de archivos principal, y posiblemente otros grupos de archivos, es sospechoso y puede estar dañado. La base de datos no se puede recuperar durante el inicio de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y, por consiguiente, no está disponible. Se requiere una acción por parte del usuario para resolver el problema.  
  
 Tenga en cuenta que si este error se produce para **tempdb**, la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se cierra.  
  
## <a name="user-action"></a>Acción del usuario  
 Una condición transitoria que se dio en el sistema durante un intento determinado de iniciar la instancia del servidor o recuperar una base de datos puede producir este error. También puede deberse a un error permanente que se produce cada vez que se intenta iniciar la base de datos. Para obtener información acerca de la causa, examine el registro de eventos de Windows para ver si contiene un error anterior que indique el error concreto.  
  
 Para obtener información sobre la causa de esta repetición del error 3456, busque en el registro de eventos de Windows un error anterior que indique el error específico. La acción del usuario adecuada depende de si la información del registro de eventos de Windows indica que el error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo causó una condición transitoria o un error permanente. Para obtener información sobre las acciones del usuario para solucionar el error 3456, consulte los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [Restauraciones de bases de datos completas &#40;modelo de recuperación simple&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md)   
 [MSSQLSERVER_824](mssqlserver-824-database-engine-error.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
