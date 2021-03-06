---
title: Enlazar columnas para su uso con cursores de bloque | Documentos de Microsoft
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
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c527c2e89ab9acd0218a1b7f88112a81d537b780
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Enlazar columnas para su uso con cursores de bloque
Dado que los cursores de bloque devuelven varias filas, las aplicaciones que usan deben enlazar una matriz de variables a cada columna en lugar de una única variable. Estas matrices se conocen colectivamente como la *búferes de conjunto de filas*. Estos son los dos estilos de enlace:  
  
-   Enlazar una matriz para cada columna. Esto se denomina *el enlace* porque cada estructura de datos (matriz) contiene datos de una sola columna.  
  
-   Define una estructura para contener los datos para una fila completa y una matriz de estas estructuras de enlace. Esto se denomina *el enlace* porque cada estructura de datos contiene los datos de una sola fila.  
  
 Tal y como cuando la aplicación enlaza las variables solo a las columnas, se llama a **SQLBindCol** para enlazar las matrices a las columnas. La única diferencia es que las direcciones que se pasan son direcciones de matriz, no sola direcciones de variable. La aplicación establece el atributo de instrucción de SQL_BIND_BY_COLUMN para especificar si está utilizando enlace de modo de columna o de modo de fila. Si desea utilizar el enlace de modo de columna o de modo de fila es mayormente una cuestión de preferencia de la aplicación. El enlace puede corresponden más al diseño de la aplicación de los datos, en cuyo caso podría proporcionar un mejor rendimiento.  
  
 Esta sección contiene los temas siguientes.  
  
-   [El enlace](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [El enlace](../../../odbc/reference/develop-app/row-wise-binding.md)
