---
title: COMO carácter de Escape de predicado | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20310c60759aea17d61b9252fd73d226567a7a54
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027233"
---
# <a name="like-predicate-escape-character"></a>COMO carácter de Escape de predicado
En un **como** predicado, el signo de porcentaje (%) coincide con cero o más de cualquier carácter y el carácter de subrayado (_) coincide con cualquier carácter. Para buscar un signo de porcentaje real o un carácter de subrayado en un **como** predicado, un carácter de escape debe ir antes del signo de porcentaje o el carácter de subrayado. La secuencia de escape que define el **como** carácter de escape de predicado es:  
  
 **{escape '** *carácter de escape* **'}**  
  
 donde *carácter de escape* es cualquier carácter compatible con el origen de datos.  
  
 Para obtener más información sobre el tipo de secuencia de escape, consulte [como secuencia de Escape](../../../odbc/reference/appendixes/like-escape-sequence.md) en el apéndice C: Gramática de SQL.  
  
 Por ejemplo, las siguientes instrucciones SQL crean el mismo conjunto de resultados del cliente de nombres que empiezan con los caracteres "% AAA". La primera instrucción usa la sintaxis de la secuencia de escape. La segunda instrucción utiliza la sintaxis nativa para Microsoft® Access y no es interoperable. Tenga en cuenta que el segundo carácter de porcentaje de cada **como** predicado es un carácter comodín que coincide con cero o más de cualquier carácter.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Para determinar si el **como** carácter de escape de predicado es compatible con un origen de datos, una aplicación llama a **SQLGetInfo** con la opción SQL_LIKE_ESCAPE_CLAUSE.
