---
title: Función SQLSetConnectInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 448b0f5e34a6b7421c23a1267dd9cd68bd93ca6f
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537180"
---
# <a name="sqlsetconnectinfo-function"></a>Función SQLSetConnectInfo
**Conformidad**  
 Versión de introducción: Cumplimiento de estándares 3,81 de ODBC: ODBC  
  
 **Resumen**  
 **SQLSetConnectInfo** se usa para establecer el origen de datos, el Id. de usuario y la contraseña en el símbolo (token) de información de conexión para una aplicación [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) llamar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
  
SQLRETURN  SQLSetConnectInfo(  
                SQLHDBC_INFO_TOKEN   TokenHandle,  
                WCHAR *              ServerName,  
                SQLSMALLINT          NameLength1,  
                WCHAR *              UserName,  
                SQLSMALLINT          NameLength2,  
                WCHAR *              Authentication,  
                SQLSMALLINT          NameLength3 );  
```  
  
## <a name="arguments"></a>Argumentos  
 *TokenHandle*  
 [Entrada] Identificador del token.  
  
 *ServerName*  
 [Entrada] Nombre del origen de datos. Los datos es posible que se encuentra en el mismo equipo que el programa, o en otro equipo en alguna parte de una red. Para obtener información acerca de cómo una aplicación elige un origen de datos, vea [elegir un origen de datos o controlador](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Entrada] Longitud de **ServerName* en caracteres.  
  
 *UserName*  
 [Entrada] Identificador de usuario.  
  
 *NameLength2*  
 [Entrada] Longitud de **UserName* en caracteres.  
  
 *Autenticación*  
 [Entrada] Cadena de autenticación (normalmente, la contraseña).  
  
 *NameLength3*  
 [Entrada] Longitud de **autenticación* en caracteres.  
  
## <a name="returns"></a>Devuelve  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnósticos  
 Igual que [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) para errores de validación de entrada, salvo que se va a usar el Administrador de controladores un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN y un **controlar** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Comentarios  
 Cada vez que un controlador devuelve SQL_ERROR o SQL_INVALID_HANDLE, el Administrador de controladores devuelve el error a la aplicación (en [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) o [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Cada vez que un controlador devuelve SQL_SUCCESS_WITH_INFO, el Administrador de controladores obtendrá la información de diagnóstico de *hDbcInfoToken*y devuelvan SQL_SUCCESS_WITH_INFO a la aplicación en [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)y [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Las aplicaciones no deben llamar directamente a esta función. Un controlador ODBC que admite la agrupación de conexiones dependientes del controlador debe implementar esta función.  
  
 Incluir sqlspi.h para el desarrollo de controladores ODBC.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un controlador ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Agrupación de conexiones dependientes del controlador](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Desarrollar el conocimiento de la agrupación de conexiones en un controlador ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
