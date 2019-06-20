---
title: Prácticas recomendadas y solución de problemas de Copia de seguridad en URL de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7f652d512f27b935b158a71a80b61c43ac6b7183
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65619587"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>Prácticas recomendadas y solución de problemas de Copia de seguridad en URL de SQL Server
  Este tema incluye prácticas recomendadas y sugerencias para la solución de problemas de copias de seguridad y restauraciones de SQL Server en el servicio Blob de Windows Azure.  
  
 Para obtener más información sobre cómo usar el servicio de almacenamiento Blob de Windows Azure para realizar operaciones de copia de seguridad o restauración de SQL Server, vea:  
  
-   [Copia de seguridad y restauración de SQL Server con el servicio Windows Azure Blob Storage](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [Tutorial: copias de seguridad y restauración de SQL Server en el servicio Microsoft Azure Blob Storage](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>Administrar copias de seguridad  
 La lista siguiente incluye recomendaciones generales para administrar copias de seguridad:  
  
-   Se recomienda usar un nombre de archivo único para cada copia de seguridad con el fin de evitar que se sobrescriban accidentalmente los blobs.  
  
-   Al crear un contenedor, se recomienda establecer el nivel de acceso en **privado**, de forma que solo los usuarios o las cuentas que puedan proporcionar la información de autenticación necesaria sean capaces de leer o escribir los blobs en el contenedor.  
  
-   En el caso de bases de datos de SQL Server en una instancia de SQL Server que se ejecuta en una máquina virtual de Windows Azure, use una cuenta de almacenamiento de la misma región que la máquina virtual para evitar costos de transferencia de datos entre las regiones. El uso de la misma región también garantiza un rendimiento óptimo para las operaciones de copia de seguridad y restauración.  
  
-   Una actividad de copia de seguridad con errores puede dar como resultado un archivo de copia de seguridad no válido. Se recomienda identificar periódicamente las copias de seguridad con errores y eliminar los archivos blob. Para obtener más información, consulte [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md).  
  
-   El uso de la opción `WITH COMPRESSION` durante la copia de seguridad puede reducir al mínimo los costos de almacenamiento y los costos de transacciones de almacenamiento. También puede reducir el tiempo necesario para completar el proceso de copia de seguridad.  
  
## <a name="handling-large-files"></a>Controlar archivos grandes  
  
-   La operación de copia de seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emplea varios subprocesos para optimizar la transferencia de datos a los servicios de almacenamiento Blob de Windows Azure.  Sin embargo, el rendimiento depende en varios factores, como el ancho de banda del ISV y el tamaño de la base de datos. Si piensa hacer copia de seguridad de bases de datos o grupos de archivos grandes desde una base de datos de SQL Server local, se recomienda que realice primero algunas pruebas de rendimiento. [Del almacenamiento de Windows Azure SLA](https://go.microsoft.com/fwlink/?LinkId=271619) tienen tiempos máximos de procesamiento para los blobs que puede tener en cuenta.  
  
-   Use la opción `WITH COMPRESSION` como se recomienda en la sección **Administrar copias de seguridad**, ya que es muy importante al realizar la copia de seguridad de archivos grandes.  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>Resolución de problemas para realizar la copia de seguridad de una dirección URL o una restauración a partir de esta  
 A continuación se indican algunas formas rápidas de solucionar errores al hacer copia de seguridad o restaurar desde el servicio de almacenamiento Blob de Windows Azure.  
  
 Para evitar errores debidos a opciones no admitidas o limitaciones, consulte la lista de limitaciones y copia de seguridad y restaurar información de comandos de compatibilidad con la [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) artículo.  
  
 **Errores de autenticación:**  
  
-   WITH CREDENTIAL es una opción nueva que es necesaria para la copia de seguridad o la restauración con el servicio de almacenamiento Blob de Windows Azure. He aquí algunos errores relacionados con las credenciales:  
  
     La credencial especificada en el comando `BACKUP` o `RESTORE` no existe. Para evitar este problema, puede incluir instrucciones T-SQL para crear la credencial si no existe ninguna en la instrucción de copia de seguridad. He aquí un ejemplo que puede usar:  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   La credencial existe pero la cuenta de inicio de sesión usada para ejecutar el comando de copia de seguridad no tiene permisos de acceso a las credenciales. Use una cuenta de inicio de sesión en el rol **db_backupoperator** con permisos para **Modificar cualquier credencial** .  
  
-   Compruebe los valores de clave y nombre de la cuenta de almacenamiento. La información almacenada en la credencial debe coincidir con los valores de propiedad de la cuenta de almacenamiento de Windows Azure que se usa en las operaciones de copia de seguridad y restauración.  
  
 **Errores de copia de seguridad:**  
  
-   Las copias de seguridad en paralelo en el mismo blob produce errores en una de las copias de seguridad y hacen que aparezca un **Error de inicialización** .  
  
-   Use los registros de errores siguientes como ayuda para solucionar problemas de copia de seguridad:  
  
    -   Establezca la marca de seguimiento 3051 para activar el registro en un registro de errores específico con el siguiente formato en:  
  
         BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log, donde \<action> es uno de los siguientes elementos:  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   También puede encontrar información si examina el registro de eventos Windows - registros en la aplicación con el nombre 'SQLBackupToUrl'.  
  
-   Al restaurar desde una copia de seguridad comprimida, puede aparecer el siguiente error:  
  
    -   **SqlException 3284. Gravedad: 16 estado: 5**  
        **Marca de archivo del mensaje en el dispositivo 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak ' no está alineada. Vuelva a emitir la instrucción Restore con el mismo tamaño de bloque usado para crear el backupset: '65536' parece un valor posible.**  
  
         Para resolver este error, vuelva a emitir la instrucción `BACKUP` especificando `BLOCKSIZE = 65536`.  
  
-   Error durante la copia de seguridad porque los blobs tienen una concesión activa: una actividad de copia de seguridad con errores puede dar como resultado blobs con concesiones activas.  
  
     Si se vuelve a intentar una instrucción de copia de seguridad, la operación de copia de seguridad puede producir un error similar al siguiente:  
  
     **BACKUP TO URL recibió una excepción del extremo remoto. Mensaje de excepción: El servidor remoto devolvió un error: (412) actualmente hay una concesión en el blob y se especificó ningún identificador de concesión en la solicitud**.  
  
     Si se intenta una instrucción de restauración en un archivo de blob de copia de seguridad que tiene una concesión activa, la operación de restauración produce un error similar al siguiente:  
  
     **Mensaje de excepción: El servidor remoto devolvió un error: (409) conflicto...**  
  
     Cuando se produce ese error, es necesario eliminar los archivos de blob. Para obtener más información sobre este escenario y cómo corregir este problema, vea [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md).  
  
## <a name="proxy-errors"></a>Errores de proxy  
 Si usa servidores proxy para tener acceso a Internet, pueden producirse los problemas siguientes:  
  
 **Limitación de la conexión por parte de los servidores proxy:**  
  
 Los servidores proxy pueden tener configuraciones que limitan el número de conexiones por minuto. Copia de seguridad en URL es un proceso multiproceso y, por tanto, puede sobrepasar este límite. Si esto ocurre, el servidor proxy elimina la conexión. Para resolver este problema, cambie la configuración de proxy para que SQL Server no utilice el proxy.   A continuación se muestran algunos ejemplos de los tipos o mensajes de error que puede ver en el registro de errores:  
  
-   Escribir en "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak " Error: BACKUP TO URL recibió una excepción del extremo remoto. Mensaje de excepción: No se puede leer datos de la conexión de transporte: Se cerró la conexión.  
  
-   Error de E/S irrecuperable en el archivo "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: ". No se pudo recopilar el error del punto de conexión remoto.  
  
     Mensaje 3013, nivel 16, estado 1, línea 2  
  
     Fin anómalo de BACKUP DATABASE.  
  
-   Backupiorequest:: Reportioerror: error de escritura en el dispositivo de copia de seguridad 'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak '. Error de sistema operativo Copia de seguridad en URL recibió una excepción del extremo remoto. Mensaje de excepción: No se puede leer datos de la conexión de transporte: Se cerró la conexión.  
  
 Si activa el registro detallado mediante la marca de seguimiento 3051, puede ver también el mensaje siguiente en los registros:  
  
 Código de estado HTTP 502, error de proxy del mensaje de estado HTTP (El número de peticiones HTTP por minuto superó el límite configurado. Póngase en contacto con el administrador del servidor ISA.  )  
  
 **Configuración de proxy predeterminada no seleccionada:**  
  
 A veces, la configuración predeterminada no se selecciona, lo que produce errores de autenticación del proxy como el que se muestra a continuación: *Error de E/S irrecuperable en el archivo "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: ". La copia de seguridad en URL recibió una excepción del punto de conexión remoto. Mensaje de excepción: El servidor remoto devolvió un error: (407)*  **Requerida autenticación del proxy**.  
  
 Para resolver este problema, cree un archivo de configuración que permita al proceso Copia de seguridad en URL utilizar la configuración de proxy predeterminada mediante los pasos siguientes:  
  
1.  Cree un archivo de configuración denominado BackuptoURL.exe.config con el código XML siguiente:  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  Coloque el archivo de configuración en la carpeta Binn de la instancia de SQL Server. Por ejemplo, si SQL Server está instalado en la unidad C de la máquina, coloque el archivo de configuración aquí: *C:\Program Files\Microsoft SQL Server\MSSQL12. \<InstanceName > \MSSQL\Binn*.  
  
## <a name="troubleshooting-sql-server-managed-backup-to-windows-azure"></a>Solucionar problemas de la Copia de seguridad administrada de SQL Server para Microsoft Azure  
 Puesto que Copia de seguridad administrada de SQL Server se basa en Copia de seguridad en URL, las sugerencias para la solución de problemas que se han descrito en las secciones anteriores son aplicables también a las bases de datos o las instancias que utilizan Copia de seguridad administrada de SQL Server.  Información sobre cómo solucionar problemas de SQL Server Managed Backup to Windows Azure se describe detalladamente en [solución de problemas de SQL Server Managed Backup to Windows Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="see-also"></a>Vea también  
 [Restauración de las copias de seguridad archivadas en Microsoft Azure](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
