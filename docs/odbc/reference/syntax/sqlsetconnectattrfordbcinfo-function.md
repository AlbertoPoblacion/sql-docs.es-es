---
title: Función SQLSetConnectAttrForDbcInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 798f986adfeda95ef091161458d94c2ccc33b2e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63125540"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>Función SQLSetConnectAttrForDbcInfo
**Conformidad**  
 Versión de introducción: Cumplimiento de estándares 3,81 de ODBC: ODBC  
  
 **Resumen**  
 **SQLSetConnectAttrForDbcInfo** es el mismo que **SQLSetConnectAttr**, pero establece el atributo en el token de la información de conexión en lugar de en el identificador de conexión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Argumentos  
 *hDbcInfoToken*  
 [Entrada] Identificador del token.  
  
 *Atributo*  
 [Entrada] Atributo que se establecerá. La lista de atributos válidas es específico del controlador y los mismos que para [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Entrada] Puntero al valor que se asociará con *atributo*. Dependiendo del valor de *atributo*, *ValuePtr* será un valor entero sin signo de 32 bits o hará referencia a una cadena de caracteres terminada en null. Observe que si el *atributo* argumento es un valor específico del controlador, el valor de *ValuePtr* puede ser un entero con signo.  
  
 *StringLength*  
 [Entrada] Si *atributo* es un atributo definido por el ODBC y *ValuePtr* apunta a un búfer binario o una cadena de caracteres, este argumento debe ser la longitud de **ValuePtr*. Para los datos de cadena de caracteres, este argumento debe contener el número de bytes en la cadena.  
  
 Si *atributo* es un atributo definido por el ODBC y *ValuePtr* es un entero, *StringLength* se omite.  
  
 Si *atributo* es un atributo definido por el controlador, la aplicación indica la naturaleza del atributo para el Administrador de controladores al establecer el *StringLength* argumento. *StringLength* puede tener los siguientes valores:  
  
-   Si *ValuePtr* es un puntero a una cadena de caracteres, a continuación, *StringLength* es la longitud de la cadena o SQL_NTS.  
  
-   Si *ValuePtr* es un puntero a un búfer binario, a continuación, la aplicación, el resultado de la SQL_LEN_BINARY_ATTR (*longitud*) macro en *StringLength*. Esto coloca un valor negativo en *StringLength*.  
  
-   Si *ValuePtr* es un puntero a un valor distinto de una cadena de caracteres o una cadena binaria, a continuación, *StringLength* debe tener el valor SQL_IS_POINTER.  
  
-   Si *ValuePtr* contiene un valor de longitud fija, a continuación, *StringLength* es SQL_IS_INTEGER o SQL_IS_UINTEGER, según corresponda.  
  
## <a name="returns"></a>Devuelve  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnósticos  
 Igual que [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), salvo que se va a usar el Administrador de controladores un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN y un **controlar** de *hDbcInfoToken* .  
  
## <a name="remarks"></a>Comentarios  
 **SQLSetConnectAttrForDbcInfo** es el mismo que **SQLSetConnectAttr**, pero establece el atributo en el token de información de conexión, en lugar de en el identificador de conexión. Por ejemplo, si **SQLSetConnectAttr** no reconoce un atributo, **SQLSetConnectAttrForDbcInfo** también se debe devolver SQL_ERROR para ese atributo.  
  
 Cada vez que el controlador devuelve SQL_ERROR o SQL_INVALID_HANDLE, el controlador debe pasar por alto este atributo para calcular el identificador de grupo. Además, va a obtener la información de diagnóstico desde el Administrador de controladores *hDbcInfoToken*y devuelvan SQL_SUCCESS_WITH_INFO a la aplicación en [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) y [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Por lo tanto, una aplicación puede recuperar detalles sobre por qué no se puede establecer algunos atributos.  
  
 Las aplicaciones no deben llamar directamente a esta función. Un controlador ODBC que admite la agrupación de conexiones dependientes del controlador debe implementar esta función.  
  
 Incluir sqlspi.h para el desarrollo de controladores ODBC.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un controlador ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Agrupación de conexiones dependientes del controlador](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Desarrollar el conocimiento de la agrupación de conexiones en un controlador ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
