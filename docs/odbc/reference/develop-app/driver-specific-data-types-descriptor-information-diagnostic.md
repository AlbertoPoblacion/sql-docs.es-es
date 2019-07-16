---
title: 'Diagnóstico de Descriptor de acceso, información, tipos específicos del controlador: Data, | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa17a5552855916798c78e0e7d371b58e58a401e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046923"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Tipos de datos específicos del controlador, Descriptor tipos, tipos de información, tipos de diagnóstico y atributos
Los controladores pueden asignar valores específicos del controlador para lo siguiente:  
  
-   **Indicadores de tipo de datos de SQL** se usan en *ParameterType* en **SQLBindParameter** y en *DataType* en **SQLGetTypeInfo** y devuelto por **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**,  **SQLDescribeParam**, **SQLProcedureColumns**, y **SQLSpecialColumns**.  
  
-   **Los campos de descriptor** se usan en *FieldIdentifier* en **SQLColAttribute**, **SQLGetDescField**, y **SQLSetDescField**.  
  
-   **Los campos de diagnóstico** se usan en *DiagIdentifier* en **SQLGetDiagField** y **SQLGetDiagRec**.  
  
-   **Tipos de información** se usan en *InfoType* en **SQLGetInfo**.  
  
-   **Conexión y los atributos de instrucción** se usan en *atributo* en **SQLGetConnectAttr**, **SQLGetStmtAttr**,  **SQLSetConnectAttr**, y **SQLSetStmtAttr**.  
  
 Para cada uno de estos elementos, hay dos conjuntos de valores: valores reservados para su uso en ODBC y valores de reservado para uso de controladores. Antes de implementar los valores específicos del controlador, un escritor de controlador debe solicitar un valor para cada tipo específico del controlador, campo o atributo de Open Group. Para el desarrollo de controlador nuevo, use el intervalo que se describe en la tabla siguiente. El Administrador de ODBC 3.8 controladores no generará un error si se usa un valor desconocido que no está en el intervalo que se describe a continuación. Sin embargo, las versiones posteriores del Administrador de controladores podrían generarse un error si no se reciben que no están en el intervalo de valores desconocidos.  
  
 Cuando cualquiera de estos valores se pasan a una función ODBC, el controlador debe comprobar si el valor es válido. Controladores devuelven SQLSTATE HYC00 (característica opcional no implementada) para valores específicos del controlador que se aplican a otros controladores.  
  
 A partir de ODBC 3.8, escritores de controlador pueden asignar atributos específicos del controlador dentro de un intervalo reservado.  
  
> [!NOTE]  
>  El Administrador de ODBC 3.8 controladores no valida ni aplica estos intervalos para la compatibilidad con versiones anteriores. Una versión futura del Administrador de controladores puede aplicarlas, sin embargo.  
  
|Tipo de atributo|Tipo de datos de ODBC|Rango específicos del controlador base|Límite de rango específicos del controlador|Constante ODBC para el intervalo de valor específico del controlador base|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|Indicadores de tipo de datos SQL|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Campos de descriptor|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Campos de diagnóstico|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Tipos de información|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Atributos de conexión|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Atributos de instrucción|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Tipos de datos específicos del controlador, los campos de descriptor, los campos de diagnóstico, tipos de información, los atributos de instrucción y los atributos de conexión se deben describir en la documentación del controlador. Cuando cualquiera de estos valores se pasan a una función ODBC, el controlador debe comprobar si el valor es válido. Controladores devuelven SQLSTATE HYC00 (característica opcional no implementada) para valores específicos del controlador que se aplican a otros controladores.  
  
 Los valores bases se definen para facilitar el desarrollo de controladores. Por ejemplo, se pueden definir los atributos de diagnóstico específica de controladores en el formato siguiente:  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
