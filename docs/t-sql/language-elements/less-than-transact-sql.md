---
title: '&lt; (No menor que) (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- < (Less Than)
- <_TSQL
- Than
- Less
- <
- Less Than
dev_langs:
- TSQL
helpviewer_keywords:
- less than (<)
- < (less than operator)
ms.assetid: 54f50bdd-bb62-4593-9af9-4c49edecab75
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8c53c2508345e6db7e8fbdb1c02d8ac8a13c5567
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="lt-less-than-transact-sql"></a>&lt; (Menor que) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Compara dos expresiones (es un operador de comparación). Cuando se comparan expresiones no NULL, el resultado es TRUE si el operando de la izquierda tiene un valor menor que el de la derecha; de lo contrario, el resultado es FALSE. Si uno o los dos operandos son NULL, vea el tema [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a>Argumentos  
 *expression*  
 Es cualquier [expresión](../../t-sql/language-elements/expressions-transact-sql.md) válida. Ambas expresiones deben tener tipos de datos que se puedan convertir implícitamente. La conversión depende de las reglas de [prioridad de tipo de datos](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Tipos de resultado  
 **Boolean**  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using--in-a-simple-query"></a>A. Usar < en una consulta simple  
 En el ejemplo siguiente se devuelven todas las filas de la tabla `HumanResources.Department` que tienen un valor en `DepartmentID` que es menor que el valor 3.  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID < 3  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
1            Engineering  
2            Tool Design  
  
(2 row(s) affected)  
  
```  
  
### <a name="b-using--to-compare-two-variables"></a>B. Usar < para comparar dos variables  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a < @b, 'TRUE', 'FALSE' ) AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------  
FALSE  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Ver también  
 [IIF &#40;Transact-SQL&#41;](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Operadores &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
