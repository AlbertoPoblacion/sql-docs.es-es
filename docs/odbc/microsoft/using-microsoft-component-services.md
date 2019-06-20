---
title: Uso de servicios de componentes de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71c78c6879645fd4f323ca79a7f77911350810c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62632917"
---
# <a name="using-microsoft-component-services"></a>Uso de servicios de componentes de Microsoft
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. En su lugar, use el controlador ODBC proporcionado por Oracle.  
  
 Puede habilitar una base de datos de Oracle trabajar con servicios de componentes transaccionales (o MTS, si está utilizando Windows NT) en Microsoft Windows NT o Windows 2000 y Microsoft Windows 95 ó 98. Para habilitar una base de datos de Oracle trabajar con servicios de componentes que admiten transacciones, los administradores del sistema deben crear una vista denominada V$ XATRANS$. Para crear esta secuencia de comandos, debe ejecutar un script de Oracle. Para obtener más información, consulte la Ayuda de servicios de componente o la documentación de Oracle.
