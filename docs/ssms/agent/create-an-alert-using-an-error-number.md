---
title: Crear una alerta con un número de error | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- alerts [SQL Server], error numbers
ms.assetid: 03dd7fac-5073-4f86-babd-37e45a86023c
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 07f3d289595f4d7e3623e879d1d092cf78bc6bc9
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67682800"
---
# <a name="create-an-alert-using-an-error-number"></a>Create an Alert Using an Error Number
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> En [Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la mayoría de las características de agente SQL Server son compatibles actualmente, aunque no todas. Vea [Diferencias de T-SQL en Instancia administrada de Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) para obtener más información.

En este tema se describe cómo crear una alerta del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] que se producirá cuando se presente un erro con un número específico utilizando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**En este tema**  
  
-   **Antes de empezar:**  
  
    [Limitaciones y restricciones](#Restrictions)  
  
    [Seguridad](#Security)  
  
-   **Para crear una alerta con un número de error, utilizando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Antes de empezar  
  
### <a name="Restrictions"></a>Limitaciones y restricciones  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] proporciona una forma gráfica y fácil de administrar todo el sistema de alertas, y constituye el método recomendado para configurar una infraestructura de alertas.  
  
-   Los eventos generados durante **xp_logevent** se producen en la base de datos maestra. Por tanto, **xp_logevent** no desencadena una alerta a menos que el valor de **@database_name** de la alerta sea is **'master'** o NULL.  
  
### <a name="Security"></a>Seguridad  
  
#### <a name="Permissions"></a>Permissions  
De forma predeterminada, solo los miembros del rol fijo de servidor **sysadmin** pueden ejecutar **sp_add_alert**.  
  
## <a name="SSMSProcedure"></a>Usar SQL Server Management Studio  
  
#### <a name="to-create-an-alert-using-an-error-number"></a>Para crear una alerta mediante un número de error  
  
1.  En el **Explorador de objetos** , haga clic en el signo más para expandir el servidor donde desea crear una alerta con un número de error.  
  
2.  Haga clic en el signo más para expandir **Agente SQL Server**.  
  
3.  Haga clic con el botón derecho en **Alertas** y seleccione **Nueva alerta**.  
  
4.  En el cuadro de diálogo **Nueva alerta** , en el cuadro **Nombre** , escriba un nombre para esta alerta.  
  
5.  Active la casilla **Habilitar** para que la alerta se pueda ejecutar. De forma predeterminada, la opción **Habilitar** está activada.  
  
6.  En la lista **Tipo** , seleccione **Alerta de evento de SQL Server**.  
  
7.  En **Definición de evento de alerta**, en la lista **Nombre de la base de datos** , seleccione una base de datos para restringir la alerta a una base de datos específica.  
  
8.  En **Las alertas se mostrarán en función de**, haga clic en **Número de error**y escriba un número de error válido para la alerta. También puede hacer clic en **Gravedad** y seleccionar la gravedad específica que producirá la alerta.  
  
9. Active la casilla correspondiente a **Mostrar alerta cuando el mensaje contenga** para restringir la alerta a una secuencia de caracteres en particular y, a continuación, escriba una palabra clave o una cadena de caracteres en el **Texto del mensaje**. El número máximo de caracteres es 100.  
  
10. Haga clic en **Aceptar**.  
  
## <a name="TsqlProcedure"></a>Usar Transact-SQL  
  
#### <a name="to-create-an-alert-using-an-error-number"></a>Para crear una alerta mediante un número de error  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up
    -- the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up
    -- the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The DB will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
Para más información, consulte [sp_add_alert (Transact-SQL)](https://msdn.microsoft.com/d9b41853-e22d-4813-a79f-57efb4511f09).  
  
