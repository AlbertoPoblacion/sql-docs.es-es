---
title: COMPRESS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 898a7e4cea01b37bcb45334a3fc669cb63357d9d
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "65943904"
---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Esta función comprime la expresión de entrada usando el algoritmo GZIP. La función devuelve una matriz de bytes del tipo **varbinary(max)** .
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argumentos  
*expression*  
Un

* **binary(***n***)**
* **char(***n***)**
* **nchar(***n***)**
* **nvarchar(max)**
* **nvarchar(***n***)**
* **varbinary(max)**
* **varbinary(***n***)**
* **ntext**

o Administrador de configuración de

* **varchar(***n***)**

expression: Para más información, vea [Expresiones &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Tipos de valores devueltos
**varbinary(max)** representa el contenido comprimido de la entrada.
  
## <a name="remarks"></a>Notas  
Los datos comprimidos no se pueden indexar.
  
La función `COMPRESS` comprime los datos de la expresión de entrada. Debe invocar esta función para cada sección de datos que se vaya a comprimir. Vea [Compresión de datos](../../relational-databases/data-compression/data-compression.md) para obtener más información acerca de la compresión de datos automática durante el almacenamiento en el nivel de fila o página.
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Comprimir datos durante la inserción de tabla  
En este ejemplo se muestra cómo comprimir los datos insertados en una tabla:
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. Archivar una versión comprimida de filas eliminadas  
Esta instrucción primero elimina los registros antiguos del reproductor de la tabla `player`. Para ahorrar espacio, luego almacena los registros en la tabla `inactivePlayer`, en un formato comprimido.
  
```sql
DELETE FROM player  
OUTPUT deleted.id, deleted.name, deleted.surname, deleted.datemodifier, COMPRESS(deleted.info)   
INTO dbo.inactivePlayers
WHERE datemodified < @startOfYear; 
```  
  
## <a name="see-also"></a>Vea también
[Funciones de cadena &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRESS &#40;Transact-SQL&#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  
