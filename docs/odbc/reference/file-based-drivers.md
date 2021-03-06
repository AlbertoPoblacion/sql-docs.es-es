---
title: Controladores basados en archivo | Documentos de Microsoft
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
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9873f0b61364bd12bca0823ba66749513a4342c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="file-based-drivers"></a>Controladores basados en archivos
Se utilizan controladores basados en archivos con orígenes de datos como dBASE que no proporcionan un motor de base de datos independiente para el controlador que se utilizará. Estos controladores acceder directamente a los datos físicos y deben implementar un motor de base de datos para procesar instrucciones SQL. Como práctica estándar, los motores de base de datos en los controladores basados en archivos implementan el subconjunto de ODBC SQL definido por el nivel de conformidad mínima de SQL; Para obtener una lista de las instrucciones SQL en este nivel de conformidad, vea [Apéndice C: SQL gramática](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 En los controladores basados en DBMS y archivo de comparación, controladores basados en archivos son menos eficaces y más difícil de escribir por el componente del motor de base de datos, menos complicado configurar porque no hay ningún partes de la red, porque pocas personas tienen el tiempo para escribir en base de datos motores tan eficaces como los generados por las compañías de la base de datos.  
  
 En la siguiente ilustración muestra dos configuraciones distintas de controladores basados en archivos, uno en el que residen los datos localmente y el otro en el que reside en un servidor de archivos de red.  
  
 ![Dos configuraciones de archivo &#45; controladores basados en](../../odbc/reference/media/pr06.gif "pr06")
