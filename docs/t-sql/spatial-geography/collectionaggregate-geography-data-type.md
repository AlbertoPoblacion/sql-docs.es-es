---
title: CollectionAggregate (tipo de datos geography) | Microsoft Docs
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c697a43ac6b79fd137da968ce5f01e49e60c105
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate (tipo de datos geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Crea una instancia de **GeometryCollection** a partir de un conjunto de objetos **geography**.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argumentos  
 *geography_operand*  
 Es una columna de tabla de tipo **geography** que representa un conjunto de objetos **geography** que se van a enumerar en la instancia de **GeometryCollection**.  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
## <a name="exception"></a>Excepción  
 Produce una excepción `FormatException` cuando hay valores de entrada no válidos. Vea [STIsValid &#40;geography Data Type&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md) (STIsValid [tipo de datos geography]).  
  
## <a name="remarks"></a>Notas  
 El método devuelve **null** cuando la entrada está vacía o esta tiene unos SRID diferentes. Vea [Identificadores de referencia espacial &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 El método omite las entradas **null**.  
  
> [!NOTE]  
>  El método devuelve **null** si todos los valores introducidos son **null**.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve una instancia de `GeometryCollection` que contiene un conjunto de objetos **geography**.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>Ver también  
 [Métodos de geografía estáticos extendidos](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
