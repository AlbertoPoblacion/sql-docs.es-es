---
title: Argumentos de la función Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1fee0aa76bc5b903d65461261a8eb5dbc2349581
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087765"
---
# <a name="unicode-function-arguments"></a>Argumentos de función de Unicode
El Administrador de controladores ODBC 3.5 (o superior) es compatible con versiones ANSI y Unicode de todas las funciones que aceptan los punteros a cadenas de caracteres o SQLPOINTER en sus argumentos. Las funciones Unicode se implementan como funciones (con un sufijo de *W*), no como macros. Las funciones de ANSI (que se puede llamar con o sin un sufijo de *A*) son idénticas a las funciones de API de ODBC actuales.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones Unicode que siempre devuelven o toman argumentos de longitud o las cadenas se pasan como recuento de caracteres. Para las funciones que devuelven información sobre la longitud de datos del servidor, el tamaño de presentación y la precisión se describen en el número de caracteres. Cuando una longitud (tamaño de transferencia de los datos) puede hacer referencia a los datos de cadena o que no son cadenas, la longitud se describe en las longitudes de octeto. Por ejemplo, **SQLGetInfoW** le conducirá a la longitud que el recuento de bytes, pero **SQLExecDirectW** usará el recuento de caracteres.  
  
 Recuento de caracteres se refiere al número de bytes (octetos) para las funciones de ANSI y el número de WCHAR (palabras de 16 bits) para las funciones UNICODE. En concreto, una secuencia de caracteres de doble byte (DBCS) o una secuencia de caracteres multibyte (MBCS) se puede componer de varios bytes. Una secuencia de caracteres Unicode UTF-16 puede estar formada por varios número de WCHAR.  
  
 La siguiente es una lista de las funciones de API de ODBC que admiten las versiones de Unicode (W) y ANSI (A):  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagField**|  
|**SQLColAttribute**|**SQLGetDiagRec**|  
|**SQLColAttributes**|**SQLGetInfo**|  
|**SQLColumnPrivileges**|**SQLGetStmtAttr**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
  
 La siguiente es una lista de las funciones ODBC instalador y el traductor de ODBC que admiten las versiones de Unicode (W) y ANSI (A):  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  Funciones en desuso tienen compatibilidad con la asignación de Unicode a ANSI porque ODBC *3.x* volver a compilar ODBC admite el Administrador de controladores *2.x* aplicaciones con UNICODE **#define**.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Aplicaciones de Unicode](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Controladores de Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Asignación de función en el Administrador de controladores](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
