---
title: 'Ejemplo: Restauración por etapas exclusiva para algunos grupos de archivos (modelo de recuperación completa) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 992b010e583a8c40032021f91f26f0a13569b2ee
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583148"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a>Ejemplo: Restauración por etapas exclusiva para algunos grupos de archivos (modelo de recuperación completa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Este tema solo es de interés para las bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que contengan varios archivos o grupos de archivos con el modelo de recuperación completa.  
  
 En una secuencia de restauración por etapas restaura y recupera una base de datos en fases en el nivel del grupo de archivos, empezando con los grupos de archivos principales y todos los secundarios de lectura/escritura.  
  
 En este ejemplo, una base de datos llamada `adb`, que utiliza el modelo de recuperación completa, contiene tres grupos de archivos. El grupo de archivos `A` es de lectura/escritura, mientras que los grupos de archivos `B` y `C` son de solo lectura. Inicialmente, todos los grupos de archivos están en línea.  
  
 Parece que el grupo de archivos principal y el `B` de la base de datos `adb` están dañados. El grupo de archivos principal es bastante más que pequeño y puede restaurarse con rapidez. El administrador de la base de datos decide restaurarlos utilizando una secuencia de restauración por etapas. En primer lugar se restauran el grupo de archivos principal y los registros de transacciones posteriores y luego se recupera la base de datos.  
  
 Los grupos de archivos intactos `A` y `C` incluyen información fundamental. Por lo tanto, se recuperarán a continuación para ponerlos en línea tan pronto como sea posible. Por último, se restaurará y recuperará el grupo de archivos secundario dañado, el `B`.  
  
## <a name="restore-sequences"></a>Secuencias de restauración:  
  
> [!NOTE]  
>  La sintaxis de un flujo de restauración en línea es la misma que la de un flujo de restauración sin conexión.  
  
1.  Cree una copia del final del registro de la base de datos `adb`. Este paso es esencial para actualizar los grupos de archivos `A` y `C` intactos respecto al punto de recuperación de la base de datos.  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  Restauración parcial del grupo de archivos principal.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     En este momento, el grupo principal está en línea. La recuperación de los archivos de los grupos `A`, `B`y `C` está pendiente, por lo que estos grupos de archivo están sin conexión.  
  
3.  Restauración en línea de los grupos de archivos `A` y `C`.  
  
     Dado que estos datos no están dañados, no es preciso restaurar los grupos de archivos a partir de la copia de seguridad. Sin embargo, es necesario recuperarlos para volver a ponerlos en línea.  
  
     El administrador de la base de datos recupera `A` y `C` inmediatamente.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     En este momento, los grupos de archivos principal, `A` y `C` están en línea. Los archivos del grupo `B` permanecen pendientes de recuperación, con el grupo de archivos sin conexión.  
  
4.  Restauración con conexión del grupo de archivos `B`.  
  
     Los archivos del grupo de archivos `B` se restauran en cualquier momento a partir de este momento.  
  
    > [!NOTE]  
    >  La copia de seguridad del grupo de archivos `B` se realizó después de cambiar el grupo a solo lectura, por lo que no es necesario poner al día estos archivos.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     Todos los grupos de archivos están ahora en línea.  
  
## <a name="additional-examples"></a>Otros ejemplos  
  
-   [Ejemplo: restauración por etapas de la base de datos &#40;modelo de recuperación simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Ejemplo: restauración por etapas exclusiva para algunos grupos de archivos &#40;modelo de recuperación simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Ejemplo: restauración con conexión de un archivo de solo lectura &#40;modelo de recuperación simple&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Ejemplo: restauración por etapas de la base de datos &#40;modelo de recuperación completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Ejemplo: restauración con conexión de un archivo de lectura/escritura &#40;modelo de recuperación completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Ejemplo: restauración con conexión de un archivo de solo lectura &#40;modelo de recuperación completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Consulte también  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Restauración con conexión &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Aplicar copias de seguridad del registro de transacciones &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Restauraciones por etapas &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
