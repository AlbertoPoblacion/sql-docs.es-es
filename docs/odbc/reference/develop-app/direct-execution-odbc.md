---
title: "Dirigen la ejecución ODBC | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], direct execution
- direct execution [ODBC]
- SQL statements [ODBC], executing
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 058dada1c14b901b32f721bc2d42f3cc24434f07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="direct-execution-odbc"></a>Ejecución directa ODBC
La ejecución directa es la manera más sencilla de ejecutar una instrucción. Cuando la instrucción se envía para su ejecución, el origen de datos lo compila en un plan de acceso y, a continuación, ejecuta ese plan de acceso.  
  
 La ejecución directa es más frecuente por aplicaciones genéricas que generan y ejecutan instrucciones en tiempo de ejecución. Por ejemplo, el código siguiente crea una instrucción SQL y ejecuta una sola vez:  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 La ejecución directa funciona mejor con las instrucciones que se ejecutará una sola vez. Su principal inconveniente es que la instrucción SQL se analiza cada vez que se ejecuta. Además, la aplicación no puede recuperar información sobre el conjunto de resultados creado por la instrucción (si existe) hasta después de la instrucción se ejecuta; Esto es posible si la instrucción se prepara y se ejecuta en dos pasos independientes.  
  
 Para ejecutar una instrucción directamente, la aplicación realiza las siguientes acciones:  
  
1.  Establece los valores de los parámetros. Para obtener más información, consulte [parámetros de la instrucción](../../../odbc/reference/develop-app/statement-parameters.md), más adelante en esta sección.  
  
2.  Llamadas **SQLExecDirect** y le pasa una cadena que contiene la instrucción SQL.  
  
3.  Cuando **SQLExecDirect** se llama, el controlador:  
  
    -   Modifica la instrucción SQL para el uso de la gramática SQL del origen de datos sin analizar la instrucción; Esto incluye reemplazando las secuencias de escape que se describen en [secuencias de Escape de ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). La aplicación puede recuperar el formulario modificado de una instrucción SQL mediante una llamada a **SQLNativeSql**. No se reemplazan las secuencias de escape si se establece el atributo de instrucción SQL_ATTR_NOSCAN.  
  
    -   Recupera los valores de parámetro actuales y los convierte según sea necesario. Para obtener más información, consulte [parámetros de la instrucción](../../../odbc/reference/develop-app/statement-parameters.md), más adelante en esta sección.  
  
    -   Envía la instrucción y los valores de parámetro convertido al origen de datos para su ejecución.  
  
    -   Devuelve los errores. Puede tratarse de secuenciación o diagnóstico de estado como SQLSTATE 24000 (estado de cursor no válido), los errores sintácticos, como SQLSTATE 42000 (sintaxis o infracción de acceso) y errores semánticos como SQLSTATE 42S02 (con Base en tabla o vista no encontrado).
