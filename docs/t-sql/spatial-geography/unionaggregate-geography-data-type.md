---
title: UnionAggregate (tipo de datos geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- UnionAggregate
- UnionAggregate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UnionAggregate method (geography)
ms.assetid: 1a3aeef1-5b0e-4ae8-aeb7-c4aab22f42ab
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 3057127174cd7a8594685e8e4e71ba1134902435
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936010"
---
# <a name="unionaggregate-geography-data-type"></a>UnionAggregate (tipo de datos geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Realiza una operación de unión en un conjunto de objetos de geografía.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
UnionAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argumentos  
 *geography_operand*  
 Es una columna de tabla de tipo **geography** que contiene el conjunto de objetos **geography** en el que se va a realizar una operación de unión.  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
## <a name="remarks"></a>Notas  
 El método devuelve **null** si la entrada tiene SRID diferentes. Vea [Identificadores de referencia espacial &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 El método omite las entradas **null**.  
  
> [!NOTE]  
>  El método devuelve **null** si todos los valores introducidos son **null**.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se realiza una operación `UnionAggregate` en un conjunto de puntos de ubicación de tipo **geography** de una ciudad.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::UnionAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a>Consulte también  
 [Métodos de geografía estáticos extendidos](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
