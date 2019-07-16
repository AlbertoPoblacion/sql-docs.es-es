---
title: Los registros de diagnóstico | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 90133b4a18876c52b9b6b6bffbe4c8c02c953e07
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039882"
---
# <a name="diagnostic-records"></a>Registros de diagnóstico
Asociado con cada entorno, conexión, la instrucción y el identificador de descriptor son *los registros de diagnóstico*. Estos registros contienen información de diagnóstico sobre la última función denominada que usa un identificador determinado. Se reemplazan los registros solo cuando se llama a otra función con el mismo identificador. No hay ningún límite al número de registros de diagnóstico que se pueden almacenar en cualquier momento.  
  
 Hay dos tipos de registros de diagnóstico: una *registro de encabezado* y cero o más *registros de estado*. El registro de encabezado es 0; los registros de estado son registros 1 y versiones posteriores. Los registros de diagnóstico están formados por un número de campos independientes, que son diferentes para el registro de encabezado y los registros de estado. Además, los componentes de ODBC pueden definir sus propios campos de registro de diagnóstico.  
  
 Aunque los registros de diagnóstico pueden considerarse como estructuras, no hay ningún requisito para que sean realmente estructuras; cómo un controlador almacena la información de diagnóstico es específica del controlador.  
  
 Campos de registros de diagnóstico se recuperan con **SQLGetDiagField**. Los campos de mensaje de diagnóstico de registros de estado, número de error nativo y SQLSTATE se pueden recuperar en una sola llamada con **SQLGetDiagRec**.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Registro de encabezado](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Registros de estado](../../../odbc/reference/develop-app/status-records.md)
