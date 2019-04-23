---
title: Use PowerShell para cambiar y enumerar propietarios de suscripciones de Reporting Services y ejecutar una suscripción | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 0fa6cb36-68fc-4fb8-b1dc-ae4f12bf6ff0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53fc7b585edf852d04256c9e85fa0bd96aa7eced
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59960901"
---
# <a name="use-powershell-to-change-and-list-reporting-services-subscription-owners-and-run-a-subscription"></a>Use PowerShell para cambiar y enumerar a los propietarios de una suscripción de Reporting Services y ejecutar una suscripción
  A partir de [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] , se puede transferir mediante programación la propiedad de una suscripción a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] de un usuario a otro. En este tema se proporcionan varios scripts de Windows PowerShell que puede utilizar para cambiar o simplemente presentar la propiedad de la suscripción. Cada ejemplo incluye sintaxis de ejemplo para el modo nativo y para el modo SharePoint. Después de cambiar el propietario de la suscripción, la suscripción se ejecutará en el contexto de seguridad del nuevo propietario, y el campo User!UserID del informe mostrará el valor del nuevo propietario. Para obtener más información sobre el modelo de objetos al que llaman los ejemplos de PowerShell, vea <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>  
  
 ![Contenido relacionado con PowerShell](../media/rs-powershellicon.jpg "Contenido relacionado con PowerShell")  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  Modo nativo de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] &#124; Modo de SharePoint de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]|  
  
 **En este tema:**  
  
-   [Cómo usar los scripts](#bkmk_how_to)  
  
-   [Secuencia de comandos: Mostrar la propiedad de todas las suscripciones](#bkmk_list_ownership_all)  
  
-   [Secuencia de comandos: Mostrar todas las suscripciones poseídas por un usuario específico](#bkmk_list_all_one_user)  
  
-   [Secuencia de comandos: Cambiar la propiedad de todas las suscripciones poseídas por un usuario específico](#bkmk_change_all)  
  
-   [Secuencia de comandos: Lista de todas las suscripciones asociadas a un informe específico](#bkmk_list_for_1_report)  
  
-   [Secuencia de comandos: Cambiar la propiedad de una suscripción específica](#bkmk_change_all_1_subscription)  
  
-   [Secuencia de comandos: Ejecutar (desencadenar) una sola suscripción](#bkmk_run_1_subscription)  
  
##  <a name="bkmk_how_to"></a> Cómo usar los scripts  
  
### <a name="permissions"></a>Permisos  
 Esta sección resume los niveles de permiso requeridos para utilizar los métodos para el modo nativo y para el modo SharePoint de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Los scripts de este tema usan los siguientes métodos de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] :  
  
-   [Método ReportingService2010.ListSubscriptions](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listsubscriptions.aspx)  
  
-   [Método ReportingService2010.ChangeSubscriptionOwner](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.changesubscriptionowner.aspx)  
  
-   [ReportingService2010.ListChildren](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listchildren.aspx)  
  
-   El método [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) solo se usa en el último script para activar la suscripción específica que se ejecutará. Si no tiene previsto utilizar este script, omita los requisitos de permiso para el método FireEvent.  
  
 **Modo nativo:**  
  
-   Mostrar suscripciones: (HYPERLINK "https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx" ReadSubscription en el informe y el usuario es propietario de la suscripción) o ReadAnySubscription  
  
-   Cambiar suscripciones: El usuario debe ser miembro del grupo BUILTIN\Administrators  
  
-   Mostrar elementos secundarios: ReadProperties en elemento  
  
-   Desencadenar evento: GenerateEvents (sistema)  
  
 **Modo SharePoint:**  
  
-   Mostrar suscripciones: ManageAlerts o (HYPERLINK "https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx" CreateAlerts en el informe y el usuario es propietario de la suscripción y la suscripción es una suscripción programada).  
  
-   Cambiar suscripciones: ManageWeb  
  
-   Mostrar elementos secundarios: ViewListItems  
  
-   Desencadenar evento: ManageWeb  
  
 Para obtener más información, vea [Comparación de roles y tareas en Reporting Services con grupos y permisos de SharePoint](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).  
  
### <a name="script-usage"></a>Uso de scripts  
 **Crear archivos de script (.ps1)**  
  
1.  Crear una carpeta con el nombre **c:\scripts**. Si elige una carpeta diferente, modifique el nombre de la carpeta utilizada en las instrucciones de sintaxis de línea de comandos del ejemplo.  
  
2.  Cree un archivo de texto para cada script y guarde los archivos en la carpeta c:\scripts. Cuando cree los archivos .ps1, use el nombre de la sintaxis de línea de comandos de cada ejemplo.  
  
3.  Abra un símbolo del sistema con privilegios administrativos.  
  
4.  Ejecute cada archivo de script utilizando la sintaxis de línea de comando proporcionada con cada ejemplo.  
  
 **Entornos probados**  
  
 Los scripts de este tema se probaron en PowerShell versión 3 y con las siguientes versiones de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]  
  
##  <a name="bkmk_list_ownership_all"></a> Secuencia de comandos: Mostrar la propiedad de todas las suscripciones  
 Este script presenta todas las suscripciones de un sitio. Puede utilizarlo para probar su conexión o para comprobar la ruta de acceso del informe y el identificador de la suscripción para su uso en los demás scripts. Además, es un script útil para verificar qué suscripciones existen y quién las posee.  
  
 **Sintaxis de modo nativo:**  
  
```  
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"  
```  
  
 **Sintaxis de modo SharePoint:**  
  
```  
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "http://[server]"  
```  
  
 **Script:**  
  
```  
# Parameters  
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
  
Param(  
    [string]$server,  
    [string]$site  
   )  
  
$rs2010 += New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site  
  
Write-Host " "  
Write-Host "----- $server's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status  
```  
  
> [!TIP]  
>  Para comprobar las direcciones URL de los sitios en modo de SharePoint, use el cmdlet de SharePoint **Get-SPSite**. Para obtener más información, vea [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx).  
  
##  <a name="bkmk_list_all_one_user"></a> Secuencia de comandos: Mostrar todas las suscripciones poseídas por un usuario específico  
 Este script presenta todas las suscripciones poseídas por un usuario específico. Puede utilizarlo para probar su conexión o para comprobar la ruta de acceso del informe y el identificador de la suscripción para su uso en los demás scripts. Este script es útil si desea comprobar qué suscripciones poseía una persona que abandona su organización, para cambiar el propietario o eliminar la suscripción.  
  
 **Sintaxis de modo nativo:**  
  
```  
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"  
```  
  
 **Sintaxis de modo SharePoint:**  
  
```  
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "http://[server]"  
```  
  
 **Script:**  
  
```  
# Parameters:  
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change  
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site        - use "/" for default native mode site  
Param(  
    [string]$currentOwner,  
    [string]$server,  
    [string]$site  
)  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site);  
  
Write-Host " "  
Write-Host " "  
Write-Host "----- $currentOwner's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}  
```  
  
##  <a name="bkmk_change_all"></a> Secuencia de comandos: Cambiar la propiedad de todas las suscripciones poseídas por un usuario específico  
 Este script cambia la propiedad de todas las suscripciones poseídas por un usuario específico al nuevo parámetro de propietario.  
  
 **Sintaxis de modo nativo:**  
  
```  
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"  
```  
  
 **Sintaxis de modo SharePoint:**  
  
```  
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"  
```  
  
 **Script:**  
  
```  
# Parameters:  
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change  
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change  
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)  
  
Param(  
    [string]$currentOwner,  
    [string]$newOwner,  
    [string]$server  
)  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$items = $rs2010.ListChildren("/", $true);  
  
$subscriptions = @();  
  
ForEach ($item in $items)  
{  
    if ($item.TypeName -eq "Report")  
    {  
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);  
        ForEach ($curRepSub in $curRepSubs)  
        {  
            if ($curRepSub.Owner -eq $previousOwner)  
            {  
                $subscriptions += $curRepSub;  
            }  
        }  
    }  
}  
  
Write-Host " "  
Write-Host " "  
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "  
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize  
  
ForEach ($sub in $subscriptions)  
{  
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);  
}  
  
$subs2 = @();  
  
ForEach ($item in $items)  
{  
    if ($item.TypeName -eq "Report")  
    {  
        $subs2 += $rs2010.ListSubscriptions($item.Path);  
    }  
}  
```  
  
##  <a name="bkmk_list_for_1_report"></a> Secuencia de comandos: Lista de todas las suscripciones asociadas a un informe específico  
 Este script presenta todas las suscripciones asociadas a un informe específico. La sintaxis de la ruta de acceso del informe es un modo SharePoint diferente que requiere una dirección URL completa. En los ejemplos de sintaxis, el nombre del informe es "title only", que contiene un espacio, lo que obliga a usar comillas en el nombre del informe.  
  
 **Sintaxis de modo nativo:**  
  
```  
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"  
```  
  
 **Sintaxis de modo SharePoint:**  
  
```  
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'http://[server]/shared documents/title only.rdl'" "http://[server]"  
```  
  
 **Script:**  
  
```  
# Parameters:  
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"  
#    site        - use "/" for default native mode site  
Param  
(  
      [string]$server,  
      [string]$reportpath,  
      [string]$site  
)  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site);  
  
Write-Host " "  
Write-Host " "  
Write-Host "----- $reportpath 's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}  
```  
  
##  <a name="bkmk_change_all_1_subscription"></a> Secuencia de comandos: Cambiar la propiedad de una suscripción específica  
 Este script cambia la propiedad de una suscripción específica. La suscripción está identificada por el SubscriptionID que pasa al script. Puede utilizar uno de los scripts para presentar suscripciones para determinar el SubscriptionID correcto.  
  
 **Sintaxis de modo nativo:**  
  
```  
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"  
```  
  
 **Sintaxis de modo SharePoint:**  
  
```  
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "http://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"  
```  
  
 **Script:**  
  
```  
# Parameters:  
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change  
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site        - use "/" for default native mode site  
#    subscriptionID - guid for the single subscription to change  
  
Param(  
    [string]$newOwner,  
    [string]$server,  
    [string]$site,  
    [string]$subscriptionid  
   )  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};  
  
Write-Host " "  
Write-Host "----- $subscriptionid's Subscription properties: "  
$subscription | select Path, report, Description, SubscriptionID, Owner, Status  
  
$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)  
  
#refresh the list  
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site  
Write-Host "----- $subscriptionid's Subscription properties: "  
$subscription | select Path, report, Description, SubscriptionID, Owner, Status  
```  
  
##  <a name="bkmk_run_1_subscription"></a> Secuencia de comandos: Ejecutar (desencadenar) una sola suscripción  
 Este script ejecuta una suscripción específica mediante el método FireEvent. El script ejecuta inmediatamente la suscripción independientemente de la programación configurada para la suscripción. Se compara EventType con el conjunto de eventos conocido que se ha definido en el archivo de configurador del servidor de informes **rsreportserver.config** . El script utiliza el siguiente tipo de eventos para las suscripciones estándar:  
  
 `<Event>`  
  
 `<Type>TimedSubscription</Type>`  
  
 `</Event>`  
  
 Para obtener más información acerca del archivo de configuración, consulte [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).  
  
 El script incluye la lógica de retraso "`Start-Sleep -s 6`" para que haya tiempo después de que se desencadene el evento, de modo que el estado actualizado esté disponible con el método ListSubscription.  
  
 **Sintaxis de modo nativo:**  
  
```  
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"  
```  
  
 **Sintaxis de modo SharePoint:**  
  
```  
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "http://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"  
```  
  
 **Script:**  
  
```  
  
# Parameters  
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site           - use $null for a native mode server  
#    subscriptionid - subscription guid  
  
Param(  
  [string]$server,  
  [string]$site,  
  [string]$subscriptionid  
  )  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
#event type is case sensative to what is in the rsreportserver.config  
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)  
  
Write-Host " "  
Write-Host "----- Subscription ($subscriptionid) status: "  
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted  
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted  
$subscriptions = $rs2010.ListSubscriptions($site);   
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}  
  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:ReportService2010.ReportingService2010.ListSubscriptions%2A>   
 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>   
 <xref:ReportService2010.ReportingService2010.ListChildren%2A>   
 <xref:ReportService2010.ReportingService2010.FireEvent%2A>  
  
  
