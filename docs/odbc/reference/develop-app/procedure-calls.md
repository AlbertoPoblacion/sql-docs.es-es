---
title: Las llamadas a procedimiento | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure calls
- procedure calls [ODBC]
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 775b48eb5a7f2089d65c6e9548a986b2f7b9bec7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63284576"
---
# <a name="procedure-calls"></a>Llamadas a procedimientos
Un *procedimiento* es un objeto ejecutable almacenado en el origen de datos. Normalmente, se trata de una o varias instrucciones SQL compiladas. Es la secuencia de escape para llamar a un procedimiento  
  
 **{** [ **?=** ]**call** *procedure-name*[ **(** [*parameter*][ **,** [*parameter*]]... **)** ] **}**  
  
 donde *nombre del procedimiento* especifica el nombre de un procedimiento y *parámetro* especifica un parámetro de procedimiento.  
  
 Para obtener más información acerca de la secuencia de escape de llamada de procedimiento, consulte [secuencia de Escape de llamar al procedimiento](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) en el apéndice C: Gramática de SQL.  
  
 Un procedimiento puede tener cero o más parámetros. También puede devolver un valor, como se indica por el marcador de parámetro opcional **? =** al principio de la sintaxis. Si *parámetro* es una entrada o un parámetro de entrada/salida, puede ser un literal o un marcador de parámetro. Sin embargo, las aplicaciones interoperables siempre deben usar marcadores de parámetros debido a algunos orígenes de datos no aceptan valores de parámetro literal. Si *parámetro* es un parámetro output, debe ser un marcador de parámetro. Marcadores de parámetros deben enlazarse a **SQLBindParameter** antes de la llamada de procedimiento se ejecuta la instrucción.  
  
 Los parámetros de entrada y de entrada/salida pueden omitirse de las llamadas a procedimiento. Si se llama a un procedimiento con paréntesis pero sin parámetros, tales como {llamar *nombre del procedimiento*()}, el controlador indica el origen de datos que se usará el valor predeterminado para el primer parámetro. Si el procedimiento no tiene ningún parámetro, esto podría hacer que el procedimiento producirá un error. Si se llama a un procedimiento sin paréntesis, como {llamar *nombre del procedimiento*}, el controlador no envía los valores de parámetro.  
  
 Pueden especificarse literales para los parámetros de entrada y de entrada/salida en llamadas a procedimiento. Por ejemplo, suponga que el procedimiento **InsertOrder** tiene cinco parámetros de entrada. La siguiente llamada a **InsertOrder** omite el primer parámetro, proporciona un literal para el segundo parámetro y usa un marcador de parámetro para la tercera, cuarta y quinta parámetros:  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Tenga en cuenta que si se omite un parámetro, todavía debe aparecer la coma que lo separa de otros parámetros. Si se omite un parámetro de entrada o de entrada/salida, el procedimiento usa el valor predeterminado del parámetro. Otra manera de especificar que el valor predeterminado de un parámetro de entrada o de entrada/salida consiste en establecer el valor del búfer de longitud/indicador enlazado al parámetro en SQL_DEFAULT_PARAM.  
  
 Si se omite un parámetro de entrada y salida o si se proporciona un literal para el parámetro, el controlador descarta el valor de salida. Del mismo modo, si se omite el marcador de parámetro para el valor devuelto de un procedimiento, el controlador descarta dicho valor devuelto. Finalmente, si una aplicación especifica un parámetro de valor devuelto para un procedimiento que no devuelve ningún valor, el controlador establece el valor del búfer de longitud/indicador enlazado al parámetro en SQL_NULL_DATA.  
  
 Supongamos que el procedimiento PARTS_IN_ORDERS crea un conjunto de resultados que contiene una lista de pedidos que contienen un número de pieza concreta. El código siguiente llama a este procedimiento para el número de pieza 544:  
  
```  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_SLONG, SQL_INTEGER, 0, 0,  
                  &PartID, 0, PartIDInd);  
  
// Place the department number in PartID.  
PartID = 544;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "{call PARTS_IN_ORDERS(?)}", SQL_NTS);  
```  
  
 Para determinar si un origen de datos admite los procedimientos, una aplicación llama a **SQLGetInfo** con la opción SQL_PROCEDURES.  
  
 Para obtener más información acerca de los procedimientos, consulte [procedimientos](../../../odbc/reference/develop-app/procedures-odbc.md).
