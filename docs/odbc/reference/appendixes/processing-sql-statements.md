---
title: Procesar instrucciones SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9452ade90f6967dff6d72d5692efcf91b93154d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057245"
---
# <a name="processing-sql-statements"></a>Procesamiento de instrucciones SQL
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite usar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad de cursor del controlador.  
  
 La biblioteca de cursores ODBC pasa todas las instrucciones SQL directamente en el controlador de excepción de los siguientes:  
  
-   Coloca la actualización y eliminación de instrucciones  
  
-   **SELECT FOR UPDATE** instrucciones  
  
-   Instrucciones SQL por lotes  
  
 Para ejecutar la actualización posicionada y eliminar las instrucciones y para colocar el cursor en una fila para llamar a **SQLGetData** para esa fila, la biblioteca de cursores construye una instrucción de búsqueda que identifica la fila.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Procesamiento de instrucciones posicionadas Update y Delete](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Procesamiento de instrucciones SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Procesamiento de lotes de instrucciones SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Construcción de instrucciones Searched](../../../odbc/reference/appendixes/constructing-searched-statements.md)
