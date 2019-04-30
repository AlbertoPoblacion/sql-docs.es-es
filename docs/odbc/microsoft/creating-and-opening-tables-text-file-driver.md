---
title: Crear y abrir tablas (controlador de archivo de texto) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce901e6a8639c8a2caea6e55cbaa18fedb56f4a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63132725"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Crear y abrir tablas (controlador de archivo de texto)
Cuando se usa el controlador de texto, se crea una nueva tabla con el formato especificado en Odbcinst.ini. Si no se especifica, se crean tablas en formato CSVDELIMITED. De forma predeterminada, las columnas de enteros predeterminado a 11 caracteres y columnas de punto flotante como valor predeterminado 22 caracteres. Columnas de fecha y utilice el formato aaaa-MM-DD. CHAR y columnas LONGCHAR son el ancho especificado en la instrucción CREATE.
