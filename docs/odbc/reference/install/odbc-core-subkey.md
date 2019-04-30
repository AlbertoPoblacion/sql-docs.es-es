---
title: Subclave de ODBC Core | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c95c4e28a5f32131307daeaa61e214af887b577
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63069709"
---
# <a name="odbc-core-subkey"></a>Subclave de ODBC Core
El valor bajo la subclave de ODBC Core ofrece el recuento de utilización de los componentes principales (Administrador de controladores, biblioteca de cursores, installer, DLL etc.). El formato de este valor se muestra en la tabla siguiente.  
  
|Name|Tipo de datos|Datos|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*Recuento*|  
  
 Por ejemplo, supongamos que se han instalado los componentes principales de ODBC mediante los programas de instalación para tres aplicaciones diferentes y dos controladores diferentes. El valor bajo la subclave de ODBC Core sería:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
