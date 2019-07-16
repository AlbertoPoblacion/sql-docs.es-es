---
title: SQLSetPos (biblioteca de cursores) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87ff006e7bead36c2aa6476b99552d1524c213b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091715"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (biblioteca de cursores)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite usar esta característica en nuevos trabajos de desarrollo y piense en modificar las aplicaciones que actualmente utilizan esta característica. Microsoft recomienda usar la funcionalidad de cursor del controlador.  
  
 Este tema describe el uso de la **SQLSetPos** función en la biblioteca de cursores. Para obtener información general sobre **SQLSetPos**, consulte [función SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 La biblioteca de cursores es compatible con la operación SQL_POSITION solo para el *operación* argumento en **SQLSetPos**. Es compatible con el valor SQL_LOCK_NO_CHANGE solo para el *LockType* argumento.  
  
 Si el controlador no admite operaciones masivas, la biblioteca de cursores devuelve SQLSTATE HYC00 (no compatible con el controlador) cuando **SQLSetPos** se llama con *RowNumber* igual a 0. No se recomienda este comportamiento del controlador.  
  
 La biblioteca de cursores no admite las operaciones de SQL_UPDATE y SQL_DELETE en una llamada a **SQLSetPos**. Implementa la biblioteca de cursores una posición instrucción update o delete SQL mediante la creación de una búsqueda instrucción update o delete con una cláusula WHERE que enumera los valores almacenados en su memoria caché para cada columna enlazada. Para obtener más información, consulte [procesar actualización coloca y eliminar instrucciones](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Si el controlador no es compatible con los cursores estáticos, debe llamar una aplicación que funciona con la biblioteca de cursores **SQLSetPos** sólo en un conjunto de filas capturado por **SQLExtendedFetch** o **SQLFetchScroll** , no por **SQLFetch**. La biblioteca de cursores implementa **SQLExtendedFetch** y **SQLFetchScroll** mediante la realización de llamadas repetidas de **SQLFetch** (con un tamaño de conjunto de filas de 1) en el controlador. La biblioteca de cursores pasa las llamadas a **SQLFetch**, en la otra entrega, a través del controlador. Si **SQLSetPos** se llama en un conjunto de filas afectada capturado por **SQLFetch** cuando el controlador no es compatible con los cursores estáticos, la llamada se producirá un error porque **SQLSetPos** no funciona con cursores de solo avance. Esto sucederá incluso si una aplicación ha llamado correctamente **SQLSetStmtAttr** establecer SQL_ATTR_CURSOR_TYPE en SQL_CURSOR_STATIC, que la biblioteca de cursores admite incluso si el controlador no es compatible con los cursores estáticos.
