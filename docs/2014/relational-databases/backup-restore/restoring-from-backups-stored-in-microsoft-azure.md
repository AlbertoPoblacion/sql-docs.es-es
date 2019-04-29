---
title: Restaurar a partir de copias de seguridad almacenadas en Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6ae358b2-6f6f-46e0-a7c8-f9ac6ce79a0e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 549efcd796d9cef721995b48fc5e7b3cc02403a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920643"
---
# <a name="restoring-from-backups-stored-in-windows-azure"></a>La restauración de las copias de seguridad archivadas en Microsoft Azure
  Este tema describe las consideraciones al restaurar una base de datos mediante una copia de seguridad almacenada en el servicio de almacenamiento Blob de Windows Azure. Esto se aplica a las copias de seguridad creadas mediante Copia de seguridad en URL de SQL Server o con [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Se recomienda revisar este tema si tiene copias de seguridad almacenadas en el servicio de almacenamiento Blob de Windows Azure que vaya a restaurar y luego revisar los temas que describen los pasos para restaurar una base de datos, que es igual para las copias de seguridad locales y de Windows Azure.  
  
## <a name="overview"></a>Información general  
 Las herramientas y los métodos que se utilizan para restaurar una base de datos a partir de una copia de seguridad local son válidos para restaurar una base de datos a partir de una copia de seguridad en la nube.  En las siguientes secciones se describen estas consideraciones y las diferencias que debe saber si utiliza las copias de seguridad almacenadas en el servicio de almacenamiento Blob de Windows Azure.  
  
### <a name="using-transact-sql"></a>Usar Transact-SQL  
  
-   Dado que SQL Server debe conectarse a un origen externo para recuperar los archivos de copia de seguridad, la credencial de SQL se utiliza para autenticarse en la cuenta de almacenamiento. Por consiguiente, la instrucción RESTORE requiere la opción WITH CREDENTIAL. Para más información, consulte [Copia de seguridad y restauración de SQL Server con el servicio Azure Blob Storage](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
-   Si usa [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] para administrar las copias de seguridad en la nube, podrá revisar todas las copias de seguridad disponibles en el almacén mediante la función del sistema **smart_admin.fn_available_backups** . Esta función del sistema devuelve todas las copias de seguridad disponibles para una base de datos en una tabla. Como los resultados se devuelven en una tabla, puede filtrarlos u ordenarlos. Para obtener más información, consulte [smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).  
  
### <a name="using-sql-server-management-studio"></a>Usar SQL Server Management Studio  
  
-   Se utiliza la tarea de restauración para restaurar una base de datos con SQL Server Management Studio. La página de medios de copia de seguridad incluye ahora la opción **Dirección URL** para mostrar los archivos de copia de seguridad almacenados en el servicio de almacenamiento Blob de Windows Azure. También debe proporcionar la credencial SQL que se usa para autenticarse en la cuenta de almacenamiento. La cuadrícula **Conjuntos de copia de seguridad para restaurar** se rellena con las copias de seguridad disponibles en el almacenamiento Blob de Windows Azure. Para más información, consulte [Restoring from Windows Azure storage Using SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS).  
  
### <a name="optimizing-restores"></a>Optimizar restauraciones  
 Para reducir el tiempo de escritura de restauración, agregue el derecho de usuario **Realizar tareas de mantenimiento del volumen** a la cuenta de usuario de SQL Server. Para obtener más información, vea [Inicialización de archivos de base de datos](https://go.microsoft.com/fwlink/?LinkId=271622). Si la restauración sigue siendo lenta con la inicialización de archivos instantánea activada, examine el tamaño del archivo de registro en la instancia donde se hizo copia de seguridad de la base de datos. Si el registro es muy grande (varios GB), cabe esperar que la restauración sea lenta. Durante la restauración, el archivo de registro se debe poner a cero, lo que lleva una cantidad considerable de tiempo.  
  
 Para reducir los tiempos de restauración, se recomienda usar copias de seguridad comprimidas.  Para los tamaños de copia de seguridad que sobrepasen los 25 GB, use la [utilidad AzCopy](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx) para realizar la descarga en la unidad local y, después, realizar la restauración. Para obtener información sobre otros procedimientos recomendados y sugerencias para copias de seguridad, vea [SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md).  
  
 También puede activar la marca de seguimiento 3051 al realizar la restauración para generar un registro detallado. Este archivo de registro se coloca en el directorio de registro y se denomina con el formato: BackupToUrl-\<instancename>-\<dbname>-action-\<PID>.log. El archivo de registro incluye información sobre cada acción de ida y vuelta al Almacenamiento de Windows Azure, incluido el tiempo que puede resultar útil para diagnosticar el problema.  
  
### <a name="topics-on-performing-restore-operations"></a>Temas sobre las operaciones de restauración  
  
-   [Restauraciones de base de datos completas &#40;modelo de recuperación simple&#41;](complete-database-restores-simple-recovery-model.md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [Restauraciones de base de datos completas &#40;modelo de recuperación completa&#41;](complete-database-restores-full-recovery-model.md)  
  
-   [Restauraciones de archivos &#40;modelo de recuperación simple&#41;](file-restores-simple-recovery-model.md)  
  
-   [Restauraciones de archivos &#40;modelo de recuperación completa&#41;](file-restores-full-recovery-model.md)  
  
-   [Restauraciones por etapas &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
