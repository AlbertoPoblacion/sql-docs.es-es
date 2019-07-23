---
ms.openlocfilehash: 78b372942de6ec62823dddecd08fdb7221cbe7a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68219685"
---


### <a name="index-stats-options"></a>Opciones de estadísticas de índice

<!--
This includes/paragraph-content/ file was created when processing vsts sqlbuvsts01 2999014 (5589131).  genemi  2017-07-21

Initially used in:
- relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md
- relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md
-->


En versiones anteriores de Microsoft SQL Server podría provocar la ralentización del sistema para reorganizar o recompilar un índice grande. En SQL Server 2016 se implementaron mejoras importantes de rendimiento para estas operaciones de índice.

Además, en versiones anteriores, la granularidad del control era menos restringida. Esto provocó que el sistema reorganizara o recompilara algunos índices incluso aunque no estuvieran muy fragmentados, algo que resultaba innecesario. Los últimos controles de la interfaz de usuario (UI) del plan de mantenimiento permiten excluir índices que no es necesario actualizar, en función de los criterios de las estadísticas de índice. Para ello, se usan internamente las siguientes vistas de administración dinámica (DMV) de Transact-SQL:


- [sys.dm_db_index_usage_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)
- [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)


 **Tipo de recorrido**  
 El sistema debe consumir recursos para recopilar estadísticas de índice. Puede elegir entre consumir menos o más recursos relativamente, en función de cuánta precisión considere necesaria para las estadísticas de índice. La interfaz de usuario ofrece la siguiente lista de niveles de precisión de entre los que debe elegir uno:


- Rápido
- Muestreado
- Detallado


 **Optimizar índice solo si:**  
 La interfaz de usuario ofrece los siguientes filtros ajustables que puede usar para evitar actualizar índices cuya actualización aún no es necesaria:


- Fragmentación &gt; *(%)*
- Recuento de páginas &gt;
- Usado en los últimos *(días)*

