---
title: GETDATE (expresión de SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 492e3f702fc5ae851a6d78aae2df5fa26e5ca379
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080931"
---
# <a name="getdate-ssis-expression"></a>GETDATE (expresión de SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Devuelve la fecha actual del sistema con formato DT_DBTIMESTAMP. La función GETDATE no tiene argumentos.  
  
> [!NOTE]  
>  El resultado devuelto de la función GETDATE tiene una longitud de 29 caracteres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Argumentos  
 None  
  
## <a name="result-types"></a>Tipos de resultado  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Ejemplos de expresiones  
 Este ejemplo devuelve el año de la fecha actual.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 Este ejemplo devuelve el número de días entre una fecha de la columna **ModifiedDate** y la fecha actual.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 Este ejemplo agrega tres meses a la fecha actual.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>Consulte también  
 [GETUTCDATE &#40;expresión de SSIS&#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
