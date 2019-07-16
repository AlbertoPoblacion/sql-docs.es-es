---
title: Las cadenas de conexión | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f68a87db729df2f4a27e2766a9de60e8c75a71a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036425"
---
# <a name="connection-strings"></a>Cadenas de conexión
Una cadena de conexión contiene información utilizada para establecer una conexión. Una cadena de conexión completa contiene toda la información necesaria para establecer una conexión. La cadena de conexión es una serie de pares palabra clave-valor separados por punto y coma. (Para ver la sintaxis completa de una cadena de conexión, consulte el [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descripción de la función.) Usa la cadena de conexión:  
  
-   **SQLDriverConnect**, lo que finaliza la cadena de conexión mediante la interacción con el usuario.  
  
-   **SQLBrowseConnect**, lo que finaliza la cadena de conexión de forma iterativa con el origen de datos.  
  
 **SQLConnect** no utiliza una cadena de conexión; el uso de **SQLConnect** es análoga a la conexión con una cadena de conexión exactamente tres pares palabra clave-valor (para el nombre del origen de datos y, opcionalmente, el usuario ID y contraseña) .
