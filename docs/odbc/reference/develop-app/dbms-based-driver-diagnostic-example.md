---
title: Ejemplo de diagnóstico de controlador basados en DBMS | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef42fe2ab881a7e24d680e0dd941cbea0d95488f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076894"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Ejemplo de diagnóstico de controladores basados en DBMS
Un controlador basados en DBMS envía solicitudes a un DBMS y devuelve información a la aplicación mediante el Administrador de controladores. Dado que el controlador es el componente que interactúa con el Administrador de controladores, da formato y devuelve los argumentos para **SQLGetDiagRec**.  
  
 Por ejemplo, si usa SQL, servicios y un controlador de Microsoft para Oracle Rdb ha encontrado un nombre de cursor no válido, podrían devolver los valores siguientes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Porque se produjo el error en el controlador, agregar los prefijos para el mensaje de diagnóstico para el proveedor ([Microsoft]) y el controlador ([controlador ODBC de Rdb]).  
  
 Si el DBMS no encontró la tabla EMPLOYEE, el controlador podría dar formato y devolver los valores siguientes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Porque se produjo el error en el origen de datos, el controlador agrega un prefijo para el identificador de origen de datos ([Rdb]) para el mensaje de diagnóstico. Debido a que el controlador era el componente que se relacionó con el origen de datos, agregar los prefijos de su proveedor ([Microsoft]) e identificador ([controlador ODBC de Rdb]) para el mensaje de diagnóstico.
