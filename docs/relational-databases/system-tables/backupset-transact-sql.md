---
title: backupset (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupset
- backupset_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupset system table
- backup media [SQL Server], backupset system table
- backup sets [SQL Server]
ms.assetid: 6ff79bbf-4acf-4f75-926f-38637ca8a943
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b138a299edbb1e9f3a2314e92b7e77418594a711
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119332"
---
# <a name="backupset-transact-sql"></a>backupset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Contiene una fila por cada conjunto de copia de seguridad. Un *conjunto de copia de seguridad* contiene la copia de seguridad de una sola operación de copia de seguridad realizada correctamente. Las instrucciones RESTORE, RESTORE FILELISTONLY, RESTORE HEADERONLY y RESTORE VERIFYONLY actúan sobre un solo conjunto de copia de seguridad en el conjunto de medios de los dispositivos de copia de seguridad especificados.  
  
 Esta tabla se almacena en el **msdb** base de datos.  

  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|Número de identificación único de conjunto de copia de seguridad que identifica al conjunto de copia de seguridad. Clave principal de identidad.|  
|**backup_set_uuid**|**uniqueidentifier**|Número de identificación único de conjunto de copia de seguridad que identifica al conjunto de copia de seguridad.|  
|**media_set_id**|**int**|Número de identificación único de conjunto de medios que identifica el conjunto de medios que contiene el conjunto de copia de seguridad. Referencias **backupmediaset (media_set_id)** .|  
|**first_family_number**|**tinyint**|Número de familia del medio en el que comienza el conjunto de copia de seguridad. Puede ser NULL.|  
|**first_media_number**|**smallint**|Número de medio del medio en el que comienza el conjunto de copia de seguridad. Puede ser NULL.|  
|**last_family_number**|**tinyint**|Número de familia del medio en el que termina el conjunto de copia de seguridad. Puede ser NULL.|  
|**last_media_number**|**smallint**|Número de medio del medio en el que termina el conjunto de copia de seguridad. Puede ser NULL.|  
|**catalog_family_number**|**tinyint**|Número de familia del medio que contiene el comienzo del directorio del conjunto de copia de seguridad. Puede ser NULL.|  
|**catalog_media_number**|**smallint**|Número de medio del medio que contiene el comienzo del directorio del conjunto de copia de seguridad. Puede ser NULL.|  
|**position**|**int**|Posición del conjunto de copia de seguridad utilizada en la operación de restauración para buscar el conjunto de copia de seguridad y los archivos correspondientes. Puede ser NULL. Para obtener más información, consulte el archivo en [copia de seguridad &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**expiration_date**|**datetime**|Fecha y hora de expiración del conjunto de copia de seguridad. Puede ser NULL.|  
|**software_vendor_id**|**int**|Número de identificación del proveedor de software que escribe el encabezado de medios de copia de seguridad. Puede ser NULL.|  
|**name**|**nvarchar(128)**|Nombre del conjunto de copia de seguridad. Puede ser NULL.|  
|**description**|**nvarchar(255)**|Descripción del conjunto de copia de seguridad. Puede ser NULL.|  
|**user_name**|**nvarchar(128)**|Nombre del usuario que realiza la operación de copia de seguridad. Puede ser NULL.|  
|**software_major_version**|**tinyint**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Número de versión principal. Puede ser NULL.|  
|**software_minor_version**|**tinyint**|Número de versión secundaria de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede ser NULL.|  
|**software_build_version**|**smallint**|Número de compilación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede ser NULL.|  
|**time_zone**|**smallint**|Diferencia entre la hora local (en la que tiene lugar la operación de copia de seguridad) y la hora universal coordinada (UTC) en intervalos de 15 minutos. Los valores pueden variar entre -48 y +48, inclusive. El valor 127 indica que se desconoce la diferencia. Por ejemplo, -20 es la hora estándar del Este (EST) o cinco horas después de UTC. Puede ser NULL.|  
|**mtf_minor_version**|**tinyint**|Número de versión secundaria del formato de cinta de [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Puede ser NULL.|  
|**first_lsn**|**numeric(25,0)**|Número de secuencia de registro de la primera entrada de registro del conjunto de copia de seguridad o de la más antigua. Puede ser NULL.|  
|**last_lsn**|**numeric(25,0)**|Número de secuencia de registro de la siguiente entrada del registro después del conjunto de copia de seguridad. Puede ser NULL.|  
|**checkpoint_lsn**|**numeric(25,0)**|Número de secuencia de registro de la entrada del registro en la que debe comenzar la operación de rehacer. Puede ser NULL.|  
|**database_backup_lsn**|**numeric(25,0)**|Número de secuencia de registro de la copia de seguridad completa más reciente de la base de datos. Puede ser NULL.<br /><br /> **database_backup_lsn** es el "inicio del punto de comprobación" que se desencadena cuando se inicia la copia de seguridad. Este LSN coincide con **first_lsn** si se realiza la copia de seguridad cuando la base de datos está inactiva y no está configurada la replicación.|  
|**database_creation_date**|**datetime**|Fecha y hora en que se creó originalmente la base de datos. Puede ser NULL.|  
|**backup_start_date**|**datetime**|Fecha y hora en que comenzó la operación de copia de seguridad. Puede ser NULL.|  
|**backup_finish_date**|**datetime**|Fecha y hora en que terminó la operación de copia de seguridad. Puede ser NULL.|  
|**type**|**char(1)**|Tipo de copia de seguridad. Puede ser:<br /><br /> D = Base de datos<br /><br /> I = Base de datos diferencial<br /><br /> L = Registro<br /><br /> F = Archivo o grupo de archivos<br /><br /> G = Archivo diferencial<br /><br /> P = Parcial<br /><br /> Q = Parcial diferencial<br /><br /> Puede ser NULL.|  
|**sort_order**|**smallint**|Criterio de ordenación del servidor que realiza la operación de copia de seguridad. Puede ser NULL. Para obtener más información acerca de los criterios de ordenación y las intercalaciones, vea [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).|  
|**code_page**|**smallint**|Página de códigos del servidor que realiza la operación de copia de seguridad. Puede ser NULL. Para obtener más información acerca de las páginas de códigos, vea [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).|  
|**compatibility_level**|**tinyint**|Configuración del nivel de compatibilidad para la base de datos. Puede ser:<br /><br /> 90 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> 100 = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<br /><br /> 110 = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /><br /> 120 = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]<br /><br /> Puede ser NULL.<br /><br /> Para obtener más información sobre los niveles de compatibilidad, vea [Nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|  
|**database_version**|**int**|Número de versión de la base de datos. Puede ser NULL.|  
|**backup_size**|**numeric(20,0)**|Tamaño del conjunto de copia de seguridad, en bytes. Puede ser NULL. Copias de seguridad de VSS, backup_size es un valor estimado.|  
|**database_name**|**nvarchar(128)**|Nombre de la base de datos que forma parte de la operación de copia de seguridad. Puede ser NULL.|  
|**server_name**|**nvarchar(128)**|Nombre del servidor en el que se ejecuta la operación de copia de seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede ser NULL.|  
|**nombre_equipo**|**nvarchar(128)**|Nombre del equipo en el que se ejecuta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede ser NULL.|  
|**flags**|**int**|En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **marcas** columna ha quedado desusada y se ha sustituido por las siguientes columnas de bits:<br /><br /> **has_bulk_logged_data** <br /> **is_snapshot** <br /> **is_readonly** <br /> **is_single_user** <br /> **has_backup_checksums** <br /> **is_damaged** <br /> **begins_log_chain** <br /> **has_incomplete_metadata** <br /> **is_force_offline** <br /> **is_copy_only**<br /><br /> Puede ser NULL.<br /><br /> En los conjuntos de copia de seguridad de versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], bits de marca:<br />1 = La copia de seguridad contiene datos registrados al mínimo. <br />2 = Se utilizó WITH SNAPSHOT. <br />4 = La base de datos era de solo lectura en el momento de la copia de seguridad.<br />8 = La base de datos estaba en modo de usuario único en el momento de la copia de seguridad.|  
|**unicode_locale**|**int**|Configuración regional Unicode. Puede ser NULL.|  
|**unicode_compare_style**|**int**|Estilo de comparación en Unicode. Puede ser NULL.|  
|**collation_name**|**nvarchar(128)**|Nombre de intercalación. Puede ser NULL.|  
|**Is_password_protected**|**bit**|Indica si el conjunto de copia de seguridad<br /><br /> está protegido mediante contraseña:<br /><br /> 0 = Sin protección<br /><br /> 1 = Protegido|  
|**recovery_model**|**nvarchar(60)**|Modelo de recuperación de la base de datos:<br /><br /> FULL<br /><br /> BULK-LOGGED<br /><br /> SIMPLE|  
|**has_bulk_logged_data**|**bit**|1 = La copia de seguridad contiene datos de registros de operaciones masivas.|  
|**is_snapshot**|**bit**|1 = La copia de seguridad se realizó con la opción SNAPSHOT.|  
|**is_readonly**|**bit**|1 = La base de datos era de solo lectura en el momento de la copia de seguridad.|  
|**is_single_user**|**bit**|1 = La base de datos estaba en el modo de usuario único en el momento de la copia de seguridad.|  
|**has_backup_checksums**|**bit**|1 = La copia de seguridad contiene sumas de comprobación de copia de seguridad.|  
|**is_damaged**|**bit**|1 = Se detectaron daños en la base de datos al crear esta copia de seguridad. Se solicitó que la copia de seguridad continuara a pesar de los errores.|  
|**begins_log_chain**|**bit**|1 = Es el primer elemento de una cadena continua de copias de seguridad de registros. Una cadena de registro empieza por la primera copia de seguridad de registros realizada después de crear la base de datos o cuando se cambia del modelo de recuperación simple al modelo de recuperación completa o al modelo de recuperación optimizado para cargas masivas de registros.|  
|**has_incomplete_metadata**|**bit**|1 = Copia de seguridad de registros después del error con metadatos incompletos. Para obtener más información, vea [Copias del final del registro &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).|  
|**is_force_offline**|**bit**|1 = La base de datos se dejó sin conexión mediante la opción NORECOVERY cuando se realizó la copia de seguridad.|  
|**is_copy_only**|**bit**|1 = Copia de seguridad de solo copia. Para obtener más información, vea [Copias de seguridad de solo copia &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).|  
|**first_recovery_fork_guid**|**uniqueidentifier**|Id. de la bifurcación de recuperación inicial. Esto corresponde a **FirstRecoveryForkID** de RESTORE HEADERONLY.<br /><br /> Copias de seguridad de datos, **first_recovery_fork_guid** es igual a **last_recovery_fork_guid**.|  
|**last_recovery_fork_guid**|**uniqueidentifier**|Id. de la bifurcación de recuperación final. Esto corresponde a **RecoveryForkID** de RESTORE HEADERONLY.<br /><br /> Copias de seguridad de datos, **first_recovery_fork_guid** es igual a **last_recovery_fork_guid**.|  
|**fork_point_lsn**|**numeric(25,0)**|Si **first_recovery_fork_guid** no es igual a **last_recovery_fork_guid**, este es el número de secuencia de registro del punto de bifurcación. En caso contrario, el valor es NULL.|  
|**database_guid**|**uniqueidentifier**|Id. único de la base de datos. Esto corresponde a **BindingID** de RESTORE HEADERONLY. Cuando se restaura la base de datos, se asigna un valor nuevo.|  
|**family_guid**|**uniqueidentifier**|Id. único de la base de datos original cuando se creó. Este valor permanece invariable cuando se restaura la base de datos, incluso con un nombre diferente.|  
|**differential_base_lsn**|**numeric(25,0)**|LSN de base para copias de seguridad diferenciales. Para una única copia de seguridad diferencial; los cambios con LSN superiores o iguales a **differential_base_lsn** se incluyen en la copia de seguridad diferencial.<br /><br /> Para una diferencial MultiBase, el valor es NULL y la base de LSN debe determinarse en el nivel de archivo (consulte [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)).<br /><br /> Para los tipos de copia de seguridad no diferenciales, el valor siempre es NULL.|  
|**differential_base_guid**|**uniqueidentifier**|Para una copia de seguridad diferencial con una única copia de seguridad base, el valor es el identificador único de la base diferencial.<br /><br /> Para las copias de seguridad diferenciales con varias copias de seguridad base, el valor es NULL y la base diferencial debe determinarse en el nivel de archivo.<br /><br /> Para los tipos de copia de seguridad no diferenciales, el valor es NULL.|  
|**compressed_backup_size**|**Numeric(20,0)**|Recuento total de bytes de la copia de seguridad almacenada en disco.<br /><br /> Para calcular la razón de compresión, utilice **compressed_backup_size** y **backup_size**.<br /><br /> Durante una **msdb** actualización, este valor se establece en NULL. lo que indica que la copia de seguridad no está comprimida.|  
|**key_algorithm**|**nvarchar(32)**|Algoritmo de cifrado usado para cifrar la copia de seguridad. El valor NO_Encryption indica que la copia de seguridad no se cifró.|  
|**encryptor_thumbprint**|**varbinary(20)**|La huella digital del sistema de cifrado que se puede utilizar para encontrar el certificado o la clave asimétrica en la base de datos. Si la copia de seguridad no se cifró, este valor es NULL.|  
|**encryptor_type**|**nvarchar(32)**|Tipo de sistema de cifrado usado: certificado o clave asimétrica. . Si la copia de seguridad no se cifró, este valor es NULL.|  
  
## <a name="remarks"></a>Comentarios  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY rellena la columna de la **backupmediaset** tabla con los valores apropiados del encabezado del conjunto de medios.  
  
 Para reducir el número de filas en esta tabla y de otras tablas de copia de seguridad y el historial, ejecute el [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procedimiento almacenado.  
  
## <a name="see-also"></a>Vea también  
 [Copia de seguridad y restaurar tablas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [Errores posibles de medios durante copia de seguridad y restauración &#40;SQL Server&#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Conjuntos de medios, familias de medios y conjuntos de copias de seguridad &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Modelos de recuperación &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [Copia de seguridad y restaurar tablas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)  
  
  
