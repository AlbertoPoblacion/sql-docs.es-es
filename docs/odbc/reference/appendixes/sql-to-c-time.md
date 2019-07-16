---
title: 'SQL a C: Tiempo | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 99f8219ef53f72b0d7ab1477bba5d24d441a3141
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065083"
---
# <a name="sql-to-c-time"></a>SQL a C: Time
El identificador de la hora es de tipo de datos SQL de ODBC:  
  
 SQL_TYPE_TIME  
  
 La siguiente tabla muestra los tipos de datos a la que se pueden convertir los datos en tiempo de SQL de la C de ODBC. Para obtener una explicación de las columnas y los términos de la tabla, vea [convertir datos de SQL a tipos de datos C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificador de tipo de C|Prueba|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longitud de bytes de caracteres<br /><br /> *9* <= *BufferLength* < = longitud de bytes de caracteres<br /><br /> *BufferLength* < 9|Datos<br /><br /> Datos truncados [a]<br /><br /> No definido|Longitud de datos en bytes<br /><br /> Longitud de datos en bytes<br /><br /> No definido|N/D<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longitud de caracteres<br /><br /> *9* <= *BufferLength* < = longitud de caracteres<br /><br /> *BufferLength* < 9|Datos<br /><br /> Datos truncados [a]<br /><br /> No definido|Longitud de datos de caracteres<br /><br /> Longitud de datos de caracteres<br /><br /> No definido|N/D<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longitud de bytes de datos < = *BufferLength*<br /><br /> Longitud de bytes de datos > *BufferLength*|Datos<br /><br /> No definido|Longitud de datos en bytes<br /><br /> No definido|N/D<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Ninguno [b]|Datos|6[d]|N/D|  
|SQL_C_TYPE_TIMESTAMP|Ninguno [b]|Datos [c]|16 [d]|N/D|  
  
 [a] se truncan las fracciones de segundos del tiempo.  
  
 [b] el valor de *BufferLength* se omite para esta conversión. El controlador se da por supuesto que el tamaño de **TargetValuePtr* es el tamaño del tipo de datos C.  
  
 [c] los campos de fecha de la estructura de marca de tiempo se establecen en la fecha actual y el campo de fracciones de segundos de la estructura de marca de tiempo se establece en cero.  
  
 [d] se trata el tamaño del tipo de datos C correspondiente.  
  
 Cuando los datos de SQL de tiempo se convierte en datos de caracteres de C, la cadena resultante tiene el "*hh*:*mm*:*ss*" formato. Este formato no se ve afectado por la configuración de país Windows®.
