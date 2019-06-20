---
title: 'C a SQL: Intervalos de tiempo del día | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb41d658637258c6d60b5adb4e0d7abb9ae81d91
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213413"
---
# <a name="c-to-sql-day-time-intervals"></a>C a SQL: Intervalos de día y hora
Los identificadores de los tipos de datos ODBC C de intervalo de día y hora son:  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 La siguiente tabla muestra los tipos de datos a la que se puede convertir el intervalo de datos C de ODBC SQL. Para obtener una explicación de las columnas y los términos de la tabla, vea [convertir datos de C a tipos de datos SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificador de tipo SQL|Prueba|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|Longitud de bytes de la columna > = longitud de bytes de caracteres<br /><br /> Longitud de bytes de la columna < [a] longitud de bytes de caracteres<br /><br /> Valor de datos no es un intervalo válido de literal|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|Longitud de caracteres de la columna > = longitud de caracteres de datos<br /><br /> Longitud de caracteres de la columna < caracteres de longitud de datos [a]<br /><br /> Valor de datos no es un intervalo válido de literal|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b] SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b] SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|Conversión de un intervalo de campo único no se ha producido un truncamiento de dígitos enteros<br /><br /> Conversión produjo un truncamiento de dígitos enteros|n/d<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Valor de datos se convirtió sin truncamiento de los campos<br /><br /> Uno o varios campos de valor de datos se puede truncar durante la conversión|n/d<br /><br /> 22015|  
  
 [a] tipos de datos interval todas C se pueden convertir a un tipo de datos de caracteres.  
  
 [b] si el campo tipo de la estructura de intervalo es tal que el intervalo es un único campo (SQL_DAY, SQL_HOUR, SQL_MINUTE o SQL_SECOND), se puede convertir el tipo C de intervalo en cualquier valor numérico exacto (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT SQL_DECIMAL o SQL_NUMERIC).  
  
 La conversión predeterminada de un tipo de intervalo C es el intervalo de hora del día correspondiente tipo SQL.  
  
 El controlador omite el valor de longitud/indicador al convertir los datos del tipo de datos C de intervalo y se da por supuesto que el tamaño del búfer de datos es el tamaño del tipo de datos C de intervalo. El valor de longitud/indicador se pasa en el *StrLen_or_Ind* argumento en **SQLPutData** y en el búfer especificado con el *StrLen_or_IndPtr* argumento en **SQLBindParameter**. El búfer de datos se especifica con el *DataPtr* argumento en **SQLPutData** y *ParameterValuePtr* argumento en **SQLBindParameter**.  
  
 El ejemplo siguiente muestra cómo enviar datos de intervalo C almacenados en la estructura SQL_INTERVAL_STRUCT en una columna de base de datos. La estructura de intervalo contiene un intervalo de DAY_TO_SECOND; se almacenarán en una columna de base de datos de tipo SQL_INTERVAL_DAY_TO_MINUTE.  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
