---
title: Admite los tipos de datos (controlador ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2d23ddc5fdd00db45aee235e96f13a8cf08082a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080782"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Tipos de datos admitidos (controlador ODBC de Visual FoxPro)
La lista de tipos de datos admitidos por el controlador se presentan a través de la API de ODBC y Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Tipos de datos en aplicaciones de C  
 Puede obtener una lista de tipos de datos admitidos por el controlador ODBC de Visual FoxPro utilizando el [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) función en las aplicaciones de C o C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Tipos de datos en las aplicaciones que usan Microsoft Query  
 Si la aplicación utiliza Microsoft Query para crear una nueva tabla en un origen de datos de Visual FoxPro, Microsoft Query muestra el **nueva definición de tabla** cuadro de diálogo. En **descripción del campo**, **tipo** cuadro listas [tipos de datos de campo Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), representado por caracteres individuales.
