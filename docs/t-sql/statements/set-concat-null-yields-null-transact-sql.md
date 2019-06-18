---
title: SET CONCAT_NULL_YIELDS_NULL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CONCAT_NULL_YIELDS_NULL_TSQL
- SET CONCAT_NULL_YIELDS_NULL
- CONCAT_NULL_YIELDS_NULL
- SET_CONCAT_NULL_YIELDS_NULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_NULL_YIELDS_NULL option
- null values [SQL Server], concatenation results
- concatenation [SQL Server]
- SET CONCAT_NULL_YIELDS_NULL statement
ms.assetid: 3091b71c-6518-4eb4-88ab-acae49102bc5
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fa91003f0afd18372119864175806b4a8b9b6655
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639328"
---
# <a name="set-concatnullyieldsnull-transact-sql"></a>SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Determina si los resultados de la concatenación se tratan como valores NULL o como valores de cadena vacía.  
  
> [!IMPORTANT]  
>  En una versión futura de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], CONCAT_NULL_YIELDS_NULL siempre estará establecida en ON y cualquier aplicación que establezca de forma explícita la opción en OFF generará un error. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- Syntax for SQL Server  
    
SET CONCAT_NULL_YIELDS_NULL { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET CONCAT_NULL_YIELDS_NULL ON    
```  
  
## <a name="remarks"></a>Notas  
 Cuando SET CONCAT_NULL_YIELDS_NULL es ON, al concatenar un valor NULL con una cadena se produce como resultado NULL. Por ejemplo, `SELECT 'abc' + NULL` produce `NULL`. Cuando SET CONCAT_NULL_YIELDS_NULL es OFF, al concatenar un valor NULL con una cadena se obtiene la propia cadena (el valor NULL se trata como una cadena vacía). Por ejemplo, `SELECT 'abc' + NULL` produce `abc`.  
  
 Si no se especifica SET CONCAT_NULL_YIELDS_NULL, se aplica la configuración de la opción de base de datos **CONCAT_NULL_YIELDS_NULL**.  
  
> [!NOTE]  
>  La opción SET CONCAT_NULL_YIELDS_NULL es igual que la opción CONCAT_NULL_YIELDS_NULL de ALTER DATABASE.  
  
 La opción SET CONCAT_NULL_YIELDS_NULL se establece en tiempo de ejecución, no en tiempo de análisis.  

SET CONCAT_NULL_YIELDS_NULL debe ser **ON** al crear o cambiar vistas indexadas, índices en columnas calculadas, índices filtrados o índices espaciales. Si SET CONCAT_NULL_YIELDS_NULL es **OFF**, las instrucciones CREATE, UPDATE, INSERT y DELETE en tablas con índices, en columnas calculadas, en índices filtrados, en índices espaciales o en vistas indexadas generarán errores. Para más información sobre las configuraciones de las opciones SET necesarias con vistas indizadas e índices en columnas calculadas, vea el apartado "Consideraciones al utilizar las instrucciones SET" en [Instrucciones SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md).
  
 Cuando CONCAT_NULL_YIELDS_NULL se establece en OFF, no se puede producir la concatenación de cadenas entre los límites del servidor.  
  
 Para ver la configuración actual de este valor, ejecute la consulta siguiente.  
  
```  
DECLARE @CONCAT_NULL_YIELDS_NULL VARCHAR(3) = 'OFF';  
IF ( (4096 & @@OPTIONS) = 4096 ) SET @CONCAT_NULL_YIELDS_NULL = 'ON';  
SELECT @CONCAT_NULL_YIELDS_NULL AS CONCAT_NULL_YIELDS_NULL;  
  
```  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se muestra el uso de los dos valores de `SET CONCAT_NULL_YIELDS_NULL`.  
  
```  
PRINT 'Setting CONCAT_NULL_YIELDS_NULL ON';  
GO  
-- SET CONCAT_NULL_YIELDS_NULL ON and testing.  
SET CONCAT_NULL_YIELDS_NULL ON;  
GO  
SELECT 'abc' + NULL ;  
GO  
  
-- SET CONCAT_NULL_YIELDS_NULL OFF and testing.  
SET CONCAT_NULL_YIELDS_NULL OFF;  
GO  
SELECT 'abc' + NULL;   
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [Instrucciones SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
