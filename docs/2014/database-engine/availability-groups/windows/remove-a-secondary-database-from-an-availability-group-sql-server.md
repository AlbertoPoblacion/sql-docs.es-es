---
title: Quitar una base de datos secundaria de un grupo de disponibilidad (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 183acf0bf1e6e92483989545a710769501fa946d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62814150"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a>Quitar una base de datos secundaria de un grupo de disponibilidad (SQL Server)
  En este tema se describe cómo quitar una base de datos secundaria de un grupo de disponibilidad AlwaysOn utilizando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o PowerShell en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Antes de empezar:**  
  
     [Requisitos previos](#Prerequisites)  
  
     [Seguridad](#Security)  
  
-   **Para quitar una base de datos secundaria, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Seguimiento:**  [después de quitar una base de datos secundaria de un grupo de disponibilidad](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a>   
###  <a name="Prerequisites"></a> Requisitos previos y restricciones  
  
-   Esta tarea solo se admite en las réplicas secundarias. Debe estar conectado a la instancia del servidor que hospeda la réplica secundaria de la que se va a quitar la base de datos.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la base de datos.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
 **Para quitar una base de datos secundaria de un grupo de disponibilidad**  
  
1.  En el Explorador de objetos, conéctese a la instancia del servidor que hospeda la réplica secundaria de la que desea quitar una o varias bases de datos secundarias y expanda el árbol.  
  
2.  Expanda los nodos **Alta disponibilidad de AlwaysOn** y **Grupos de disponibilidad** .  
  
3.  Seleccione el grupo de disponibilidad y expanda el nodo **Bases de datos de disponibilidad** .  
  
4.  Este paso depende de si desea quitar varios grupos de bases de datos o solo una base de datos, del siguiente modo:  
  
    -   Para quitar varias bases de datos, use el panel **Detalles del Explorador de objetos** para ver y seleccionar todas las bases de datos que desea quitar. Para obtener más información, vea [Usar los detalles del Explorador de objetos para supervisar los grupos de disponibilidad &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Para quitar una sola base de datos, selecciónela en el panel **Explorador de objetos** o el panel **Detalles del Explorador de objetos** .  
  
5.  Haga clic con el botón derecho en la base de datos o las bases de datos seleccionadas y seleccione **Quitar base de datos secundaria** en el menú de comandos.  
  
6.  En el cuadro de diálogo **Quitar base de datos del grupo de disponibilidad** , para quitar todas las bases de datos enumeradas, haga clic en **Aceptar**. Si no desea quitar todas las bases de datos enumeradas, haga clic en **Cancelar**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para quitar una base de datos secundaria de un grupo de disponibilidad**  
  
1.  Conéctese a la instancia del servidor que hospeda la réplica secundaria.  
  
2.  Utilice la cláusula [SET HADR de la instrucción ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) del siguiente modo:  
  
     ALTER DATABASE *database_name* SET HADR OFF  
  
     donde *database_name* es el nombre de una base de datos secundaria que se va a quitar del grupo de disponibilidad al que pertenece.  
  
     En el ejemplo siguiente se quita la base de datos secundaria local *MyDb2* de su grupo de disponibilidad.  
  
    ```  
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="PowerShellProcedure"></a> Usar PowerShell  
 **Para quitar una base de datos secundaria de un grupo de disponibilidad**  
  
1.  Cambie el directorio (`cd`) a la instancia del servidor que hospeda la réplica secundaria.  
  
2.  Use el cmdlet **Remove-SqlAvailabilityDatabase** , y especifique el nombre de la base de datos de disponibilidad que se va a quitar del grupo de disponibilidad. Cuando esté conectado a una instancia de servidor que hospeda una réplica secundaria, solo la base de datos secundaria local se quita del grupo de disponibilidad.  
  
     Por ejemplo, el comando siguiente quita la base de datos secundaria `MyDb8` de la réplica secundaria hospedada por la instancia de servidor denominada `SecondaryComputer\Instance`. La sincronización de datos cesa en las bases de datos secundarias quitadas. Este comando no afecta a la base de datos principal ni a ninguna otra base de datos secundaria.  
  
    ```  
    Remove-SqlAvailabilityDatabase `  
    -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  Para ver la sintaxis de un cmdlet, use el cmdlet `Get-Help` en el entorno de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Para más información, consulte [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Para configurar y usar el proveedor de SQL Server PowerShell**  
  
-   [Proveedor de SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="FollowUp"></a> Seguimiento: después de quitar una base de datos secundaria de un grupo de disponibilidad  
 Cuando se quita una base de datos secundaria, deja de estar unida al grupo de disponibilidad y este descartará toda la información acerca de la base de datos secundaria quitada. La base de datos secundaria quitada se pone en estado RESTORING.  
  
> [!TIP]  
>  Durante un breve período de tiempo después de quitar una base de datos secundaria, es posible que pueda reiniciar la sincronización de datos de AlwaysOn en la base de datos volviéndola a unir al grupo de disponibilidad. Para obtener más información, vea [Combinar una base de datos secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
 En este momento hay formas alternativas de tratar una base de datos secundaria quitada:  
  
-   Si ya no necesita la base de datos secundaria, puede quitarla.  
  
     Para obtener más información, vea [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) o [Eliminar una base de datos](../../../relational-databases/databases/delete-a-database.md).  
  
-   Si desea obtener acceso a una base de datos secundaria quitada después de haberse quitado del grupo de disponibilidad, puede recuperar la base de datos. Sin embargo, si recupera una base de datos secundaria quitada, dos bases de datos independientes divergentes que tienen el mismo nombre estarán en línea. Debe asegurarse de que los clientes puedan tener acceso solo a la base de datos principal actual.  
  
     Para obtener más información, vea [Recuperar una base de datos sin restaurar los datos &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Quitar una base de datos principal de un grupo de disponibilidad &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
