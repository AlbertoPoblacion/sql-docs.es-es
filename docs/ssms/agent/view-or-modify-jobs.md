---
title: Ver o modificar trabajos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2d6090349f52fbfebedfbb336b23ca11f462b81e
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67680612"
---
# <a name="view-or-modify-jobs"></a>Ver o modificar trabajos
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

Puede ver cualquier trabajo que haya creado. Asimismo, después de ejecutar un trabajo, puede ver su historial. El historial de un trabajo le permite ver cuándo se ejecutó el trabajo, el estado del trabajo en conjunto y el estado de cada paso del trabajo. Puede ver si el trabajo ha tenido algún error en el pasado, cuándo finalizó correctamente por última vez y qué salida ha creado el trabajo cada vez que se ha ejecutado. Los miembros del rol fijo de servidor **sysadmin** pueden ver o modificar cualquier trabajo, con independencia de quién sea el propietario.  
  
> [!NOTE]  
> Para que exista un historial de trabajos, éste debe haberse ejecutado al menos una vez. Puede limitar el tamaño total del registro de historial de trabajos y el tamaño por trabajo.  
  
Por último, puede modificar un trabajo para satisfacer nuevos requisitos. Puede modificar:  
  
-   Opciones de respuesta  
  
-   Programaciones  
  
-   Pasos de trabajo  
  
-   Propiedad  
  
-   Categoría de trabajo  
  
-   Servidores de destino (solo para trabajos multiservidor)  
  
Para asegurarse de que los cambios en los trabajos multiservidor surten efecto, debe exponer los cambios en la lista de descarga con el fin de que los servidores de destino puedan descargar el trabajo actualizado. Para asegurarse de que los servidores de destino tienen las definiciones de trabajos más actuales, exponga una instrucción INSERT después de actualizar el trabajo multiservidor, de la forma siguiente:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Para más información, consulte [sp_purge_jobhistory (Transact-SQL)](https://msdn.microsoft.com/237f9bad-636d-4262-9bfb-66c034a43e88).  
  
Los miembros del rol fijo de servidor **sysadmin** pueden ver la definición o el historial de cualquier trabajo, y pueden modificar cualquier trabajo.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descripción**|**Tema**|  
|Describe cómo ver trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[View a Job](../../ssms/agent/view-a-job.md)|  
|Describe cómo ver el registro del historial de trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[View the Job History](../../ssms/agent/view-the-job-history.md)|  
|Describe cómo eliminar el contenido del registro del historial de trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Clear the Job History Log](../../ssms/agent/clear-the-job-history-log.md)|  
|Describe cómo establecer límites de tamaño para los registros de historial de trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Resize the Job History Log](../../ssms/agent/resize-the-job-history-log.md)|  
|Describe cómo cambiar las propiedades de los trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Modify a Job](../../ssms/agent/modify-a-job.md)|  
  
## <a name="see-also"></a>Consulte también  
[sysjobhistory](../../relational-databases/system-tables/dbo-sysjobhistory-transact-sql.md)  
  
