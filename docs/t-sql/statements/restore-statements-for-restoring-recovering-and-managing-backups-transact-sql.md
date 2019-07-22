---
title: Instrucciones RESTORE para restaurar, recuperar y administrar copias de seguridad (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 62be9d06e64e3ce986da0d96c4d04238d5f9ca3f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082547"
---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>Instrucciones RESTORE para restaurar, recuperar y administrar copias de seguridad (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdbmi-xxxx-xxx-md.md )]

  En esta sección se describen las instrucciones RESTORE relacionadas con las copias de seguridad. Además de la instrucción RESTORE {DATABASE | LOG} principal para restaurar y recuperar copias de seguridad, hay una serie de instrucciones RESTORE auxiliares que le ayudan a administrar las copias de seguridad y a planear las secuencias de restauración. Los comandos RESTORE auxiliares son los siguientes: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY y RESTORE VERIFYONLY.  
  
> [!IMPORTANT]  
>  En versiones anteriores de SQL Server, cualquier usuario podía obtener información sobre los conjuntos de copia de seguridad y los dispositivos de copia de seguridad mediante las instrucciones Transact-SQL RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY y RESTORE VERIFYONLY. Dado que estas instrucciones revelan información sobre el contenido de los archivos de copia de seguridad, en [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] y versiones posteriores requieren el permiso CREATE DATABASE. Este requisito proporciona una protección más completa que en versiones anteriores de los archivos de copia de seguridad y de la información que contienen. Para obtener información sobre este permiso, vea [GRANT &#40;permisos de base de datos de Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="in-this-section"></a>En esta sección  
  
|.|Descripción|  
|---------------|-----------------|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)|Describe las instrucciones Transact-SQL RESTORE DATABASE y RESTORE LOG que se utilizan para restaurar y recuperar una base de datos de copias de seguridad realizadas mediante el comando BACKUP. RESTORE DATABASE se utiliza para bases de datos en todos los modelos de recuperación. RESTORE LOG se utiliza solo en modelos de recuperación completa y modelos de recuperación optimizados para cargas masivas de registros. RESTORE DATABASE también puede utilizarse para revertir una base de datos a una instantánea de base de datos.|  
|[RESTORE &#40;argumentos, Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Documenta los argumentos descritos en las secciones "Sintaxis" de la instrucción RESTORE y del conjunto de instrucciones auxiliares asociado: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY y RESTORE VERIFYONLY. Solo un subconjunto de estas seis instrucciones admite la mayoría de los argumentos. En la descripción del argumento se indica si éste está admitido.|  
|[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|Describe la instrucción Transact-SQL RESTORE FILELISTONLY, que se utiliza para devolver un conjunto de resultados que contiene una lista de los archivos de registro y base de datos contenidos en el conjunto de copia de seguridad.|  
|[RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|Describe la instrucción Transact-SQL RESTORE HEADERONLY, que se utiliza para devolver un conjunto de resultados que contiene toda la información de encabezado de copia de seguridad para todos los conjuntos de copia de seguridad en un dispositivo de copia de seguridad determinado.|  
|[RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|Describe la instrucción Transact-SQL RESTORE LABELONLY, que se utiliza para devolver un conjunto de resultados que contiene información sobre el medio de copia de seguridad identificado por el dispositivo de copia de seguridad dado.|  
|[RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|Describe la instrucción Transact-SQL RESTORE REWINDONLY, que se utiliza para rebobinar y cerrar dispositivos de cinta que se quedaron abiertos al ejecutar las instrucciones BACKUP o RESTORE con la opción NOREWIND.|  
|[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|Describe la instrucción Transact-SQL RESTORE VERIFYONLY, que se utiliza para comprobar la copia de seguridad, sin restaurarla, y comprueba que el conjunto de copia de seguridad esté completo y se pueda leer, aunque no intenta comprobar la estructura de los datos.|  
  
## <a name="see-also"></a>Consulte también  
 [Realizar copias de seguridad y restaurar bases de datos de SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
