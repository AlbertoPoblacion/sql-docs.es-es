---
title: VERSION (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ba4237f9a43a525571a2d25f95acb0a31d4a5cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="version---transact-sql-metadata-functions"></a>Versión - Transact funciones de metadatos de SQL
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 Devuelve la versión de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] en ejecución en el dispositivo.  
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "icono de vínculo de tema") [convenciones de sintaxis de Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Argumentos  
  
## <a name="general-remarks"></a>Notas generales  
Debe especificarse un nombre de tabla en una [FROM](../../t-sql/queries/from-transact-sql.md) cláusula para esta función devolver resultados. Se devolverá una fila de resultados para cada fila del conjunto de resultados de la consulta; usar [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) para limitar el número de filas devueltas.  
  
## <a name="examples"></a>Ejemplos  
En el ejemplo siguiente se devuelve el número de versión.  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Vea también 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
