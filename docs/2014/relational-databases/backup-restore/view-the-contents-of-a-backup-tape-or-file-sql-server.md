---
title: Ver el contenido de una cinta o un archivo de copia de seguridad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- displaying backup content
- viewing backup content
- tape backup devices, viewing contents
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dfee2d0f32ffaaf73527effdeea13d43b83a39fb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62921228"
---
# <a name="view-the-contents-of-a-backup-tape-or-file-sql-server"></a>Ver el contenido de una cinta o un archivo de copia de seguridad (SQL Server)
  En este tema se describe cómo ver el contenido de un archivo o una cinta de copia de seguridad en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  La compatibilidad con dispositivos de cinta de copia de seguridad se quitará en una versión futura de SQL Server. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para ver el contenido de una cinta o un archivo de copia de seguridad, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Security"></a> Seguridad  
 Para obtener más información sobre seguridad, vea [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql).  
  
####  <a name="Permissions"></a> Permisos  
 En [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] y versiones posteriores, la obtención de información sobre un conjunto de copia de seguridad o un dispositivo de copia de seguridad requiere el permiso CREATE DATABASE. Para obtener más información, vea [GRANT &#40;permisos de base de datos de Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a>Para ver el contenido de una cinta o un archivo de copia de seguridad  
  
1.  Tras conectarse a la instancia apropiada de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], en el Explorador de objetos, haga clic en el nombre del servidor para expandir el árbol correspondiente.  
  
2.  Expanda **Bases de datos**y, en función de la base de datos, seleccione la base de datos de un usuario o expanda **Bases de datos del sistema** y seleccione una base de datos del sistema.  
  
3.  Haga clic con el botón derecho en la base de datos de la que quiera hacer una copia de seguridad, seleccione **Tareas**y haga clic en **Copia de seguridad**. Aparece el cuadro de diálogo **Copia de seguridad de base de datos** .  
  
4.  En la sección **Destino** de la página **General** , haga clic en **Disco** o **Cinta**. En el cuadro de lista **Copia de seguridad en** , busque el archivo de disco o la cinta que desea.  
  
     Si el archivo de disco o la cinta no se muestra en el cuadro de lista, haga clic en **Agregar**. Seleccione una unidad de cinta o un nombre de archivo. Para agregarlo al cuadro de lista **Copia de seguridad en** , haga clic en **Aceptar**.  
  
5.  En el cuadro de lista **Copia de seguridad en** , seleccione la ruta de acceso del disco o de la unidad de cinta que quiera ver y haga clic en **Contenido**. De este modo se abre el cuadro de diálogo **Contenido del dispositivo** .  
  
6.  En el panel derecho se muestra información sobre el conjunto de medios y los conjuntos de copia de seguridad de la cinta o del archivo seleccionados.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a>Para ver el contenido de una cinta o un archivo de copia de seguridad  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Use la instrucción [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) . En este ejemplo se devuelve información sobre el archivo denominado `AdventureWorks2012-FullBackup.bak`.  
  
```sql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)   
 [backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql)   
 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql)   
 [backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)   
 [Dispositivos de copia de seguridad &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Definir un dispositivo lógico de copia de seguridad para un archivo de disco &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Definir un dispositivo lógico de copia de seguridad en una unidad de cinta &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
