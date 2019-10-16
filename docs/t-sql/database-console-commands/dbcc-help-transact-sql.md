---
title: DBCC HELP (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC HELP
- DBCC_HELP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC statement syntax information
- DBCC HELP statement
ms.assetid: 306092c6-4354-4e47-928b-606124fbdc6e
author: pmasl
ms.author: umajay
ms.openlocfilehash: eaad7e6f3e66bb39ec43f402c531b7f89bdcf980
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251383"
---
# <a name="dbcc-help-transact-sql"></a>DBCC HELP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

Devuelve información de la sintaxis del comando DBCC especificado.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
DBCC HELP ( 'dbcc_statement' | @dbcc_statement_var | '?' )  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *dbcc_statement* |  *\@dbcc_statement_var*  
 Es el nombre del comando DBCC cuya información de sintaxis se desea recibir. Proporcione únicamente la parte del comando DBCC que sigue a DBCC, por ejemplo CHECKDB en lugar de DBCC CHECKDB.  
  
 ?  
 Devuelve todos los comandos DBCC para los que hay ayuda disponible.  
  
 WITH NO_INFOMSGS  
 Suprime todos los mensajes informativos con niveles de gravedad entre 0 y 10.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
DBCC HELP devuelve un conjunto de resultados que presenta la sintaxis del comando DBCC especificado.
  
## <a name="permissions"></a>Permisos  
Requiere la pertenencia al rol fijo de servidor **sysadmin** .
  
## <a name="examples"></a>Ejemplos  
### <a name="a-using-dbcc-help-with-a-variable"></a>A. Usar DBCC HELP con una variable  
En este ejemplo se devuelve información de sintaxis para DBCC `CHECKDB`.
  
```sql  
DECLARE @dbcc_stmt sysname;  
SET @dbcc_stmt = 'CHECKDB';  
DBCC HELP (@dbcc_stmt);  
GO  
```  
  
### <a name="b-using-dbcc-help-with-the--option"></a>B. Usar DBCC HELP con ? Opción  
En este ejemplo se devuelven todas las instrucciones DBCC para las que hay ayuda disponible.
  
```sql  
DBCC HELP ('?');  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
