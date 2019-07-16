---
title: Uso de identificadores de tipo de datos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b5e9fea64986bf595676540d74bb87a6e62521c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070015"
---
# <a name="using-data-type-identifiers"></a>Usar identificadores de tipo de datos
Las aplicaciones utilizar identificadores de tipo de datos de dos maneras: para describir sus búferes en el controlador y para recuperar metadatos sobre el conjunto de resultados desde el controlador para que pueda determinar qué tipo de C almacena en búfer para que use para almacenar los datos. Las aplicaciones llaman a las siguientes funciones para llevar a cabo estas tareas:  
  
-   **SQLBindParameter**, **SQLBindCol**, y **SQLGetData** : para describir el tipo de datos C de búferes de la aplicación.  
  
-   **SQLBindParameter** : para describir el tipo de datos SQL de parámetros dinámicos.  
  
-   **SQLColAttribute** y **SQLDescribeCol** , para recuperar los tipos de datos SQL de columnas del conjunto de resultados.  
  
-   **SQLDescribeParameter** , para recuperar los tipos de datos SQL de parámetros.  
  
-   **SQLColumns**, **SQLProcedureColumns**, y **SQLSpecialColumns** , para recuperar los tipos de datos SQL de diversa información de esquema  
  
-   **SQLGetTypeInfo** : para recuperar una lista de tipos de datos admitidos  
  
 Identificadores de tipo de datos se almacenan en el campo SQL_DESC_CONCISE_TYPE de un descriptor. Las funciones de descriptor **SQLSetDescField** y **SQLSetDescRec** puede usarse con los tipos adecuados para realizar las tareas enumeradas en la lista anterior. Para obtener más información, consulte [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
