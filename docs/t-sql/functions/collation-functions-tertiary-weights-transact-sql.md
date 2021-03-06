---
title: TERTIARY_WEIGHTS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TERTIARY_WEIGHTS_TSQL
- TERTIARY_WEIGHTS
dev_langs:
- TSQL
helpviewer_keywords:
- weights [SQL Server]
- SQL tertiary collations
- TERTIARY_WEIGHTS function
ms.assetid: 7e1f5350-260b-4c61-8c84-69bb1a214f1f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5edddaffd94337a1538ed00085216145f9389670
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="collation-functions---tertiaryweights-transact-sql"></a>Funciones de intercalación: TERTIARY_WEIGHTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Devuelve una cadena binaria de pesos para cada carácter en una expresión de cadena no Unicode definida con una intercalación terciaria de SQL.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
TERTIARY_WEIGHTS( non_Unicode_character_string_expression )  
```  
  
## <a name="arguments"></a>Argumentos  
*non_Unicode_character_string_expression*  
Es una [expresión](../../t-sql/language-elements/expressions-transact-sql.md) de cadena de tipo **char**, **varchar** o **varchar(max)** definida en una intercalación SQL terciaria. Para obtener una lista de estas intercalaciones, vea la sección Notas.
  
## <a name="return-types"></a>Tipos de valores devueltos
TERTIARY_WEIGHTS devuelve **varbinary** cuando *non_Unicode_character_string_expression* es **char** o **varchar**, y devuelve **varbinary(max)** cuando *non_Unicode_character_string_expression* es **varchar(max)**.
  
## <a name="remarks"></a>Notas  
TERTIARY_WEIGHTS devuelve NULL cuando el parámetro *non_Unicode_character_string_expression* no está definido con una intercalación terciaria de SQL. En la tabla siguiente se muestran las intercalaciones terciarias de SQL.
  
|Id. de orden|Intercalación de SQL|  
|---|---|
|33|SQL_Latin1_General_Pref_CP437_CI_AS|  
|34|SQL_Latin1_General_CP437_CI_AI|  
|43|SQL_Latin1_General_Pref_CP850_CI_AS|  
|44|SQL_Latin1_General_CP850_CI_AI|  
|49|SQL_1xCompat_CP850_CI_AS|  
|53|SQL_Latin1_General_Pref_CP1_CI_AS|  
|54|SQL_Latin1_General_CP1_CI_AI|  
|56|SQL_AltDiction_Pref_CP850_CI_AS|  
|57|SQL_AltDiction_CP850_CI_AI|  
|58|SQL_Scandinavian_Pref_CP850_CI_AS|  
|82|SQL_Latin1_General_CP1250_CI_AS|  
|84|SQL_Czech_CP1250_CI_AS|  
|86|SQL_Hungarian_CP1250_CI_AS|  
|88|SQL_Polish_CP1250_CI_AS|  
|90|SQL_Romanian_CP1250_CI_AS|  
|92|SQL_Croatian_CP1250_CI_AS|  
|94|SQL_Slovak_CP1250_CI_AS|  
|96|SQL_Slovenian_CP1250_CI_AS|  
|106|SQL_Latin1_General_CP1251_CI_AS|  
|108|SQL_Ukrainian_CP1251_CI_AS|  
|113|SQL_Latin1_General_CP1253_CS_AS|  
|114|SQL_Latin1_General_CP1253_CI_AS|  
|130|SQL_Latin1_General_CP1254_CI_AS|  
|146|SQL_Latin1_General_CP1256_CI_AS|  
|154|SQL_Latin1_General_CP1257_CI_AS|  
|156|SQL_Estonian_CP1257_CI_AS|  
|158|SQL_Latvian_CP1257_CI_AS|  
|160|SQL_Lithuanian_CP1257_CI_AS|  
|183|SQL_Danish_Pref_CP1_CI_AS|  
|184|SQL_SwedishPhone_Pref_CP1_CI_AS|  
|185|SQL_SwedishStd_Pref_CP1_CI_AS|  
|186|SQL_Icelandic_Pref_CP1_CI_AS|  
  
La función TERTIARY_WEIGHTS está pensada para su uso en la definición de una columna calculada que se define en los valores de una columna **char**, **varchar** o **varchar(max)**. Definir un índice tanto en la columna calculada como en la columna **char**, **varchar** o **varchar(max)** puede mejorar el rendimiento cuando se especifica la columna **char**, **varchar** o **varchar(max)** en la cláusula ORDER BY de una consulta.
  
## <a name="examples"></a>Ejemplos  
El siguiente ejemplo crea una columna calculada en una tabla que aplica la función `TERTIARY_WEIGHTS` a los valores de una columna `char`.
  
```sql
CREATE TABLE TertColTable  
(Col1 char(15) COLLATE SQL_Latin1_General_Pref_CP437_CI_AS,  
Col2 AS TERTIARY_WEIGHTS(Col1));  
GO   
```  
  
## <a name="see-also"></a>Vea también
[ORDER BY Clause &#40;Transact-SQL&#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md)
  
  
