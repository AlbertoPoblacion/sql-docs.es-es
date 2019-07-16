---
title: Estado de solo lectura (controlador de Excel) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 39f9d2e7ba40ba067659a86f45d2006c83594f3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988043"
---
# <a name="read-only-status-excel-driver"></a>Estado de solo lectura (controlador de Excel)
Cuando se usa el controlador de Microsoft Excel, las tablas de origen de datos se abren como de solo lectura de forma predeterminada y se pueden abrir con sólo un usuario a la vez. Aunque las tablas tienen el estado de solo lectura, sin embargo, las aplicaciones pueden realizar las inserciones y actualizaciones para las tablas de Microsoft Excel.  
  
 Cuando una aplicación realiza un comando Guardar como en los datos de Microsoft Excel a través del controlador de Microsoft Excel, la aplicación debe crear una nueva tabla e insertar los datos se guarden en la nueva tabla. Inserciones como resultado de anexar a la tabla. Ninguna otra operación puede realizarse en la tabla hasta que se cierra y vuelve a abrir. Una vez que se cierra la tabla, no se puede realizar ninguna inserción posteriores porque la tabla, a continuación, es una tabla de solo lectura.  
  
 Es posible actualizar los valores cuando se usa el controlador de Microsoft Excel, pero no se puede eliminar una fila de una tabla basada en una hoja de cálculo de Microsoft Excel, por lo que las actualizaciones no se consideran compatibles oficialmente con el controlador de Microsoft Excel.
