---
title: ROWCOUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROWCOUNT_BIG
- ROWCOUNT_BIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROWCOUNT_BIG function
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 6e18a0eb-bb36-4348-90d9-8b1ecf095064
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b40fbc3cca4d396c32b192a7c59a485da70ea8b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el número de filas afectadas por la última instrucción ejecutada. Esta función actúa como [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md), salvo que el tipo de valor devuelto de ROWCOUNT_BIG es **bigint**.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **bigint**  
  
## <a name="remarks"></a>Notas  
 A continuación de una instrucción SELECT, esta función devuelve el número de filas devueltas por la instrucción.  
  
 A continuación de las instrucciones INSERT, UPDATE o DELETE, esta función devuelve el número de filas afectadas por la instrucción de modificación de datos.  
  
 A continuación de las instrucciones que no devuelven filas, como una instrucción IF, esta función devuelve 0.  
  
## <a name="see-also"></a>Ver también  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
