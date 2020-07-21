---
title: DAY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a58ac7e29f6a7c41fd0b8e617a04b9a52368fd15
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011373"
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Esta función devuelve un entero que representa el día (del mes) del argumento *date* especificado.
  
Vea [Tipos de datos y funciones de fecha y hora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md) para obtener información general sobre todos los tipos de datos y las funciones de fecha y hora de [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Argumentos  
*date*  
Una expresión que se resuelve en uno de los tipos de datos siguientes:

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

Para *date*, `DAY` aceptará una expresión de columna, una expresión, un literal de cadena o una variable definida por el usuario.
  
## <a name="return-type"></a>Tipo de valor devuelto  
**int**
  
## <a name="return-value"></a>Valor devuelto  
DAY devuelve el mismo valor que [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**day**, *date*).
  
Si *date* contiene solo una parte horaria, `DAY` devolverá 1, el día base.
  
## <a name="examples"></a>Ejemplos  
Esta instrucción devuelve `30`, el número del propio día.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
Esta instrucción devuelve `1900, 1, 1`. El argumento *date* tiene un valor numérico de `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpreta `0` como 1 de enero de 1900.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Consulte también
[CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


