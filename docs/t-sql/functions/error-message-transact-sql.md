---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
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
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 598b89a47941c038b39387468de8bd3036acae2b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve el texto del mensaje del error que ha provocado la ejecución del bloque CATCH de una construcción TRY…CATCH.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Valor devuelto  
 Cuando se ha llamado en un bloque CATCH, devuelve el texto completo del mensaje de error que ha provocado la ejecución del bloque CATCH. El texto incluye los valores proporcionados para los parámetros sustituibles, como las longitudes, nombres de objeto o tiempos.  
  
 Devuelve NULL si se le llama desde fuera del ámbito del bloque CATCH.  
  
## <a name="remarks"></a>Notas  
 Puede llamarse a ERROR_MESSAGE desde cualquier lugar del ámbito de un bloque CATCH.  
  
 ERROR_MESSAGE devuelve el mensaje de error con independencia de cuántas veces se haya ejecutado, o en qué parte del ámbito del bloque CATCH se ejecute. Esto contrasta con funciones como @@@ERROR, que solo devuelve un número de error en la instrucción inmediatamente posterior a la que causa un error, o la primera instrucción de un bloque CATCH.  
  
 En bloques CATCH anidados, ERROR_MESSAGE devuelve el mensaje de error específico del ámbito del bloque CATCH en el que se hace referencia a él. Por ejemplo, el bloque CATCH de una construcción TRY...CATCH externa podría tener una construcción TRY...CATCH anidada. En el bloque CATCH anidado, ERROR_MESSAGE devuelve el mensaje del error que ha invocado el bloque CATCH anidado. Si se ejecuta ERROR_MESSAGE en el bloque CATCH externo, devuelve el mensaje del error que ha invocado el bloque CATCH.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Usar ERROR_MESSAGE en un bloque CATCH  
 El siguiente ejemplo de código muestra una instrucción `SELECT` que genera un error de división por cero. Se devuelve el mensaje de error.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. Usar ERROR_MESSAGE en un bloque CATCH con otras herramientas de control de errores.  
 El siguiente ejemplo de código muestra una instrucción `SELECT` que genera un error de división por cero. Además del mensaje de error, se devuelve información relacionada con el error.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>C. Usar ERROR_MESSAGE en un bloque CATCH con otras herramientas de control de errores.  
 El siguiente ejemplo de código muestra una instrucción `SELECT` que genera un error de división por cero. Además del mensaje de error, se devuelve información relacionada con el error.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  

