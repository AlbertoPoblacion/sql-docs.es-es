---
title: Instalar Analysis Services | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0904dc53e17ed140310df38d1f63dc9fe3fc45cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63054565"
---
# <a name="install-sql-server-analysis-services"></a>Instalar SQL Server Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  SQL Server Analysis Services es un servidor de bases de datos analíticas que hospeda modelos tabulares, cubos multidimensionales y modelos de minería de datos que puede acceder desde informes, hojas de cálculo y paneles.  
  
 Analysis Services es de varias instancias, lo que significa que puede instalar más de una copia en un único equipo o ejecutar versiones nuevas y antiguas side-by-side. Cualquier instancia que instale se ejecuta en uno de estos tres modos, según lo determinado durante la instalación: Multidimensional y minería de datos, Tabular o SharePoint. Si quiere usar varios modos, necesitará una instancia independiente para cada uno.  
  
 Después de instalar el servidor en un modo determinado, puede usarlo para hospedar soluciones conformes con ese modo. Por ejemplo, se necesita un servidor de modo tabular para acceder a los datos de modelo tabulares a través de la red.  
  
## <a name="get-tools-and-designers"></a>Obtener herramientas y diseñadores  
 El programa de instalación de SQL Server ya no instala los diseñadores de modelos ni las herramientas de administración usados para el diseño de soluciones o la administración de servidores. En esta versión, las herramientas tienen un programa de instalación independiente, al que se puede acceder desde los vínculos siguientes:  
  
-   [Descarga de SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md)  
  
-   [Descargar SQL Server Data Tools (SSDT)](../../../ssdt/download-sql-server-data-tools-ssdt.md)  
  
 Necesitará SSMS y SSDT para trabajar con datos e instancias de Analysis Services. Las herramientas pueden instalarse en cualquier ubicación, pero no olvide configurar puertos en el servidor antes de intentar una conexión. Para obtener información detallada, vea [Configurar Firewall de Windows para permitir el acceso a Analysis Services](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .  
  
## <a name="install-using-a-wizard"></a>Instalar mediante un asistente  
 La siguiente lista muestra las páginas del Asistente para la instalación de SQL Server que se usan para instalar Analysis Services.  
  
1.  Seleccione **Analysis Services** en el árbol de características del programa de instalación.  
  
     ![Árbol de características del programa de instalación que muestra Analysis Services](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "árbol de características del programa de instalación que muestra Analysis Services")  
  
2.  En la página de configuración de Analysis Services, seleccione un modo. Modo tabular es el valor predeterminado...  
  
     ![Página de configuración con las opciones de configuración de Analysis Services](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "página de configuración con las opciones de configuración de Analysis Services")  
  
  El modo tabular utiliza el motor de análisis en memoria xVelocity (VertiPaq), que es el almacenamiento predeterminado para los modelos tabulares. Después de implementar los modelos tabulares en el servidor, puede configurar selectivamente las soluciones tabulares para utilizar el almacenamiento de disco de DirectQuery como una alternativa al almacenamiento vinculado a la memoria.  
 
 Multidimensional y minería de datos de modo uso MOLAP como almacenamiento predeterminado para los modelos implementados en Analysis Services. Después de implementar en el servidor, puede configurar una solución para usar ROLAP si quiere ejecutar consultas directamente en la base de datos relacional en lugar de almacenar los datos de la consulta en una base de datos multidimensional de Analysis Services.  
  

  
 La administración de memoria y la configuración de E/S se pueden ajustar para obtener un mejor rendimiento al usar modos de almacenamiento no predeterminados. Vea [Propiedades de servidor en Analysis Services](../../../analysis-services/server-properties/server-properties-in-analysis-services.md) para obtener más información.  
  
## <a name="command-line-setup"></a>Instalación de línea de Comandos  
 El programa de instalación de SQL Server incluye un parámetro (**ASSERVERMODE**) que especifica el modo de servidor. En el siguiente ejemplo se muestra una instalación de la línea de comandos que instala Analysis Services en modo de servidor tabular.  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 **INSTANCENAME** debe tener menos de 17 caracteres.  
  
 Todos los valores de cuenta de marcador de posición se deben reemplazar con cuentas y contraseñas válidas.  
  
 **ASSERVERMODE** distingue entre mayúsculas y minúsculas.  Todos los valores se deben expresar en mayúsculas. En la tabla siguiente se describen los valores válidos de **ASSERVERMODE**.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|TABULAR|Este es el valor predeterminado. Si no establece **ASSERVERMODE**, el servidor está instalado en modo Tabular.|
|MULTIDIMENSIONAL|Este valor es opcional.|  
|POWERPIVOT|Este valor es opcional. En ejercicio, si establece el parámetro **ROLE** , el modo de servidor se establece automáticamente en 1, haciendo que **ASSERVERMODE** sea opcional en una instalación de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] para SharePoint. Para obtener más información, consulte [Instalar Power Pivot desde el símbolo del sistema](http://msdn.microsoft.com/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328).|  
  
  
## <a name="see-also"></a>Vea también  
 [Determinar el modo de servidor de una instancia de Analysis Services](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Modelado tabular](https://msdn.microsoft.com/library/hh212945(v=sql.110).aspx)  
  
  
