---
title: Enlazar columnas | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a634a553672b83931091056dd489f7559c4269b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106215"
---
# <a name="binding-columns"></a>Enlazar columnas
Datos capturados desde el origen de datos se devuelven a la aplicación en las variables que ha asignado la aplicación para este propósito. Antes de ello, debe asociar la aplicación, o *enlazar*, establecen estas variables a las columnas del resultado; conceptualmente, este proceso es el mismo que el enlace de variables de aplicación para los parámetros de la instrucción. Cuando la aplicación enlaza una variable a una columna del conjunto de resultados, describe esa variable - dirección, tipo de datos etc. - al controlador. El controlador almacena esta información en la estructura se mantiene para esa instrucción y usa la información para devolver el valor de la columna cuando se captura la fila.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Columnas del conjunto de resultados de enlace](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Uso de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
