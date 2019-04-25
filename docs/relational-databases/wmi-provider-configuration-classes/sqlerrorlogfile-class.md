---
title: Clase SqlErrorLogFile | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2794e4f59b6c898b1fd956c0f9390ba9bbbd439e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62515480"
---
# <a name="sqlerrorlogfile-class"></a>Clase SqlErrorLogFile
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Proporciona propiedades para ver información sobre un archivo de registro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Propiedades  
 La clase SQLErrorLogFile define las siguientes propiedades.  
  
|||  
|-|-|  
|ArchiveNumber|Tipo de datos: **uint32**<br /><br /> Tipo de acceso: Solo lectura<br /><br /> <br /><br /> El número de archivo para el archivo de registro.|  
|InstanceName|Tipo de datos: **cadena**<br /><br /> Tipo de acceso: Solo lectura<br /><br /> Calificadores: Key<br /><br /> <br /><br /> El nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] donde reside el archivo de registro.|  
|LastModified|Tipo de datos: **datetime**<br /><br /> Tipo de acceso: Solo lectura<br /><br /> <br /><br /> Fecha de la última modificación del archivo de registro.|  
|LogFileSize|Tipo de datos: **uint32**<br /><br /> Tipo de acceso: Solo lectura<br /><br /> <br /><br /> El tamaño del archivo de registro en bytes.|  
|Name|Tipo de datos: **cadena**<br /><br /> Tipo de acceso: Solo lectura<br /><br /> Calificadores: Key<br /><br /> <br /><br /> El nombre del archivo de registro.|  
  
## <a name="remarks"></a>Comentarios  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Espacio de nombres|\raíz\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se recupera información sobre todos los archivos de registro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una instancia especificada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para ejecutar el ejemplo, reemplace \< *Instance_Name*> con el nombre de la instancia, por ejemplo, 'instancia1'.  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>Comentarios  
 Cuando *nombreDeInstancia* no se proporciona en la instrucción WQL, la consulta devolverá información para la instancia predeterminada. Por ejemplo, la siguiente instrucción WQL devolverá información sobre todos los archivos de registro de la instancia predeterminada (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Seguridad  
 Para conectarse a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivo de registro a través de WMI, debe tener los permisos siguientes en los equipos locales y remotos:  
  
-   Acceso de lectura a la **Root\Microsoft\SqlServer\ComputerManagement10** espacio de nombres WMI. De forma predeterminada, todos tienen acceso de lectura mediante el permiso Habilitar cuenta.  
  
    > [!NOTE]  
    >  Para obtener información sobre cómo comprobar los permisos de WMI, consulte la sección seguridad del tema [ver sin conexión archivos de registro](../../relational-databases/logs/view-offline-log-files.md).  
  
-   Permiso de lectura a la carpeta que contiene los registros de errores. De forma predeterminada, el error registros se encuentran en la siguiente ruta de acceso (donde \< *unidad >* representa la unidad donde se instaló [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y \< *nombreDeInstancia*> es el nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Unidad >: \Program Files\Microsoft SQL Server\MSSQL11** **.\< NombreDeInstancia > \MSSQL\Log**  
  
 Si se conecta a través de un firewall, asegúrese de que se establece una excepción en el firewall para WMI en los equipos de destino remotos. Para obtener más información, consulte [conectarse a WMI de forma remota comenzando con Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Vea también  
 [Clase SqlErrorLogEvent](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogevent-class.md)   
 [Ver archivos del registro sin conexión](../../relational-databases/logs/view-offline-log-files.md)  
  
  
