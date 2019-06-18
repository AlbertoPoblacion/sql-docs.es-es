---
title: SET ARITHIGNORE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET ARITHIGNORE
- SET_ARITHIGNORE_TSQL
- ARITHIGNORE
- ARITHIGNORE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ARITHIGNORE statement
- overflow errors [SQL Server]
- ARITHIGNORE option
- divide-by-zero errors
ms.assetid: 71b2c2a5-c83a-4dfe-8469-237987a6e503
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ef517e329c651e4d3f21207d1f9e30bcfa0bb9a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639306"
---
# <a name="set-arithignore-transact-sql"></a>SET ARITHIGNORE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Controla si se devuelven mensajes de error al producirse errores de desbordamiento o división por cero durante una consulta.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server and Azure SQL Database

SET ARITHIGNORE { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

SET ARITHIGNORE OFF
```

## <a name="remarks"></a>Notas  
 La opción SET ARITHIGNORE solo controla si se devuelve un mensaje de error. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devuelve NULL en un cálculo en que se invoca un error de desbordamiento o de división por cero con independencia de esta opción. La opción SET ARITHABORT se puede utilizar para determinar si la consulta ha finalizado o no. Esta opción no afecta a los errores producidos al ejecutar las instrucciones INSERT, UPDATE y DELETE.  
  
 Si SET ARITHABORT o SET ARITHIGNORE es OFF y SET ANSI_WARNINGS es ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devolverá un mensaje de error cuando haya errores de división por cero o desbordamiento.  
  
 La opción SET ARITHIGNORE se establece en tiempo de ejecución, no en tiempo de análisis.  
  
 Para ver la configuración actual de este valor, ejecute la consulta siguiente.  
  
```  
DECLARE @ARITHIGNORE VARCHAR(3) = 'OFF';  
IF ( (128 & @@OPTIONS) = 128 ) SET @ARITHIGNORE = 'ON';  
SELECT @ARITHIGNORE AS ARITHIGNORE;  
  
```  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer al rol public.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se muestran las dos opciones de `SET ARITHIGNORE` con ambos tipos de errores de consulta.  
  
```  
SET ARITHABORT OFF;  
SET ANSI_WARNINGS OFF  
GO  
  
PRINT 'Setting ARITHIGNORE ON';  
GO  
-- SET ARITHIGNORE ON and testing.  
SET ARITHIGNORE ON;  
GO  
SELECT 1 / 0 AS DivideByZero;  
GO  
SELECT CAST(256 AS TINYINT) AS Overflow;  
GO  
  
PRINT 'Setting ARITHIGNORE OFF';  
GO  
-- SET ARITHIGNORE OFF and testing.  
SET ARITHIGNORE OFF;  
GO  
SELECT 1 / 0 AS DivideByZero;  
GO  
SELECT CAST(256 AS TINYINT) AS Overflow;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 En el siguiente ejemplo se muestran los errores de división entre cero y de desbordamiento. No se devuelve un mensaje de error relativo a estos errores porque ARITHIGNORE está establecido en OFF.  
  
```  
-- SET ARITHIGNORE OFF and testing.  
SET ARITHIGNORE OFF;  
SELECT 1 / 0 AS DivideByZero;  
SELECT CAST(256 AS TINYINT) AS Overflow;  
  
```  
  
## <a name="see-also"></a>Consulte también  
 [Instrucciones SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-arithabort-transact-sql.md)  
  
  

