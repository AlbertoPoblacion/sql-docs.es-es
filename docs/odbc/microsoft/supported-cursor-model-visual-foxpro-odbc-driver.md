---
title: Admite el modelo de Cursor (controlador ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 875348a501c292e55b267ece769f16dd6bc9dbdd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270937"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Modelo de Cursor compatibles (el controlador ODBC de Visual FoxPro)
El controlador de Visual FoxPro ODBC admite tanto *bloque* (*conjunto de filas*) y *estático* cursores. Los cursores estáticos son compatibles con los controladores que se ajustan al cumplimiento de ODBC de nivel 1. El controlador no admite dinámicos, cursores controlados por o mixto (keyset y dynamic) cursores.  
  
 La aplicación puede llamar a [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) con una opción SQL_CURSOR_TYPE de SQL_CURSOR_FORWARD_ONLY (cursor de bloque) o SQL_CURSOR_STATIC (cursor estático).  
  
> [!NOTE]  
>  Si se llama a **SQLSetStmtOption** con una opción SQL_CURSOR_TYPE distinto SQL_CURSOR_FORWARD_ONLY o SQL_CURSOR_STATIC, la función devuelve SQL_SUCCESS_WITH_INFO con un valor de SQLSTATE de 01S02 de SQLState (valor de opción cambiado). El controlador establece todos los modos de cursor no compatible en SQL_CURSOR_STATIC.  
  
 Para obtener más información acerca de los tipos de cursor y aproximadamente **SQLSetStmtOption**, consulte el [referencia del programador de ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>cursor de bloque  
 Un conjunto de resultados de desplazamiento hacia delante, de solo lectura devuelto al cliente, quién es responsable de mantener el almacenamiento para los datos.  
  
## <a name="static-cursor"></a>cursor estático  
 Una instantánea de un conjunto de datos definido por la consulta. Los cursores estáticos no reflejan los cambios en tiempo real de los datos subyacentes otros usuarios. Búfer de memoria del cursor se mantiene mediante la biblioteca de cursores ODBC, lo que permite el desplazamiento hacia delante y hacia atrás.  
  
## <a name="rowset"></a>conjunto de filas  
 Bloques de datos almacenados en un cursor, que representa las filas se recuperan de un origen de datos.
