---
title: Extraer un script de un seguimiento (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5cab84931db11e91e474ffd38aecfa4fb2aafae4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62712462"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>Extraer un script de un seguimiento (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  En este tema se describe cómo extraer eventos de [!INCLUDE[tsql](../../includes/tsql-md.md)] de una tabla o archivo de seguimiento y guardarlos como archivo de script de [!INCLUDE[tsql](../../includes/tsql-md.md)] mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Para extraer un script de Transact-SQL de una tabla o archivo de seguimiento  
  
1.  Abra la tabla o archivo de seguimiento que contiene los eventos de [!INCLUDE[tsql](../../includes/tsql-md.md)] que desea guardar en un archivo de script de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Para obtener más información, vea [Abrir un archivo de seguimiento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) o el Asistente para la optimización del [Abrir una tabla de seguimiento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
2.  En el menú **Archivo**, seleccione **Exportar**, **Extraer eventos de SQL Server** y, luego, haga clic en **Extraer eventos de Transact-SQL**.  
  
3.  En el cuadro de diálogo **Guardar como** , escriba un nombre para el archivo de [!INCLUDE[tsql](../../includes/tsql-md.md)] y haga clic en **Guardar**.  
  
## <a name="see-also"></a>Consulte también  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
