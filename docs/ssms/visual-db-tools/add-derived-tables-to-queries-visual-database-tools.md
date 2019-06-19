---
title: Agregar tablas derivadas a las consultas (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4911b633fb6dcb2b40dc6d22828c0af53b0d2bda
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65088764"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>Agregar tablas derivadas a las consultas (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Las tablas derivadas son conjuntos de resultados que se utilizan como orígenes de tabla en una consulta. Puede agregar una tabla derivada a una consulta en el **panel Diagrama**.  
  
### <a name="to-add-a-derived-table-to-a-query"></a>Para agregar una tabla derivada a una consulta  
  
1.  Abra una consulta existente o cree una nueva.  
  
2.  Haga clic con el botón derecho en el **panel Diagrama** y elija **Agregar nueva tabla derivada**.  
  
    Se agrega una nueva tabla con el nombre derivedtbl_*N* y la instrucción SELECT de la tabla derivada se agrega a la cláusula FROM de la consulta.  
  
## <a name="see-also"></a>Consulte también  
[Realizar operaciones básicas con consultas (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[Crear consultas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[Abrir consultas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-queries-visual-database-tools.md)  
[SELECT (Transact-SQL)](https://msdn.microsoft.com/dc85caea-54d1-49af-b166-f3aa2f3a93d0)  
  
