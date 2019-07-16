---
title: Desconectando de datos de un origen o el controlador | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a01220b6a4f15ee3770b844f41e7ddc5399f5f86
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039762"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Desconectarse de datos de un origen o el controlador
Cuando una aplicación ha terminado de utilizar un origen de datos, llama a **SQLDisconnect**. **SQLDisconnect** libera las instrucciones que se asignan en la conexión y desconecta el controlador del origen de datos. Devuelve un error si una transacción está en proceso.  
  
 Después de desconectarse, puede llamar la aplicación **SQLFreeHandle** para liberar la conexión. Tras liberar la conexión, es un error de programación de aplicaciones para usar el identificador de la conexión en una llamada a una función ODBC; Si lo hace por lo que tiene consecuencias indefinidas, pero probablemente irrecuperables. Cuando **SQLFreeHandle** se llama, las versiones de controlador utiliza la estructura para almacenar información acerca de la conexión.  
  
 La aplicación también puede volver a usar la conexión, ya sea para conectarse a un origen de datos diferente o volver a conectarse al mismo origen de datos. La decisión de seguir conectado, en lugar de desconectarse y volver a conectarse más tarde, requiere que el autor de la aplicación, tenga en cuenta los costes relativos de cada opción; conectarse a un origen de datos tanto permanecen conectados pueden ser relativamente costosos dependiendo del medio de conexión. Realizar un equilibrio correcto, la aplicación también debe realizar suposiciones sobre la probabilidad y el momento de realizar más operaciones en el mismo origen de datos.
