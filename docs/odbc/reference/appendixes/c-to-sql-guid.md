---
title: 'C a SQL: GUID | Documentos de Microsoft'
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
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a393aefa101bef2738e15ed12b0f1679e4a6c9c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-guid"></a>C a SQL: GUID
El identificador para el tipo de datos C de ODBC de GUID es:  
  
 SQL_C_GUID  
  
 La siguiente tabla muestra los tipos de datos a la que se pueden convertir datos GUID C de ODBC SQL. Para obtener una explicación de las columnas y los términos de la tabla, vea [convertir datos de C a tipos de datos de SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificador de tipo SQL|Prueba|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Longitud de bytes de la columna > = 36|n/d|  
|SQL_VARCHAR|Columna de longitud de bytes < 36|22001|  
|SQL_LONGVARCHAR|Valor de datos no es un GUID válido|22018|  
|SQL_WCHAR|Longitud de caracteres de la columna > = 36|n/d|  
|SQL_WVARCHAR|Columna de caracteres de longitud < 36|22001|  
|SQL_WLONGVARCHAR|Valor de datos no es un GUID válido|22018|  
|SQL_GUID|Ninguno [a]|n/d|  
  
 [a] todos los valores hexadecimales son válidos como un GUID.  
  
 El controlador omite el valor de longitud/indicador al convertir datos del tipo de datos GUID C y se da por supuesto que el tamaño del búfer de datos es el tamaño del tipo de datos GUID C. El valor de longitud/indicador se pasa en el *StrLen_or_Ind* argumento en **SQLPutData** y en el búfer especificado con el *StrLen_or_IndPtr* argumento en **SQLBindParameter**. El búfer de datos se especifica con el *DataPtr* argumento en **SQLPutData** y *ParameterValuePtr* argumento en **SQLBindParameter**.
