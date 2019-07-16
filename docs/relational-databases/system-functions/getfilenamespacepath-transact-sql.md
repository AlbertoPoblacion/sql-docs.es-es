---
title: GetFileNamespacePath (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- GetFileNamespacePath
- GetFileNamespacePath_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetFileNamespacePath function
ms.assetid: b393ecef-baa8-4d05-a268-b2f309fce89a
author: rothja
ms.author: jroth
ms.openlocfilehash: ab369b619bc0ad378292cf71573ab973dc056c2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101429"
---
# <a name="getfilenamespacepath-transact-sql"></a>GetFileNamespacePath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve la ruta de acceso UNC para un archivo o directorio de un objeto FileTable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<column-name>.GetFileNamespacePath(is_full_path, @option)  
```  
  
## <a name="arguments"></a>Argumentos  
 *column-name*  
 El nombre de columna de la varbinary (max) **file_stream** columna de una FileTable.  
  
 El *nombre de columna* valor debe ser un nombre de columna válido. No puede ser una expresión ni un valor convertido de una columna de otro tipo de datos.  
  
 *is_full_path*  
 Expresión entera que especifica si se devuelve una ruta de acceso absoluta o relativa. *is_full_path* puede tener uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**0**|Devuelve la ruta de acceso relativa al directorio de base de datos.<br /><br /> Este es el valor predeterminado|  
|**1**|Devuelve la ruta de acceso UNC completa, empezando por `\\computer_name`.|  
  
 *@option*  
 Expresión entera que define cómo se debe dar formato al componente de servidor de la ruta de acceso. *@option* Puede tener uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**0**|Devuelve el nombre del servidor convertido a formato NetBIOS, por ejemplo:<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDatabase`<br /><br /> Este es el valor predeterminado.|  
|**1**|Devuelve el nombre del servidor sin la conversión, por ejemplo:<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDatabase`|  
|**2**|Devuelve la ruta de acceso al servidor completa, por ejemplo:<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDatabase`|  
  
## <a name="return-type"></a>Tipo devuelto  
 **nvarchar(max)**  
  
 Si la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está en clúster en un clúster de conmutación por error, el nombre de la máquina que se devuelve como parte de esta ruta de acceso es el nombre del host virtual de la instancia en clúster.  
  
 Cuando la base de datos pertenece a un grupo de disponibilidad Always On, el **FileTableRootPath** función devuelve el nombre de red virtual (VNN) en lugar del nombre de equipo.  
  
## <a name="general-remarks"></a>Notas generales  
 La ruta de acceso que el **GetFileNamespacePath** función devuelve es una ruta de directorio o archivo lógica en el formato siguiente:  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\...`  
  
 Esta ruta de acceso lógica no se corresponden directamente con una ruta de acceso física de NTFS. Controlador de filtro de sistema de archivos de FILESTREAM y el agente FILESTREAM se traduce a la ruta de acceso física. Esta separación entre la ruta de acceso lógica y la ruta de acceso física permite a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reorganizar internamente los datos sin afectar a la validez de la ruta de acceso.  
  
## <a name="best-practices"></a>Procedimientos recomendados  
 Para mantener independientes del equipo y de la base de datos actuales el código y las aplicaciones, evite escribir código basado en rutas de acceso absolutas de archivos. En su lugar, obtenga la ruta de acceso completa para un archivo en tiempo de ejecución mediante la **FileTableRootPath** y **GetFileNamespacePath** funciones entre sí, tal como se muestra en el ejemplo siguiente. De forma predeterminada, la función **GetFileNamespacePath** devuelve la ruta de acceso relativa del archivo en la ruta de acceso raíz de la base de datos.  
  
```sql  
USE MyDocumentDatabase;  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
  
@fullPath = varchar(1000);  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath() FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="examples"></a>Ejemplos  
 Los ejemplos siguientes muestran cómo llamar a la **GetFileNamespacePath** función para obtener la ruta de acceso UNC de un archivo o directorio en un FileTable.  
  
```  
-- returns the relative path of the form "\MyFileTable\MyDocDirectory\document.docx"  
SELECT file_stream.GetFileNamespacePath() AS FilePath FROM DocumentStore  
WHERE Name = N'document.docx';  
  
-- returns "\\MyServer\MSSQLSERVER\MyDocumentDatabase\MyFileTable\MyDocDirectory\document.docx"  
SELECT file_stream.GetFileNamespacePath(1, Null) AS FilePath FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con directorios y rutas de acceso de FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
