---
description: REPLACE (expresión de SSIS)
title: REPLACE (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe1fae03a09aace19069d3aaeba55f0fbb4b36ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477500"
---
# <a name="replace-ssis-expression"></a>REPLACE (expresión de SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Devuelve una expresión de caracteres tras reemplazar una cadena de caracteres dentro de la expresión por otra cadena de caracteres diferente o por la cadena vacía.  
  
> [!NOTE]  
>  La función REPLACE usa con frecuencia cadenas largas. Las consecuencias del truncamiento pueden controlarse o pueden dar lugar a una advertencia o un error. Para obtener más información, vea [Sintaxis &#40;SSIS&#41;](../../integration-services/expressions/syntax-ssis.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>Argumentos  
 *character_expression*  
 Expresión de caracteres válida que busca la función.  
  
 *searchstring*  
 Expresión de caracteres válida que intenta encontrar la función.  
  
 *replacementstring*  
 Expresión de caracteres válida que se usa como expresión de reemplazo.  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_WSTR  
  
## <a name="remarks"></a>Observaciones  
 La longitud de *searchstring* no debe ser cero.  
  
 La longitud de *replacementstring* puede ser cero.  
  
 Los argumentos *searchstring* y *replacementstring* pueden utilizar variables y columnas.  
  
 REPLACE solo funciona con el tipo de datos DT_WSTR. Los argumentos*character_expression1, character_expression2* y *character_expression3* que son literales de cadena o columnas de datos con el tipo de datos DT_STR se convierten implícitamente al tipo de datos DT_WSTR antes de que REPLACE realice su operación. Los otros tipos de datos deben convertirse explícitamente al tipo de datos DT_WSTR. Para más información, vea [Conversión &#40;expresión de SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 REPLACE devuelve un resultado NULL si alguno de los argumentos es NULL.  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo usa un literal de cadena. El resultado devuelto es "All Terrain Bike".  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 Este ejemplo quita la cadena "Bike" de la columna **Product** .  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 Este ejemplo reemplaza los valores de la columna **DaysToManufacture** . La columna tiene un tipo de datos Integer y en la expresión se incluye la conversión de **DaysToManufacture** al tipo de datos DT_WSTR.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>Vea también  
 [SUBSTRING &#40;expresión de SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
