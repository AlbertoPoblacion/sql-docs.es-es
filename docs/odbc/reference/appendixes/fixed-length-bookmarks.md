---
title: Marcadores de longitud fija | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21af6ef1be21e000d25582151650f274fe3561a4
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793371"
---
# <a name="fixed-length-bookmarks"></a>Marcadores de longitud fija
Si un ODBC *3.x* controlador debería funcionar con un ODBC *2.x* aplicación que usa marcadores de longitud fija, el controlador deben admitir lo siguiente:  
  
-   SQL_UB_ON como un valor para la opción de instrucción SQL_USE_BOOKMARKS. (SQL_UB_ON está en desuso en ODBC *3.x*.)  
  
-   La opción de instrucción SQL_GET_BOOKMARK.
