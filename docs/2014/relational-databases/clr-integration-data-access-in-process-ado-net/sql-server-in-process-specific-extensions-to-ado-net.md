---
title: SQL Server extensiones específicas en proceso a ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 98781a7258a4fa70f9f8c70c37140445af5bcb76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874712"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Extensiones específicas en proceso de SQL Server a ADO.NET
  Hay cuatro extensiones funcionales principales a ADO.NET que son específicamente para el uso en proceso. En los siguientes temas se tratan estas extensiones en detalle.  
  
## <a name="in-this-section"></a>En esta sección  
 [Objeto SqlContext](sqlcontext-object.md)  
 Esta clase proporciona acceso a las demás extensiones abstrayendo el contexto de llamador de una rutina de SQL Server que ejecuta el código administrado en proceso.  
  
 [SqlPipe, objetos](sqlpipe-object.md)  
 Esta clase contiene rutinas para enviar resultados tabulares y mensajes al cliente.  
  
 [Objeto SqlTriggerContext](sqltriggercontext-object.md)  
 Esta clase proporciona información sobre el contexto en el que se ejecuta un desencadenador.  
  
 [SqlDataRecord, objeto](sqldatarecord-object.md)  
 La clase SqlDataRecord representa una única fila de datos, junto con sus metadatos relacionados, y permite que los procedimientos almacenados devuelvan al cliente conjuntos de resultados personalizados.  
  
  
