---
title: STNumCurves (tipo de datos geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 1eb57ac476d430d5bc79c71ce5c6a12087155366
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "68088999"
---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (tipo de datos geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Este método devuelve el número de curvas en una instancia de **geometry** cuando la instancia es un tipo de datos espacial unidimensional. Los tipos de datos espaciales unidimensionales incluyen **LineString**, **CircularString** y **CompoundCurve**. `STNumCurves`() solo funciona en tipos simples; no funciona con colecciones de **geometry** como **MultiLineString**.
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Tipos de valor devuelto  
 Tipo de valor devuelto de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Tipo de valor devuelto de CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Observaciones  
 Una instancia vacía unidimensional de **geometry** devuelve 0. Se devuelve **NULL** cuando la instancia de **geometry** no es una instancia unidimensional o es una instancia no inicializada.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Usar STNumCurves() en una instancia de CircularString  
 En el siguiente ejemplo se muestra cómo obtener el número de curvas de una instancia de `CircularString`:  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Usar STNumCurves() en una instancia de CompoundCurve  
 En el siguiente ejemplo se utiliza `STNumCurves()` para devolver el número de curvas de una instancia de `CompoundCurve`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>Consulte también  
 [Información general de los tipos de datos espaciales](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Métodos de OGC en instancias de geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

