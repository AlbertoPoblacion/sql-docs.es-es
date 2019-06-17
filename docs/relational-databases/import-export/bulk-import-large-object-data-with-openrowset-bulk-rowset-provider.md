---
title: Importar de forma masiva datos de objetos de gran tamaño mediante el proveedor de conjuntos de filas BULK OPENROWSET | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 38cf74c8ad6542eeafc9f6f785f8bc9f0eecea99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "64946416"
---
# <a name="bulk-import-large-object-data-with-openrowset-bulk-rowset-provider"></a>Importar de forma masiva datos de objetos de gran tamaño mediante el proveedor de conjuntos de filas BULK OPENROWSET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  El proveedor de conjuntos de filas BULK OPENROWSET de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permite realizar la importación masiva de un archivo de datos como datos de objetos grandes.  
  
 Los tipos de datos de objetos grandes admitidos por el proveedor de conjuntos de filas BULK OPENROWSET son: **varbinary**(max) o **image**, **varchar**(max) o **text**, y **nvarchar**(max) o **ntext**.  
  
> [!NOTE]  
>  Los tipos de datos **image**, **text** y **ntext** han quedado en desuso.  
  
 La cláusula BULK de OPENROWSET admite tres opciones para importar el contenido de un archivo de datos como un conjunto de filas de fila única y columna única. Puede especificar una de estas opciones de objetos grandes en lugar de usar un archivo de formato. Las opciones son las siguientes:  
  
 SINGLE_BLOB  
 Lee el contenido de *data_file* como un archivo de una sola fila y devuelve el contenido como un conjunto de filas de una sola columna del tipo **varbinary(max)** .  
  
 SINGLE_CLOB  
 Lee el contenido del archivo de datos especificado como caracteres y devuelve el contenido como un conjunto de filas de una sola fila y una sola columna del tipo **varchar(max)** , mediante la intercalación de la base de datos actual, como un documento de texto o de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word.  
  
 SINGLE_NCLOB  
 Lee el contenido del archivo de datos especificado como Unicode y devuelve el contenido como un conjunto de filas de una sola fila y una sola columna del tipo **nvarchar(max)** , mediante la intercalación de la base de datos actual.  
  
## <a name="see-also"></a>Consulte también  
 [Importación en bloque de datos mediante las instrucciones BULK INSERT u OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Mantener valores NULL o usar valores predeterminados durante la importación en bloque &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [bcp (utilidad)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  
