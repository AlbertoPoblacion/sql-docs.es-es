---
title: Realizar copias de seguridad de un registro de transacciones (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 78472cf0a270ffbb83ddf744956e7d2c5a1a1f64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783123"
---
# <a name="back-up-a-transaction-log-sql-server"></a>Realizar copia de seguridad de un registro de transacciones (SQL Server)
  En este tema se describe cómo realizar una copia de seguridad de un registro de transacciones en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o PowerShell.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para realizar una copia de seguridad de un registro de transacciones, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  Como alternativa, puede utilizar el[Asistente para planes de mantenimiento](../maintenance-plans/use-the-maintenance-plan-wizard.md)a fin de crear copias de seguridad.  
  
-   [Tareas relacionadas](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   La instrucción BACKUP no se permite en una transacción explícita o implícita.  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Si una base de datos utiliza el modelo de recuperación optimizado para cargas masivas de registros o completo, debe hacer una copia de seguridad del registro de transacciones con suficiente regularidad como para proteger los datos e impedir que el registro de transacciones se llene. De este modo se trunca el registro y se admite la restauración de la base de datos a un momento concreto.  
  
-   De forma predeterminada, cada operación de copia de seguridad correcta agrega una entrada en el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y en el registro de eventos del sistema. Si hace una copia de seguridad del registro de transacciones con frecuencia, estos mensajes que indican la corrección de la operación pueden acumularse rápidamente, con lo que se crean registros de errores muy grandes que pueden dificultar la búsqueda de otros mensajes. En esos casos, puede suprimir estas entradas de registro utilizando la marca de seguimiento 3226 si ninguno de los scripts depende de esas entradas. Para obtener más información, vea [Marcas de seguimiento &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 De forma predeterminada, los permisos BACKUP DATABASE y BACKUP LOG corresponden a los miembros del rol fijo de servidor **sysadmin** y de los roles fijos de base de datos **db_owner** y **db_backupoperator** .  
  
 Los problemas de propiedad y permisos del archivo físico del dispositivo de copia de seguridad pueden interferir con una operación de copia de seguridad. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] debe poder leer y escribir en el dispositivo y la cuenta en la que se ejecuta el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] debe tener permisos de escritura. En cambio, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), que agrega una entrada para un dispositivo de copia de seguridad en las tablas del sistema, no comprueba los permisos de acceso a los archivos. Es posible que estos problemas con el archivo físico del dispositivo de copia de seguridad no aparezcan hasta que se tenga acceso al recurso físico, al intentar la copia de seguridad o la restauración.  
  
##  <a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-back-up-a-transaction-log"></a>Para realizar una copia de seguridad de un registro de transacciones  
  
1.  Después de conectarse a la instancia apropiada de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], en el Explorador de objetos, haga clic en el nombre del servidor para expandir el árbol de servidores.  
  
2.  Expanda **Bases de datos**y, en función de la base de datos, seleccione la base de datos de un usuario o expanda **Bases de datos del sistema** y seleccione una base de datos del sistema.  
  
3.  Haga clic con el botón derecho en la base de datos, seleccione **Tareas**y haga clic en **Copia de seguridad**. Aparece el cuadro de diálogo **Copia de seguridad de base de datos** .  
  
4.  En el cuadro de lista **Base de datos** , compruebe el nombre de la base de datos. También puede seleccionar otra base de datos en la lista.  
  
5.  Compruebe que el modelo de recuperación sea **FULL** o **BULK_LOGGED**.  
  
6.  En el cuadro de lista **Tipo de copia de seguridad**, seleccione **Registro de transacciones**.  
  
7.  También puede seleccionar **Copia de seguridad de solo copia** para crear un copia de seguridad de solo copia. Una *copia de seguridad de solo copia* es una copia de seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] independiente de la secuencia de copias de seguridad convencionales de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, vea [Copias de seguridad de solo copia &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
    > [!NOTE]  
    >  Cuando la opción **Diferencial** está seleccionada, no se puede crear una copia de seguridad de solo copia.  
  
8.  Acepte el nombre del conjunto de copia de seguridad predeterminado sugerido en el cuadro de texto **Nombre** o escriba un nombre diferente para el conjunto de copia de seguridad.  
  
9. Opcionalmente, en el cuadro de texto **Descripción**, escriba una descripción del conjunto de copia de seguridad.  
  
10. Especifique cuándo expirará el conjunto de copia de seguridad:  
  
    -   Para que el conjunto de copia de seguridad expire al cabo de un número de días específico, haga clic en **Después de** (opción predeterminada) y escriba el número de días tras la creación del conjunto en que este expirará. Este valor puede estar entre 0 y 99999 días; el valor 0 significa que el conjunto de copia de seguridad no expirará nunca.  
  
         El valor predeterminado se establece en la opción **Tiempo predeterminado de retención de medios de copia de seguridad (días)** del cuadro de diálogo **Propiedades del servidor** (página**Configuración de base de datos** ). Para tener acceso a este cuadro de diálogo, haga clic con el botón derecho en el nombre del servidor en el Explorador de objetos y seleccione Propiedades. Después, seleccione la página **Configuración de base de datos** .  
  
    -   Para que el conjunto de copia de seguridad expire en una determinada fecha, haga clic en **El**y escriba la fecha en la que expirará.  
  
11. Elija el tipo de destino de la copia de seguridad haciendo clic en **Disco**, **Dirección URL** o **Cinta**. Para seleccionar las rutas de acceso de hasta 64 unidades de disco o cinta que contienen un solo conjunto de medios, haga clic en **Agregar**. Las rutas seleccionadas se muestran en el cuadro de lista **Copia de seguridad en**.  
  
     Para eliminar un destino de copia de seguridad, selecciónelo y haga clic en **Quitar**. Para ver el contenido de un destino de copia de seguridad, selecciónelo y haga clic en **Contenido**.  
  
12. Para ver o seleccionar las opciones avanzadas, haga clic en **Opciones** en el panel **Seleccionar una página**.  
  
13. Seleccione una opción de **Sobrescribir medios** haciendo clic en una de las siguientes:  
  
    -   **Hacer copia de seguridad en el conjunto de medios existente**  
  
         Para esta opción, haga clic en **Anexar al conjunto de copia de seguridad existente** o **Sobrescribir todos los conjuntos de copia de seguridad existentes**. Para obtener más información, vea [Conjuntos de medios, familias de medios y conjuntos de copias de seguridad &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
         Opcionalmente, seleccione **Comprobar nombre de conjunto de medios y fecha de expiración del conjunto de copia de seguridad** para que la operación de copia de seguridad compruebe la fecha y la hora en que expiran el conjunto de medios y el conjunto de copia de seguridad.  
  
         También puede escribir un nombre en el cuadro de texto **Nombre del conjunto de medios** . Si no especifica ningún nombre, se creará un conjunto de medios con un nombre en blanco. Si especifica un nombre para el conjunto, los medios (cinta o disco) se comprueban para ver si el nombre real coincide con el nombre especificado aquí.  
  
         Si deja el nombre del conjunto de medios en blanco y selecciona la casilla para comprobarlo con los medios, el resultado correcto significará que el nombre del conjunto en los medios también está en blanco.  
  
    -   **Hacer una copia de seguridad en un nuevo conjunto de medios y borrar todos los conjuntos de copia de seguridad existentes**  
  
         Para esta opción, escriba un nombre en el cuadro de texto **Nuevo nombre del conjunto de medios** y, opcionalmente, describa el conjunto de medios en el cuadro de texto **Nueva descripción del conjunto de medios**. Para obtener más información, vea [Conjuntos de medios, familias de medios y conjuntos de copias de seguridad &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
14. Si lo desea, en la sección **confiabilidad** , compruebe lo siguiente:  
  
    -   **Comprobar copia de seguridad al finalizar**.  
  
    -   **Realice una suma de comprobación antes de escribir en los medios**y, opcionalmente, **continúe con el error de suma de comprobación**. Para obtener más información sobre las sumas de comprobación, vea [Errores posibles de medios durante copia de seguridad y restauración &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
15. En la sección **Registro de transacciones** :  
  
    -   Para las copias de seguridad rutinarias del registro, conserve la selección predeterminada **Truncar el registro de transacciones quitando las entradas inactivas**.  
  
    -   Para hacer una copia de seguridad del final del registro (es decir, del registro activo), active **Realizar copia de seguridad del final del registro y dejar la base de datos en estado de restauración**.  
  
         Una copia del final del registro se lleva a cabo cuando no se consigue realizar la copia de seguridad del final de registro para impedir la pérdida de trabajo. Realice una copia de seguridad del registro activo (copia del final del registro) después de un error, antes de comenzar la restauración de la base de datos o cuando se conmuta por error a una base de datos secundaria. Esta opción equivale a especificar la opción NORECOVERY en la instrucción BACKUP LOG de Transact-SQL. Para obtener más información sobre las copias del final del registro, vea [Copias del final del registro &#40;SQL Server&#41;](tail-log-backups-sql-server.md).  
  
16. Si va a realizar copias de seguridad en una unidad de cinta (según se haya especificado en la sección **Destino** de la página **General**), la opción **Descargar la cinta después de realizar la copia de seguridad** está activa. Al hacer clic en esta opción se activa la opción **Rebobinar la cinta antes de descargar** .  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]y versiones posteriores admiten la [compresión de copia de seguridad](backup-compression-sql-server.md). De manera predeterminada, el hecho de que se comprima una copia de seguridad depende de la opción de configuración que tenga el servidor para el **valor predeterminado de la compresión de la copia de seguridad**. Sin embargo, independientemente del nivel predeterminado del servidor actual, puede comprimir una copia de seguridad activando **Comprimir copia de seguridad** y puede evitar la compresión activando **No comprimir copia de seguridad**.  
  
     **Para ver el valor predeterminado de la compresión de copia de seguridad actual**  
  
    -   [Ver o establecer la opción de configuración del servidor de compresión de copia de seguridad predeterminada](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 **Cifrado**  
  
 Para cifrar el archivo de copia de seguridad, active la casilla **Cifrar copia de seguridad** . Seleccione un algoritmo de cifrado que utilizar para cifrar el archivo de copia de seguridad y proporcione un certificado o clave asimétrica. Los algoritmos disponibles para el cifrado son:  
  
-   AES 128  
  
-   AES 192  
  
-   AES 256  
  
-   Triple DES  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-back-up-a-transaction-log"></a>Para realizar una copia de seguridad de un registro de transacciones  
  
1.  Ejecute la instrucción BACKUP LOG para realizar una copia de seguridad del registro de transacciones y especifique:  
  
    -   El nombre de la base de datos a la que pertenece el registro de transacciones del que se desea hacer una copia de seguridad.  
  
    -   El dispositivo de copia de seguridad en el que se va a escribir la copia de seguridad del registro de transacciones.  
  
###  <a name="TsqlExample"></a> Ejemplo (Transact-SQL)  
  
> [!IMPORTANT]  
>  En este ejemplo se utiliza la base de datos [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] , que utiliza el modelo de recuperación simple. Con el fin de permitir copias de seguridad de registros, antes de realizar una copia de seguridad completa de la base de datos, la base de datos se ha configurado para usar el modelo de recuperación completa. Para obtener más información, vea [Ver o cambiar el modelo de recuperación de una base de datos &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
 En este ejemplo se crea una copia de seguridad del registro de transacciones de la base de datos [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] en el dispositivo de copia de seguridad creado anteriormente, `MyAdvWorks_FullRM_log1`.  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> Usar PowerShell  
  
Utilice el cmdlet `Backup-SqlDatabase` y especifique `Log` como el valor del parámetro `-BackupAction`.  
  
En el ejemplo siguiente se crea una copia de seguridad de registro de la base de datos `MyDB` en la ubicación de copia de seguridad predeterminada de la instancia de servidor `Computer\Instance`.  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
Para configurar y usar el proveedor de SQL Server PowerShell, vea [proveedor de SQL Server PowerShell](../../powershell/sql-server-powershell-provider.md).
  
##  <a name="RelatedTasks"></a> Tareas relacionadas  
  
-   [Restaurar una copia de seguridad de registros de transacciones &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
-   [Restaurar una base de datos de SQL Server a un momento dado &#40;modelo de recuperación completa&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [Solucionar problemas de un registro de transacciones lleno &#40;Error 9002 de SQL Server&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a>Consulte también  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Aplicar copias de seguridad del registro de transacciones &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Planes de mantenimiento](../maintenance-plans/maintenance-plans.md)   
 [Copias de seguridad de archivos completas &#40;SQL Server&#41;](full-file-backups-sql-server.md)  
