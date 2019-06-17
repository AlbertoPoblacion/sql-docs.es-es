---
title: Conectarse a un origen de datos (controlador ODBC para Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: adee8d8dd8d6db0d79b37ff853c41e7604fe21de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63302126"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Conectarse a un origen de datos (controlador ODBC para Oracle)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. En su lugar, use el controlador ODBC proporcionado por Oracle.  
  
 Una aplicación ODBC puede pasar información de conexión en varios aspectos. Por ejemplo, la aplicación podría tener el controlador siempre solicitarán al usuario información de conexión. O puede esperar a la aplicación de una cadena de conexión que especifica la conexión de origen de datos. Cómo conectarse a un origen de datos depende de la aplicación ODBC usado el método de conexión.  
  
 Es una forma habitual para conectarse a un origen de datos a través del cuadro de diálogo origen de datos. Si la aplicación ODBC se ha configurado para usar un cuadro de diálogo, cuadro de diálogo se muestra y le pide la información de conexión del origen de datos adecuado.  
  
 También puede conectarse a un origen de datos mediante el [cadena de conexión](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Para conectarse a un origen de datos mediante un cuadro de diálogo  
  
1.  Cuando aparezca el cuadro de diálogo origen de datos, seleccione un origen de datos de Oracle y, a continuación, haga clic en Aceptar. Aparece el cuadro de diálogo Conectar.  
  
2.  Rellene la información apropiada para el cuadro de diálogo Conectar y, a continuación, haga clic en Aceptar.  
  
 Después de la conexión se comprueba información, la aplicación puede utilizar el controlador ODBC para Oracle para obtener acceso a la información que contiene el origen de datos.
