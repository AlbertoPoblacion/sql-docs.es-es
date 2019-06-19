---
title: SET OFFSETS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 86733abf5f744a50275db88fa443c82c51ae4394
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939834"
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el desplazamiento (posición con respecto al inicio de una instrucción) de las palabras clave especificadas en instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] a aplicaciones DB-Library.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>Argumentos  
 *keyword_list*  
 Es una lista separada por comas de construcciones de [!INCLUDE[tsql](../../includes/tsql-md.md)], entre las que se incluyen SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM y EXECUTE.  
  
## <a name="remarks"></a>Notas  
 SET OFFSETS solo se utiliza en aplicaciones DB-Library.  
  
 La opción SET OFFSETS se establece en tiempo de análisis, no en tiempo de ejecución. El establecimiento en tiempo de análisis significa que si la instrucción SET está presente en el proceso por lotes o el procedimiento almacenado, la configuración tendrá efecto aunque la ejecución del código no llegue al punto donde se encuentre; y se aplicará antes de que se ejecute ninguna otra instrucción. Por ejemplo, la instrucción SET tendrá efecto incluso cuando se encuentre en un bloque de una instrucción IF…ELSE que no se alcance nunca en la ejecución, ya que se analiza el bloque de la instrucción IF…ELSE.  
  
 Si se establece SET OFFSETS en un procedimiento almacenado, su valor se restablecerá cuando el procedimiento almacenado devuelva el control. Por ello, una instrucción SET OFFSETS especificada en SQL dinámico no tiene ningún efecto en las instrucciones siguientes.  
  
 SET PARSEONLY devuelve los desplazamientos si la opción OFFSETS es ON y no hay errores.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer al rol **public** .  
  
## <a name="see-also"></a>Consulte también  
 [Instrucciones SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY &#40;Transact-SQL&#41;](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  
