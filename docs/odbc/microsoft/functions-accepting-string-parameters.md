---
title: Aceptar parámetros de cadena de funciones | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], string parameters
- ODBC desktop database drivers [ODBC], string parameters
- Jet-based ODBC drivers [ODBC], string parameters
- functions [ODBC], string parameters
- string parameters [ODBC]
ms.assetid: 869b8421-f71e-4dfd-adce-691bd3012b16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61bb013885238492d9c7324658ede198c489361d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127323"
---
# <a name="functions-accepting-string-parameters"></a>Aceptar parámetros de cadena de funciones
Todas las funciones que toman parámetros de cadena se convierten a Unicode. (Se exportará la forma "W" de la función.) Recuento de bytes se convierte al recuento de caracteres para las API de ODBC aplicable. Esto se aplica a las funciones siguientes:  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLColAttributes**  
  
-   **SQLDescribeCol**  
  
-   **SQLError** (reemplazado por **SQLGetDiagField**)  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **SQLSetCursorName**  
  
-   **SQLGetStmtAttr**  
  
-   **SQLGetInfo**  
  
-   **SQLGetStmtOption** (becomes **SQLGetStmtAttr**)  
  
-   **SQLSetStmtOption** (becomes **SQLSetStmtAttr**)  
  
-   **SQLGetConnectOption**  
  
-   **SQLSetConnectOption**  
  
-   **SQLGetTypeInfo**  
  
-   **SQLStatistics**  
  
-   **SQLTables**  
  
-   **SQLNativeSQL**  
  
-   **SQLSpecialColumns**  
  
-   **ConfigDSNEx**  
  
-   **ConfigDSN**
