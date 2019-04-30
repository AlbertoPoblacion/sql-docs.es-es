---
title: Invocación del procedimiento | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b33bc399646a6d274c875abd36d53219a2814e1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200519"
---
# <a name="procedure-invocation"></a>Invocación del procedimiento
Cuando se usa el controlador de Microsoft Access, los procedimientos se pueden invocar desde el controlador mediante la **SQLExecDirect** o **SQLPrepare** función con la sintaxis siguiente: {llamar *nombre del procedimiento*  [(*parámetro*[,*parámetro*]...)]}. Tenga en cuenta que no se admiten expresiones como parámetros a un procedimiento llamado.  
  
 Si un nombre de procedimiento incluye un guión, el nombre debe delimitarse con comillas atrás (').  
  
 Puede llamar a una consulta con parámetros mediante la instrucción anterior.
