---
title: "Ubicación de caché | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8d2c2083175bcccf1fba0157bcdf30c8b83af81
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="location-of-cache"></a>Ubicación de caché
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad del controlador cursor.  
  
 La biblioteca de cursores se almacena en memoria caché los datos en memoria y en los archivos temporales de Windows®. Esto limita el tamaño del conjunto de resultados que puede controlar la biblioteca de cursores solo por espacio en disco disponible. Un archivo temporal se usa cuando los datos que se va a almacenar en caché cruzan el límite de segmento si se insertan al final de la caché de la biblioteca de cursores. En su lugar, se agregan los datos en la memoria caché en lugar del bloque de última de datos en la memoria caché. El bloque de datos guardados en último se guarda en un archivo temporal. Si la biblioteca de cursores se finaliza correctamente, por ejemplo, cuando se produce un error en la potencia, pueden dejar archivos temporales de Windows en el disco. Se denominan ~ CTT*nnnn*tmp y se crean en el directorio actual.  
  
> [!NOTE]  
>  Si trata de la biblioteca de cursores en Microsoft® WindowsNT®/Windows 2000 en caché los datos en un archivo temporal en el directorio actual mientras se ejecuta la aplicación desde un recurso compartido de solo lectura o un disco compacto (por ejemplo, un ejemplo de biblioteca Microsoft Foundation Class), SQLSTATE HY000 (General Error-Unable crear un búfer de archivo) se devolverá.
