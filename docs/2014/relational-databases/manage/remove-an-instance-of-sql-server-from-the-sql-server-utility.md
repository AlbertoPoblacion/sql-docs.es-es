---
title: Eliminación de una instancia de SQL Server de la utilidad de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 49459743e2eb8af64b1c41910c660f713dbdb2a5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63035974"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a>Quitar una instancia de SQL Server de la utilidad de SQL Server
  Siga los pasos que se indican a continuación para quitar una instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Este procedimiento quita la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la vista de lista del UCP y detiene la recopilación de datos de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . No se desinstala la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Antes de utilizar este procedimiento para quitar una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , asegúrese de que los servicios [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y Agente SQL Server se están ejecutando en la instancia que se va a quitar.  
  
1.  En el explorador de la utilidad en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], haga clic en **Instancias administradas**. Fíjese en la vista de lista de instancias administradas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en el panel de contenido del explorador de la utilidad.  
  
2.  En la columna **Nombre de instancia de SQL Server** de la vista de lista, seleccione la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se va a quitar de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Haga clic con el botón derecho en la instancia que se va a quitar y seleccione **Quitar instancia administrada...** .  
  
3.  Especifique las credenciales con privilegios de administrador para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Haga clic en **conectar...** , compruebe la información en el **conectar al servidor** diálogo cuadro y, después, haga clic en **Connect**. Verá la información de inicio de sesión en el cuadro de diálogo **Quitar instancia administrada** .  
  
4.  Para confirmar la operación, haga clic en **Aceptar**. Para salir de la operación, haga clic en **Cancelar**.  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a>Quitar manualmente una instancia administrada de SQL Server de una Utilidad de SQL Server  
 Este procedimiento quita la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la vista de lista del UCP y detiene la recopilación de datos de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . No se desinstala la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Para utilizar PowerShell con el fin de quitar una instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Este script realiza las siguientes operaciones:  
  
-   Obtiene el UCP por nombre de instancia de servidor.  
  
-   Quita la instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
 Observe que esto es importante para hacer referencia al nombre exacto de instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tal como este se haya almacenado en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que distinga entre mayúsculas y minúsculas, debe especificar el nombre de instancia con la grafía exacta que haya devuelto @@SERVERNAME. Para obtener el nombre de instancia para la instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ejecute esta consulta en la instancia administrada:  
  
```  
select @@SERVERNAME AS instance_name  
```  
  
 En este momento, la instancia administrada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se quitará totalmente del UCP. No aparecerá en la vista de lista la próxima vez que actualice los datos para la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Este estado es idéntico al que se obtiene si un usuario termina correctamente la operación para quitar instancias administradas en la interfaz de usuario SSMS.  
  
## <a name="see-also"></a>Vea también  
 [Utilizar el explorador de Utilidad para administrar la utilidad de SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Solucionar problemas de la Utilidad de SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
