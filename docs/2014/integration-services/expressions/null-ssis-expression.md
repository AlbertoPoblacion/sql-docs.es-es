---
title: NULL (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f4a796b0ab746468ffef3cab5b3480e73b4cf637
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62768831"
---
# <a name="null-ssis-expression"></a>NULL (expresión de SSIS)
  Devuelve un valor NULL asociado al tipo de datos solicitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Argumentos  
 *typespec*  
 Tipo de datos válido. Para obtener más información, vea [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipos de resultado  
 Cualquier tipo de datos válido con valor NULL.  
  
## <a name="remarks"></a>Comentarios  
 NULL devuelve un resultado NULL si el valor del argumento es NULL.  
  
 Para solicitar un valor NULL para algunos tipos de datos es necesario utilizar parámetros. En la tabla siguiente se muestran estos tipos de datos y sus parámetros.  
  
|Tipo de datos|Parámetro|Ejemplo|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) convierte 30 caracteres al tipo de datos DT_STR con la página de códigos 1252.|  
|DT_WSTR|*charcount*|(DT_WSTR,20) convierte 20 caracteres al tipo de datos DT_WSTR.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) convierte 50 bytes al tipo de datos DT_BYTES.|  
|DT_DECIMAL|*escala*|(DT_DECIMAL,2) convierte un valor numérico al tipo de datos DT_DECIMAL con una escala de 2.|  
|DT_NUMERIC|*precisión*<br /><br /> *scale*|(DT_NUMERIC,10,3) convierte un valor numérico al tipo de datos DT_NUMERIC con una precisión de 10 decimales y una escala de 3.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) convierte un valor al tipo de datos DT_TEXT con la página de códigos 1252.|  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Estos ejemplos devuelven el valor NULL de los tipos de datos: DT_STR, DT_DATE y DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>Vea también  
 [ISNULL &#40;expresión de SSIS&#41;](null-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](functions-ssis-expression.md)  
  
  
