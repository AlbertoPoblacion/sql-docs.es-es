---
title: SQLColAttributes (controlador de acceso) | Documentos de Microsoft
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
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: de4d676a7e0f1f56c2803225986e592860a00e5c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (controlador de Access)
> [!NOTE]  
>  En este tema se proporciona información específica del controlador de acceso. Para obtener información general acerca de esta función, vea el tema correspondiente en [referencia de la API de ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribute|Comentarios|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Para los datos LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE es la longitud máxima de la columna, no la longitud máxima de la columna horas 2.|  
|SQL_OWNER_NAME|Una cadena vacía ("") se devuelve en esta columna porque no se admite el nombre del propietario.|  
|SQL_QUALIFIER_NAME|Se devuelve la ruta de acceso a un archivo de base de datos.|  
|SQL_COLUMN_SEARCHABLE|Columnas LONGVARBINARY y LONGVARCHAR se notifican como SQL_UNSEARCHABLE.<br /><br /> Tipos de datos de caracteres y binarios de longitud fija y de longitud variable son permite realizar búsquedos, aunque no sean LONGVARBINARY y LONGVARCHAR.|  
  
> [!NOTE]  
>  Los pasos anteriores no es una lista completa de los atributos devueltos por **SQLColAttributes**.
