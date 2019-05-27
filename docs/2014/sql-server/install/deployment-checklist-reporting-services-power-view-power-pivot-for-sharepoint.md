---
title: 'Lista de comprobación de implementación: Reporting Services, Power View y PowerPivot para SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9a2575c8-06fc-4ef4-9f24-c19e52b1bbcf
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b2c6e28a8c328bd1e38cee2f4cad74802a981aa9
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66095638"
---
# <a name="deployment-checklist-reporting-services-power-view-and-powerpivot-for-sharepoint"></a>Lista de comprobación de implementación: Reporting Services, Power View y PowerPivot para SharePoint
  Use la siguiente lista de comprobación para instalar estas características de BI en la misma granja de SharePoint: PowerPivot para SharePoint, generador de informes, y [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Aunque esta lista de comprobación recomienda un orden de instalación concreto, en la práctica puede instalar estas características prácticamente en cualquier orden. Esta lista de comprobación supone la instalación de los siguientes productos o características:  
  
1.  SharePoint Server 2010 con Service Pack 1 (SP1)  
  
2.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Motor de base de datos  
  
3.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services y complemento de Reporting Services  
  
4.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot para SharePoint  
  
 Después de instalar estas características, podrá hacer lo siguiente.  
  
-   Acceder a los libros de PowerPivot que creó en PowerPivot para Excel a partir de los sitios de SharePoint.  
  
-   Compilar informes de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] interactivos basados en libros de PowerPivot en SharePoint.  
  
-   Crear informes del Generador de informes al iniciar el Generador de informes en SharePoint.  
  
> [!NOTE]  
>  PowerPivot para SharePoint requiere que instale SharePoint 2010 Service Pack 1 (SP1) en la granja de servidores de SharePoint. Si va a instalar el software para proceder a una evaluación, plantéese comenzar con un servidor limpio para que pueda evitar la sobrecarga que supone la actualización de la granja. Actualizar una granja afecta a las operaciones de SharePoint y normalmente requiere un plan cuidadoso. Si su objetivo es instalar PowerPivot para SharePoint lo más rápido posible, siga este método: instale SharePoint 2010, instale SharePoint 2010 SP1 y, a continuación, configure la granja de servidores en un paso posterior. Se evita la actualización porque todavía no está configurada la granja de servidores al instalar SharePoint 2010 SP1.  
>   
>  En esta lista de comprobación, se supone que el paso de configuración de la granja de servidores se realizará durante la configuración de PowerPivot para SharePoint, utilizando la Herramienta de configuración de PowerPivot. Alternativamente, puede utilizar el Asistente para configuración del producto SharePoint si prefiere ese método. Ambos métodos tienen como resultado una granja de servidores operativa que admite PowerPivot para SharePoint.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Debe ser administrador local para ejecutar el programa de instalación de SQL Server.  
  
 SharePoint Server 2010 Enterprise Edition se requiere para PowerPivot para SharePoint. También puede utilizar la edición Enterprise de evaluación.  
  
 Debe instalarse SharePoint Server 2010 SP1. Sin él, no puede configurar la granja de servidores para usar las características de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .  
  
 El equipo debe estar unido a un dominio.  
  
 Debe tener una o más cuentas de usuario de dominio para aprovisionar los servicios. Necesitará las cuentas de usuario de dominio para los siguientes servicios: Servicios web de SharePoint y servicios administrativos, Reporting Services, Analysis Services, Excel Services, servicios de Store seguro y servicio de sistema de PowerPivot. La característica de cuentas administradas en SharePoint requiere cuentas de dominio. El Motor de base de datos se puede aprovisionar utilizando una cuenta virtual, pero todos los demás servicios se deberían ejecutar como un usuario del dominio.  
  
 El nombre de instancia de PowerPivot debe estar disponible. No puede tener una instancia con nombre de PowerPivot existente en el equipo en el que está instalando PowerPivot para SharePoint.  
  
 Si está instalando PowerPivot para SharePoint en una granja existente, debe tener una o más aplicaciones web de SharePoint que estén configuradas para la autenticación en modo clásico. El a los datos PowerPivot solo funcionará si la aplicación web admite la autenticación en modo clásico. Para obtener más información acerca de los requisitos en modo clásico, vea [PowerPivot Authentication and Authorization](../../analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization.md).  
  
 Revise los siguientes temas adicionales para conocer los requisitos del sistema y de las versiones:  
  
-   [Instrucciones para usar las características de SQL Server BI en una granja de servidores de SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
## <a name="steps"></a>Pasos  
 En los siguientes pasos se supone que un administrador va a instalar y configurar el servidor. El usuario del programa de instalación en SharePoint también es el administrador de una granja y, a menudo, el administrador del sitio primario para la colección de sitios predeterminada. Si va a dividir los siguientes pasos entre varias personas, se podrían requerir permisos adicionales para que los siguientes pasos funcionen.  
  
|Paso|Vínculo|  
|----------|----------|  
|Ejecutar la herramienta de preparación de Productos de SharePoint 2010|Debe tener el disco de instalación para SharePoint 2010. La herramienta de preparación es PrerequisiteInstaller.exe en los discos de instalación.|  
|Instalar la edición Enterprise Evaluation o Enterprise de SharePoint Server 2010.|Al instalar SharePoint, puede decidir configurar la granja posteriormente no ejecutando el asistente para la configuración del producto de SharePoint 2010 una vez finalizada la instalación. Para configurar la granja de servidores en espera, podrá usar un [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] instancia del motor de base de datos, que se instala en un paso posterior como servidor de base de datos de la granja de servidores. Para configurar la granja, utilizará la Herramienta de configuración de PowerPivot. Incluye las acciones para aprovisionar la granja si todavía no está configurada.|  
|Instalar SharePoint Server 2010 SP1.|Descargar SP1 desde [ https://support.microsoft.com/kb/2460045 ](https://go.microsoft.com/fwlink/p/?linkID=219697).|  
|Ejecutar el programa de instalación de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] para instalar el Motor de base de datos y PowerPivot para SharePoint.|[Instalar PowerPivot para SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> El paso 1 explica cómo instalar PowerPivot para SharePoint. En este paso, asegúrese de hacer clic en la casilla en la página Rol de instalación que agrega el Motor de base de datos al rol. Si lo hace, agrega el motor de base de datos a la instalación, por lo que puede usar como servidor de base de datos de la granja de servidores al configurar la granja de servidores en el paso siguiente. Sin embargo, si la granja de servidores ya está configurada, puede omitir este paso.<br /><br /> El paso 2 le pide que configure el servidor. Para este paso, elija la herramienta Configuración de PowerPivot. Aunque hay varios enfoques disponibles, utilizar la herramienta de configuración es el más eficaz para una instalación independiente.<br /><br /> Si SharePoint 2010 está instalado pero no configurado, la herramienta preselecciona las acciones que crearán la granja, una aplicación web predeterminada y una colección de sitios raíz. Asegúrese de dejar estas opciones seleccionadas para que se cree la granja. Si ya configuró la granja, la herramienta omitirá estas acciones y solo proporcionará las que sean necesarias para configurar PowerPivot para SharePoint.<br /><br /> El paso 3 le indica que instale la versión SQL Server 2008 R2 del Proveedor OLE DB de Analysis Services. Este paso es importante para admitir las versiones de un libro que se crearon en la versión 2008 R2 de PowerPivot para Excel.|  
|Comprobar que la granja está operativa.|Primero, inicie Administración Central y confirme que está disponible. A continuación, abra el sitio de grupo escribiendo http://localhost.  Debería ver un sitio web del grupo de SharePoint.|  
|Compruebe que PowerPivot para SharePoint estaá operativo|[Comprobar una instalación de PowerPivot para SharePoint](../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md)<br /><br /> Esta tarea confirma el acceso a los datos PowerPivot mediante un libro de ejemplo que se carga.|  
|Ejecutar el programa de instalación de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] para instalar y configurar Reporting Services y el complemento Reporting Services.|[Instalar el modo de SharePoint de Reporting Services para SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)<br /><br /> Opcionalmente, al instalar Reporting Services, puede agregar una instancia adicional de Analysis Services al árbol de características del programa de instalación si desea un segundo recurso para hospedar los datos tabulares. La instancia de Analysis Services adicional se utilizaría para hospedar las bases de datos del modelo tabular que se crea en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Las bases de datos tabulares son un origen de datos válido para los informes de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].<br /><br /> [Instalar Analysis Services en modo tabular](../../analysis-services/instances/install-windows/install-analysis-services.md)|  
|Comprobar que Reporting Services está operativo.|[Verificación de una instalación de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)|  
|(Administradores de sitio) Configure los permisos de SharePoint.|Para agregar, modificar o eliminar elementos en las bibliotecas de SharePoint se requieren permisos Contribuir. El nivel de permisos Ver es suficiente para el acceso de solo lectura a los informes y libros PowerPivot que presentan datos incrustados.<br /><br /> Los libros PowerPivot a los que se tiene acceso como orígenes de datos externos (donde el la dirección URL del libro es una cadena de conexión en otro libro o informe) requieren permisos Leer, que son más altos que los permisos Ver.<br /><br /> Las conexiones de modelo semántico de BI también requerían permisos de Lectura. Podría necesitar crear nuevos niveles de permisos o grupos de SharePoint para obtener los permisos correctos.|  
|(Administradores de sitio) Extender las bibliotecas de documentos|Extender bibliotecas de documentos para utilizar tipos de contenido BI: Informes de modelo semántico de BI conexiones, Reporting Services orígenes de datos compartidos, el generador de informes:<br /><br /> 1) <br />                    **Habilitar la administración de contenido de tipo**. En documentos compartidos u otra biblioteca de documentos, en la pestaña biblioteca, haga clic en **configuración de la biblioteca**. En configuración General, haga clic en **configuración avanzada**. En tipos de contenido, seleccione **Sí** para permitir la administración de tipos de contenido y, a continuación, haga clic en **Aceptar**.<br /><br /> 2) <br />                    **Seleccione los tipos de contenido de BI**. En la pestaña biblioteca, haga clic en **configuración de la biblioteca**. En tipos de contenido, haga clic en **agregar a partir de tipos de contenido de sitio**. En el grupo de tipo de contenido de Business Intelligence, agregue **archivo de conexión de modelo semántico de BI** y **Report Data Source**. Si lo desea, también puede agregar otros tipos de contenido de Reporting Services, como modelo de informe, para habilitar escenarios adicionales de generación de informes.<br /><br /> <br /><br /> Para obtener más información, consulte [agregar BI semántica modelo de conexión de tipo de contenido en una biblioteca de &#40;PowerPivot para SharePoint&#41; ](../../analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library.md) y [Agregar informe Server tipos de contenido en una biblioteca &#40;Reporting Services en El modo integrado de SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).|  
|(Administradores de sitio) Crear archivos de conexión de datos que se utilizan para iniciar [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].|Debe crear una conexión de modelo semántico de BI (.bism) o un origen de datos compartido de Reporting Services (.rsds) como origen de datos para [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Después de crear un archivo de conexión de datos, puede iniciar [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] si usa la conexión de datos como origen de datos.<br /><br /> [Creación de una conexión de modelo semántico de BI a un libro de PowerPivot](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)<br /><br /> [Crear una conexión de modelo semántico de BI a una base de datos de modelo tabular](../../relational-databases/databases/model-database.md)<br /><br /> Nota: [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] está disponible porque instaló la versión [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] de Reporting Services y configuró el servidor como un servicio compartido. Si instaló Reporting Services y lo configuró para el nivel de integración de SQL Server 2008, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] no está disponible.|  
  
## <a name="see-also"></a>Vea también  
 [Características compatibles con las ediciones de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)  
  
  
