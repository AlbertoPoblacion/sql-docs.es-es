---
title: sp_helpfilegroup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fe9798b6a9f560621eba9806e25081f72e316c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122542"
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve los nombres y los atributos de los grupos de archivos asociados con la base de datos actual.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @filegroupname = ] 'name'` Es el nombre lógico de cualquier grupo de archivos en la base de datos actual. *nombre* es **sysname**, su valor predeterminado es null. Si *nombre* no se especifica, se enumeran todos los grupos de archivos en la base de datos actual y se muestran solo el primer conjunto de resultados que se muestra en la sección conjuntos de resultados.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (correcto) o 1 (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**groupname**|**sysname**|Nombre del grupo de archivos.|  
|**groupid**|**smallint**|Identificador numérico del grupo de archivos.|  
|**filecount**|**int**|Número de archivos del grupo de archivos.|  
  
 Si *nombre* está especificado, se devuelve una fila para cada archivo en el grupo de archivos.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Nombre lógico del campo en el grupo de archivos.|  
|**fileid**|**smallint**|Identificador numérico del archivo.|  
|**filename**|**nchar(260)**|Nombre físico del archivo, incluida la ruta de acceso del directorio.|  
|**size**|**nvarchar(15)**|Tamaño del archivo en kilobytes.|  
|**maxsize**|**nvarchar(15)**|Tamaño máximo del archivo.<br /><br /> Es el tamaño máximo que puede alcanzar el archivo. El valor UNLIMITED en este campo indica que el archivo puede aumentar hasta que el disco esté lleno.|  
|**growth**|**nvarchar(15)**|Incremento de crecimiento del archivo. Indica la cantidad de espacio que se agrega al archivo cada vez que se necesita espacio.<br /><br /> 0 = El archivo tiene un tamaño fijo y no aumenta.|  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer al rol **public** .  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Devolver todos los grupos de archivos de una base de datos  
 En el siguiente ejemplo se devuelve información sobre los grupos de archivos de la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>b. Devolver todos los archivos de un grupo de archivos  
 En el siguiente ejemplo se devuelve información para todos los archivos del grupo de archivos `PRIMARY` de la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados del motor de base de datos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Archivos y grupos de archivos de base de datos](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
