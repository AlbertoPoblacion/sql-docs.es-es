---
title: Asignar a otros usuarios la propiedad de un trabajo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1516bb84fbfe733ba9d37838d945ef2f88019d76
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262408"
---
# <a name="give-others-ownership-of-a-job"></a>Give Others Ownership of a Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

En este tema se describe cómo volver a asignar a otro usuario la propiedad de los trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Antes de empezar:**  [Limitaciones y restricciones](#Restrictions), [Seguridad](#Security)  
  
-   **Para asignar a otros usuarios la propiedad de un trabajo, utilizando:**  
  
    [SQL Server Management Studio](#SSMSProc2)  
  
    [Transact-SQL](#TsqlProc2)  
  
    [objetos de administración de SQL Server](#SMOProc2)  
  
## <a name="BeforeYouBegin"></a>Antes de empezar  
  
### <a name="Restrictions"></a>Limitaciones y restricciones  
Para crear un trabajo, el usuario debe ser miembro de uno de los roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o del rol fijo de servidor **sysadmin** . Solo pueden editar el trabajo el propietario de éste o los miembros del rol **sysadmin** . Para más información sobre los roles fijos de base de datos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consulte [Roles fijos de base de datos del Agente SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Para cambiar el propietario de un trabajo debe ser administrador de sistema.  
  
La asignación de un trabajo a otro inicio de sesión no garantiza que el nuevo propietario disponga de los permisos suficientes para ejecutar el trabajo.  
  
### <a name="Security"></a>Seguridad  
Por razones de seguridad, solo el propietario del trabajo o un miembro del rol **sysadmin** puede cambiar la definición del trabajo. Solo los miembros del rol fijo de servidor **sysadmin** pueden asignar la propiedad de un trabajo a otros usuarios y pueden ejecutar cualquier trabajo, independientemente de quién sea el propietario del mismo.  
  
> [!NOTE]  
> Si cambia la propiedad de un trabajo a un usuario que no es miembro del rol fijo de servidor **sysadmin** y el trabajo está ejecutando unos pasos que necesitan las cuentas de un servidor proxy (por ejemplo, la ejecución de paquetes [!INCLUDE[ssIS](../../includes/ssis_md.md)] ), asegúrese de que el usuario tenga acceso a ese servidor proxy o, de lo contrario, se producirán errores en el trabajo.  
  
#### <a name="Permissions"></a>Permissions  
Para obtener información detallada, vea [Implementar la seguridad del Agente SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMSProc2"></a>Usar SQL Server Management Studio  
**Para asignar a otros usuarios la propiedad de un trabajo**  
  
1.  En el **Explorador de objetos** , conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]y, después, expándala.  
  
2.  Expanda el **Agente SQL Server**, expanda **Trabajos**, haga clic con el botón derecho en el trabajo y, a continuación, haga clic en **Propiedades**.  
  
3.  En la lista **Propietario** , seleccione un inicio de sesión. Para cambiar el propietario de un trabajo debe ser administrador de sistema.  
  
    La asignación de un trabajo a otro inicio de sesión no garantiza que el nuevo propietario disponga de los permisos suficientes para ejecutar el trabajo.  
  
## <a name="TsqlProc2"></a>Usar Transact-SQL  
**Para asignar a otros usuarios la propiedad de un trabajo**  
  
1.  En el Explorador de objetos, conéctese a una instancia del Motor de base de datos y, a continuación, expándala.  
  
2.  En la barra de herramientas, haga clic en **Nueva consulta**.  
  
3.  En la ventana de consulta, escriba las instrucciones siguientes que usan el procedimiento almacenado del sistema [sp_manage_jobs_by_login (Transact-SQL)](https://msdn.microsoft.com/832ec15a-6e92-4eb5-8c4a-af4dba79fbaa) . En el siguiente ejemplo se reasignan todos los trabajos de `danw` a `françoisa`.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'françoisa' ;  
    GO  
    ```  
  
## <a name="SMOProc2"></a>Usar Objetos de administración de SQL Server  
**Para asignar a otros usuarios la propiedad de un trabajo**  
  
1.  Llame a la clase **Job** mediante el lenguaje de programación de su elección, como Visual Basic, Visual C# o PowerShell. Para el código de ejemplo, consulte [Programar tareas administrativas automáticas en el Agente SQL Server](../../relational-databases/server-management-objects-smo/tasks/scheduling-automatic-administrative-tasks-in-sql-server-agent.md).  
  
## <a name="see-also"></a>Consulte también  
[Implementar trabajos](../../ssms/agent/implement-jobs.md)  
[Crear trabajos](../../ssms/agent/create-jobs.md)  
  
