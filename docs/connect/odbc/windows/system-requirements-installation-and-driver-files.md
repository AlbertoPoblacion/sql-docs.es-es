---
title: Requisitos del sistema, instalación y archivos del controlador | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9b48188cbc1eb25774bc127246514d82ca5ef475
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66841083"
---
# <a name="system-requirements-installation-and-driver-files"></a>Requisitos del sistema, instalación y archivos del controlador
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] admite conexiones a SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]y [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en Windows puede instalarse en un equipo que también tenga una o varias versiones de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
ODBC Driver 13 y 13.1 para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], además de lo anterior, es compatible con SQL Server 2016. 

ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] admite todas las anteriores y también SQL Server 2017.

ODBC Driver 17 for SQL Server es compatible con la versión 17.3 del controlador a partir de SQL Server 2019.

Es el nombre del controlador que se especifica en una cadena de conexión `ODBC Driver 11 for SQL Server` o `ODBC Driver 13 for SQL Server` (de 13 y 13.1) o `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Sistemas operativos admitidos

Puede ejecutar aplicaciones con el controlador en los siguientes sistemas operativos Windows:  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(solo en ODBC Driver 11)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Instalación de Microsoft ODBC Driver for SQL Server

El controlador se instala al ejecutar `msodbcsql.msi` desde uno de los siguientes vínculos:

- [Descargar Microsoft ODBC Driver 17 for SQL Server en Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Descargar Microsoft ODBC Driver 13.1 for SQL Server en Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Descargar Microsoft ODBC Driver 13 for SQL Server en Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Descargar Microsoft ODBC Driver 11 for SQL Server en Windows](https://www.microsoft.com/download/details.aspx?id=36434). 

> [!NOTE]
> Para aquellos que tienen controladores 17.1.0.1 o instalar a continuación, se recomienda que se desinstale manualmente antes de instalar la versión más reciente del controlador

Puede instalarse en paralelo con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  

Cuando se llama a `msodbcsql.msi`, solo se instalan los componentes de cliente de forma predeterminada. Los componentes de cliente son archivos que permiten ejecutar aplicaciones desarrolladas mediante el controlador. Para instalar los componentes de SDK, especifique `ADDLOCAL=ALL` en la línea de comandos. Por ejemplo:  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Especifique `IACCEPTMSODBCSQLLICENSETERMS=YES` para aceptar los términos de la licencia para el usuario final si utiliza la opción de instalación `/passive`, `/qn`, `/qb` o `/qr`. Esta opción se debe especificar con todas las letras mayúsculas. Por ejemplo:  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 Para realizar una desinstalación silenciosa, haga lo siguiente:  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Cuando una aplicación utiliza el controlador, esta debe indicar que depende del controlador mediante la opción de instalación `APPGUID`. De este modo, el instalador del controlador puede notificar cuáles son las aplicaciones dependientes antes de que se lleve a cabo la desinstalación. Para especificar una dependencia del controlador, establezca el parámetro de línea de comandos `APPGUID` en el código de producto cuando se instale en modo silencioso el controlador. (Se debe crear un código de producto al usar Microsoft Installer para empaquetar el programa de instalación de la aplicación). Por ejemplo:  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Herramientas de línea de comandos: sqlcmd.exe y bcp.exe

El `bcp.exe` y `sqlcmd.exe` las herramientas para usarlo con el controlador puede descargarse en [utilidades de línea de comandos de Microsoft 11 para SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [13 de utilidades de línea de comandos de Microsoft para SQL Server](https://www.microsoft.com/download/details.aspx?id=52680), o [Utilidades de línea de comandos de Microsoft 13.1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). El controlador es un requisito previo para instalar `sqlcmd.exe` y `bcp.exe`.
  
`bcp.exe` y `sqlcmd.exe` están instalados en el `110\Tools` subcarpeta de `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` para la versión 11, y `130\Tools` para 13.1 y 13.

Las aplicaciones que utilizan funciones BCP deben especificar el controlador (con la misma versión que aparece en el archivo de encabezado) y la biblioteca usada para compilar la aplicación.  

Por ejemplo, cuando se compila una aplicación ODBC con `msodbcsql11.lib` y `msodbcsql.h`, use "DRIVER = {ODBC Driver 11 para SQL Server}" en la cadena de conexión.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Componentes de Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en Windows 
 El controlador ODBC en Windows contiene los siguientes componentes:
 
|Componente|Descripción|  
|---------------|-----------------|  
|msodbcsql17.dll o <br> msodbcsql13.dll o <br> msodbcsql11.dll|El archivo de biblioteca de vínculos dinámicos (DLL) que contiene toda la funcionalidad del controlador. Este archivo está instalado en % SYSTEMROOT%\System32.|  
|msodbcdiag17.dll o <br> msodbcdiag13.dll o <br> msodbcdiag11.dll|El archivo de biblioteca de vínculos dinámicos (DLL) que contiene la interfaz de diagnósticos (seguimiento) del controlador. Este archivo está instalado en % SYSTEMROOT%\System32.|
|msodbcsqlr17.rll o <br> msodbcsqlr13.rll o <br> msodbcsqlr11.rll|El archivo de recursos asociado de la biblioteca de controladores. Este archivo está instalado en % SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm o <br> s11ch_msodbcsql.chm |El archivo de Ayuda del Asistente para orígenes de datos que documenta cómo crear un origen de datos para el controlador. Este archivo se instala en %SYSTEMROOT%\System32\1033 <br /> <br /> **Nota:** no hay ningún archivo chm para ODBC Driver 17. |  
|msodbcsql.h|El archivo de encabezado que contiene todas las definiciones nuevas necesarias para utilizar el controlador.<br /><br /> **Nota:**  No se puede hacer referencia a msodbcsql.h y odbcss.h en el mismo programa.<br /><br /> msodbcsql.h para ODBC Driver 17 o 13 está instalado en %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> msodbcsql.h para ODBC Driver 11 está instalado en %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib o <br> msodbcsql13.lib o <br> msodbcsql11.lib|El archivo de biblioteca necesario para llamar a las funciones de la utilidad **bcp** que forman parte del controlador.<br /><br /> **Nota:** Si hace referencia a este archivo de biblioteca en el programa, asegúrese de que se encuentra en la ruta de acceso de su sistema y en la de los usuarios que usen la aplicación.<br /><br /> msodbcsql17.lib o msodbcsql13.lib está instalado en %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib está instalado en %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|

  
## <a name="see-also"></a>Consulte también  
 [Microsoft ODBC Driver for SQL Server en Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
