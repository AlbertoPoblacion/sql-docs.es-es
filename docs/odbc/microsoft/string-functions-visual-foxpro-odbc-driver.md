---
title: Funciones (controlador ODBC de Visual FoxPro) de cadena | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db1fbaffbee0f74625f4a11cad3b961f194e3829
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948774"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Funciones de cadena (el controlador ODBC de Visual FoxPro)
En la tabla siguiente se muestra funciones de manipulación de cadena ODBC compatibles con el controlador ODBC de Visual FoxPro; Cuando la gramática de Visual FoxPro para la misma función difiere de la sintaxis ODBC, se muestra el equivalente de Visual FoxPro.  
  
|Gramática ODBC|Gramática Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(código)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|DIFERENCIA *(string_exp1, string_exp2)*||  
|Insertar *(string_exp1, inicio, longitud, string_exp2)*|MATERIAL *(string_exp1, inicio, longitud, string_exp2)*|  
|LCASE *(string_exp)*|INFERIOR *(string_exp)*|  
|IZQUIERDA *(string_exp, recuento)*||  
|LENGTH *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|Repita *(string_exp, recuento)*|REPLICAR *(string_exp, recuento)*|  
|Reemplace *(string_exp1, string_exp2, string_exp3)*|STRTRAN *(string_exp1, string_exp2, string_exp3)*|  
|DERECHA *(string_exp, recuento)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|ESPACIO *(recuento)*||  
|SUBCADENA *(string_exp, inicio, longitud)*|SUBSTR *(string_exp, inicio, longitud)*|  
|UCASE *(string_exp)*|SUPERIOR *(string_exp)*|
