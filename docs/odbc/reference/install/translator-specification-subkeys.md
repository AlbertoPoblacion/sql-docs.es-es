---
title: "Traductor especificación subclaves | Documentos de Microsoft"
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
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86ba311eb458c1128a611b6d1cc2ed1c71329d3f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="translator-specification-subkeys"></a>Subclaves de la especificación de traductor
Cada traductor aparece en la subclave de traductores de ODBC tiene una subclave de su propio. Esta subclave tiene el mismo nombre que el valor correspondiente en la subclave de traductores de ODBC. Los valores bajo esta subclave enumeran las rutas de acceso completas del traductor, el programa de instalación de traductor archivos DLL y el contador de uso. Los formatos de los valores son como se muestra en la tabla siguiente.  
  
|Nombre|Tipo de datos|data|  
|----------|---------------|----------|  
|Traductor|REG_SZ|*ruta de la DLL de traductor*|  
|ssNoVersion|REG_SZ|*el programa de instalación-DLL-path*|  
|UsageCount|REG_DWORD|*Recuento*|  
  
 Para obtener información sobre recuentos de uso, consulte [recuento de uso](../../../odbc/reference/install/usage-counting.md) anteriormente en esta sección.  
  
 Las aplicaciones no deben establecer el recuento de uso. ODBC mantendrá este número.  
  
 Por ejemplo, suponga que el traductor de páginas de código de Microsoft tiene una traducción de archivo DLL denominado Mscpxl32.dll, que las funciones de traductor el programa de instalación están en el mismo archivo DLL, y que se ha instalado el traductor de tres veces. Los valores bajo la subclave de traductor de páginas de código de Microsoft podrían ser el siguiente:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
