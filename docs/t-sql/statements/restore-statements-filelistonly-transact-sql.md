---
title: RESTORE FILELISTONLY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE FILELISTONLY
- RESTORE_FILELISTONLY_TSQL
- FILELISTONLY
- FILELISTONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backups [SQL Server], file lists
- RESTORE FILELISTONLY statement
- listing backed up files
ms.assetid: 0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6776115033e6e7222abc610673dd8b0aaff81dc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---filelistonly-transact-sql"></a>Instrucciones RESTORE: FILELISTONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve un conjunto de resultados que contiene una lista con los archivos de base de datos y de registro del conjunto de copia de seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Para obtener las descripciones de los argumentos, vea [Argumentos de RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RESTORE FILELISTONLY   
FROM <backup_device>   
[ WITH   
 {  
--Backup Set Options  
   FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>Argumentos  
 Para obtener las descripciones de los argumentos de RESTORE FILELISTONLY, vea [Argumentos de RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Un cliente puede utilizar RESTORE FILELISTONLY para obtener una lista de los archivos que contiene el conjunto de copia de seguridad. Esta información se devuelve como conjunto de resultados que contiene una fila por cada archivo.  
  
|Nombre de columna|Tipo de datos|Description|  
|-|-|-|  
|LogicalName|**nvarchar(128)**|Nombre lógico del archivo.|  
|PhysicalName|**nvarchar(260)**|Nombre físico o del sistema operativo del archivo.|  
|Tipo|**char(1)**|Uno de los tipos de archivo:<br /><br /> **L** = archivo de registro de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> **D** = archivo de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> **F** = catálogo de texto completo<br /><br /> **S** = FileStream, FileTable o contenedor [!INCLUDE[hek_2](../../includes/hek-2-md.md)]|  
|FileGroupName|**nvarchar(128)**|Nombre del grupo de archivos que contiene el archivo.|  
|Tamaño|**numeric(20,0)**|Tamaño actual, en bytes.|  
|MaxSize|**numeric(20,0)**|Tamaño máximo permitido, en bytes.|  
|FileID|**bigint**|Identificador de archivo, único en la base de datos.|  
|CreateLSN|**numeric(25,0)**|Número de secuencia de registro en el que se creó el archivo.|  
|DropLSN|**numeric(25,0)** NULL|Número de secuencia de registro en que se quitó el archivo. Si el archivo no se ha quitado, este valor es NULL.|  
|UniqueID|**uniqueidentifier**|Identificador único global del archivo.|  
|ReadOnlyLSN|**numeric(25,0) NULL**|Número de flujo de registro en el que el grupo de archivos que contiene el archivo cambió de lectura/escritura a solo lectura (el cambio más reciente).|  
|ReadWriteLSN|**numeric(25,0)** NULL|Número de secuencia de registro en el que el grupo de archivos que contiene el archivo cambió de solo lectura a lectura/escritura (el cambio más reciente).|  
|BackupSizeInBytes|**bigint**|Tamaño en bytes de la copia de seguridad de este archivo.|  
|SourceBlockSize|**int**|Tamaño de bloque (en bytes) del dispositivo físico que contiene el archivo (no el dispositivo de copia de seguridad).|  
|FileGroupID|**int**|Id. del grupo de archivos.|  
|LogGroupGUID|**uniqueidentifier NULL**|NULL.|  
|DifferentialBaseLSN|**numeric(25,0)** NULL|En el caso de las copias de seguridad diferenciales, los cambios cuyo número de secuencia de registro sea mayor o igual que **DifferentialBaseLSN** se incluyen en la copia diferencial.<br /><br /> Para otros tipos de copia de seguridad, el valor es NULL.|  
|DifferentialBaseGUID|**uniqueidentifier**|Identificador único de la base diferencial, en el caso de las copias de seguridad diferenciales.<br /><br /> Para otros tipos de copia de seguridad, el valor es NULL.|  
|IsReadOnly|**bit**|**1** = El archivo es de solo lectura.|  
|IsPresent|**bit**|**1** = El archivo se encuentra en la copia de seguridad.|  
|TDEThumbprint|**varbinary(32)**|Muestra la huella digital de la clave de cifrado de base de datos. La huella digital de la clave de cifrado es el valor hash SHA-1 del certificado con el que se cifra la clave. Para más información sobre el cifrado de bases de datos, vea [Cifrado de datos transparente &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).|  
|SnapshotURL|**nvarchar(360)**|Dirección URL de la instantánea de Azure del archivo de base de datos incluido en la copia de seguridad de FILE_SNAPSHOT. Devuelve NULL si no hay ninguna copia de seguridad de FILE_SNAPSHOT.|  
  
## <a name="security"></a>Seguridad  
 La operación de copia de seguridad puede especificar opcionalmente contraseñas de un conjunto de medios, de un conjunto de copia de seguridad o de ambos. Si se ha definido una contraseña en un conjunto de medios o un conjunto de copia de seguridad, debe especificar la contraseña o contraseñas correctas en la instrucción RESTORE. Estas contraseñas impiden operaciones de restauración y anexiones no autorizadas de los conjuntos de copia de seguridad en medios que usan herramientas de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. No obstante, la contraseña no impide que se sobrescriba el medio con la opción FORMAT de la instrucción BACKUP.  
  
> [!IMPORTANT]  
>  El nivel de protección que proporciona esta contraseña es bajo. El objetivo es impedir una restauración incorrecta con las herramientas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ya sea por parte de usuarios autorizados o no autorizados. No impide la lectura de los datos de las copias de seguridad por otros medios o el reemplazo de la contraseña. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] La práctica recomendada para proteger las copias de seguridad consiste en almacenar las cintas de copia de seguridad en una ubicación segura o hacer una copia de seguridad en archivos de disco protegidos mediante las listas de control de acceso (ACL) adecuadas. Las ACL se deben establecer en el directorio raíz en el que se crean las copias de seguridad.  
  
### <a name="permissions"></a>Permisos  
 A partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], para obtener información sobre un conjunto de copia de seguridad o un dispositivo de copia de seguridad, es necesario el permiso CREATE DATABASE. Para obtener más información, vea [GRANT &#40;permisos de base de datos de Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve la información de un dispositivo de copia de seguridad denominado `AdventureWorksBackups`. El ejemplo utiliza la opción `FILE` para especificar el segundo conjunto de copias de seguridad del dispositivo.  
  
```  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a>Ver también  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Conjuntos de medios, familias de medios y conjuntos de copias de seguridad &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Historial de copias de seguridad e información de encabezados &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
