---
title: Subclaves de la especificación del origen de datos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad210f91d00f9e692c8ee20fef01a808a01501c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198208"
---
# <a name="data-source-specification-subkeys"></a>Subclaves de la especificación del origen de datos
Cada origen de datos aparece en la subclave de orígenes de datos ODBC tiene una subclave de su propio. Esta subclave tiene el mismo nombre que el valor correspondiente en la subclave de orígenes de datos ODBC. Los valores en esta subclave deben mostrar la DLL del controlador y pueden enumerar una descripción del origen de datos. Si el controlador admite traductores, los valores pueden enumerar el nombre de un traductor de forma predeterminada, el archivo DLL de traducción predeterminado y la opción de traducción predeterminado. Los valores también pueden mostrar otra información requerida por el controlador para conectarse al origen de datos. Por ejemplo, el controlador podría requerir un nombre del servidor, el nombre de base de datos o el nombre de esquema.  
  
 Los formatos de los valores son como se muestra en la tabla siguiente. Solo el valor de controlador es obligatorio.  
  
|Nombre|Tipo de datos|Datos|  
|----------|---------------|----------|  
|Descripción|REG_SZ|*description*|  
|Controlador|REG_SZ|*driver-DLL-path*|  
|TranslationDLL|REG_SZ|*translator-DLL-path*|  
|TranslationName|REG_SZ|*translator-name*|  
|TranslationOption|REG_SZ|*translation-option*|  
|*opt-value-name*|*opt-value-type*|*opt-value-data*|  
  
 Por ejemplo, suponga que el controlador de SQL Server requiere el nombre del servidor y una marca para OEM a la conversión de ANSI y define los valores de servidor y OEMTOANSI para estos. Supongamos también que el origen de datos de inventario usa la página de código de Microsoft® Translator para traducir entre las páginas de código de multilingüe (850) y Windows® Latín 1 (1250). Los valores bajo la subclave de inventario podrían ser como sigue:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
