---
title: Procedimientos almacenados compilados de forma nativa y opciones SET de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: eaf7057130cc3d13c0025b92b207efbace339e74
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2020
ms.locfileid: "63131480"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Procedimientos almacenados compilados de forma nativa y opciones SET de ejecución.
  Las opciones de sesión son fijas en los bloques atomic. La ejecución de un procedimiento almacenado no se ve afectada por las opciones SET de una sesión. Sin embargo, ciertas opciones SET, como SET NOEXEC y SET SHOWPLAN_XML, causan que no se ejecuten los procedimientos almacenados (incluidos los compilados de forma nativa).  
  
 Cuando un procedimiento almacenado de forma nativa se ejecuta con la opción STATISTICS activada, las estadísticas se obtienen para el procedimiento en su conjunto y no para cada instrucción. Para obtener más información, vea [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql) y [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql). Para obtener estadísticas de ejecución de nivel de instrucción para los procedimientos almacenados compilados de forma nativa, use una sesión de eventos extendidos en el evento sp_statement_completed, que se inicia cuando finaliza cada una de las consultas de una ejecución de procedimientos almacenados. Para obtener más información sobre cómo crear sesiones de eventos extendidos, vea [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).  
  
 `SHOWPLAN_XML` se admite para procedimientos almacenados compilados de forma nativa. `SHOWPLAN_ALL` y `SHOWPLAN_TEXT` no son compatibles con los procedimientos almacenados compilados de forma nativa.  
  
 `SET FMTONLY` no es compatible con los procedimientos almacenados compilados de forma nativa. Use en su lugar [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).  
  
## <a name="see-also"></a>Consulte también  
 [Procedimientos almacenados compilados de forma nativa](natively-compiled-stored-procedures.md)  
  
  
