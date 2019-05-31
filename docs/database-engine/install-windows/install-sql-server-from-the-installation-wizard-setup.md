---
title: Instalación de SQL Server 2016 desde el Asistente para la instalación (programa de instalación) | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, steps
- Setup [SQL Server], steps
- SQL Server, installing
ms.assetid: 6ad23de1-2bab-4933-9122-c09f5565028d
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: dfe56c7b445353950529603ec2195e90457c35c9
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993676"
---
# <a name="install-sql-server-from-the-installation-wizard-setup"></a>Instalar SQL Server desde el Asistente para la instalación (programa de instalación)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
En este artículo se describe cómo instalar SQL Server con el Asistente para la instalación. Se aplica a [!INCLUDE[SQLServer2016](../../includes/sssql15-md.md)] y a [!INCLUDE[SQLServer2017](../../includes/sssqlv14-md.md)].

En este artículo se proporciona un procedimiento paso a paso para instalar una nueva instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando el Asistente para la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El Asistente para la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona un único árbol de características para la instalación de todos los componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; de este modo, no tendrá que instalarlos individualmente: Para más información sobre cómo instalar los componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] por separado, vea [Instalar SQL Server](../../database-engine/install-windows/install-sql-server.md#how-to-install-individual-components).  

 En estos otros artículos se documentan otras maneras de instalar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  

-   [Instalar SQL Server desde el símbolo del sistema](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
  
-   [Instalar SQL Server mediante un archivo de configuración](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)  
  
-   [Instalar SQL Server mediante SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
  
-   [Crear un nuevo clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)  
  
-   [Upgrade SQL Server Using the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md) (Actualización de SQL Server mediante el Asistente para instalación [programa de instalación]) 

## <a name="get-the-installation-media"></a>Obtener los medios de instalación

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]
  
## <a name="prerequisites"></a>Prerequisites  
 Antes de instalar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], lea los artículos de [Planear una instalación de SQL Server](../../sql-server/install/planning-a-sql-server-installation.md).  
  
> [!NOTE]  
> En instalaciones locales, debe ejecutar el programa de instalación como administrador. Si instala [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde un recurso compartido remoto, deberá usar una cuenta de dominio que tenga permisos de lectura y ejecución para dicho recurso.  
 
 ###  <a name="bkmk_ga_instalpatch"></a> Requisito de instalación de revisión 

Microsoft ha identificado un problema con la versión concreta de los archivos binarios en tiempo de ejecución de Microsoft VC++ 2013 que instala como requisito previo SQL Server. Si esta actualización de los archivos binarios en tiempo de ejecución de VC++ no se instala, puede que SQL Server experimente problemas de estabilidad en determinados escenarios. Antes de instalar SQL Server, siga las instrucciones de [Notas de la versión de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) para ver si el equipo necesita una revisión para los archivos binarios en tiempo de ejecución de VC.  
  
## <a name="to-install-includessnoversionincludesssnoversion-mdmd"></a>Para instalar [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]  
  
1.  Inserte el medio de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Desde la carpeta raíz, haga doble clic en Setup.exe. Para realizar la instalación desde un recurso compartido de red, localice la carpeta raíz de dicho recurso y, a continuación, haga doble clic en Setup.exe.  
  
2.  El Asistente para instalación ejecuta el Centro de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para crear una nueva instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], haga clic en **Instalación** en el área de navegación del lado izquierdo y, luego, haga clic en **Nueva instalación independiente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o agregar características a una instalación existente**.  

3.  En la página Clave del producto, seleccione una opción para indicar si está instalando una edición gratuita de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o una versión de producción del producto con una clave de PID. Para más información, vea [Ediciones y características admitidas de SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  
  
     Para continuar, haga clic en **Siguiente**.

<!--
The following item is for SQL Server 2019 or greater
-->
  
::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
4.  En la página Términos de licencia, revise el contrato de licencia y, si está de acuerdo, active la casilla **Acepto los términos de licencia y [Declaración de privacidad](https://privacy.microsoft.com/privacystatement)** . Después, haga clic en **Siguiente**.  

::: moniker-end

<!--
The following item is for SQL Server 2016-2017
-->

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"
4.  En la página Términos de licencia, revise el contrato de licencia y, si está de acuerdo, active la casilla **Acepto los términos de licencia** y haga clic en **Siguiente**.  

::: moniker-end

  >[!NOTE]
  > SQL Server transmite la información sobre su experiencia de instalación, así como otros datos de uso y rendimiento para ayudar a Microsoft a mejorar el producto. Para obtener más información acerca de los controles de privacidad y de procesamiento de datos de SQL Server, vea la [declaración de privacidad](https://privacy.microsoft.com/privacystatement) y [Configuración de SQL Server para enviar comentarios a Microsoft](https://docs.microsoft.com/sql/sql-server/sql-server-customer-feedback?view=sql-server-2016).

5.  En la ventana Reglas globales, el procedimiento de instalación avanzará automáticamente hasta la ventana Actualizaciones de productos si no hay ningún error de regla.  
  
6.  La página [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update aparecerá a continuación si la casilla [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update del Panel de control\Todos los elementos de Panel de control\Windows Update\Cambiar configuración no está activada. Si se pone una marca de verificación en la página [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, cambiará la configuración del equipo para incluir las últimas actualizaciones al buscar actualizaciones en Windows Update.  

7.  En la página Actualizaciones del producto se muestran las actualizaciones del producto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] más recientes disponibles. Si no se detectan actualizaciones de producto, el programa de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no muestra esta página y pasa automáticamente a la página **Instalar archivos de instalación** .  

8.  En la página Instalar archivos de instalación, el programa de instalación proporciona el progreso de descarga, extracción e instalación de los archivos de instalación. Si se encuentra una actualización para la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], y se especifica que debe incluirse, esa actualización también se instalará. Si no se encuentra ninguna actualización, el programa de instalación avanzará automáticamente. 
  
9. En **Instalar reglas**, el programa de instalación de SQL Server busca posibles problemas que puedan producirse al ejecutar el programa de instalación. Si se producen errores, haga clic en la columna **Estado** para obtener más información. En caso contrario, haga clic en **Siguiente**. 

10. Si se trata de la primera instalación de SQL Server en el equipo, se omite la página **Tipo de instalación** y la instalación va directamente a la página **Selección de características**. Sin embargo, si SQL Server ya está instalado en el sistema, en el **Tipo de instalación** opte por realizar una instalación nueva o agregar características a una instalación existente. Haga clic en **Siguiente**. 
  
11. En la página **Selección de características**, seleccione los componentes de la instalación. Por ejemplo, para instalar una nueva instancia del motor de base de datos de SQL Server, seleccione **Servicios de Motor de base de datos**.

    Después de seleccionar el nombre de la característica, aparece una descripción de cada grupo del componente en el panel **Descripción de característica** . Puede activar cualquier combinación de casillas. Para obtener más información, vea Ediciones y componentes de [SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) y [SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).
  
     Los requisitos previos para las características seleccionadas se muestran en el panel **Requisitos previos de las características seleccionadas** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] El programa de instalación instalará los requisitos previos que no se hayan instalado todavía durante el paso de instalación que se describe más adelante en este procedimiento.  
  
     Si desea especificar un directorio personalizado para los componentes compartidos, use el campo situado en la parte inferior de la página Selección de características. Para cambiar la ruta de instalación de los componentes compartidos, actualice el nombre de ruta en el campo situado en la parte inferior del cuadro de diálogo o haga clic en **Examinar** para moverse a un directorio de instalación. La ruta de instalación predeterminada es [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)].  
  
     La ruta de acceso especificada para los componentes compartidos debe ser una ruta de acceso absoluta. La carpeta no se debe comprimir ni cifrar. No se admiten las unidades asignadas.  
  
     SQL Server usa dos directorios para las características compartidas:
  
     * Directorio de características compartidas  
  
     * Directorio de características compartidas (x86)  
  
     La ruta de acceso especificada para cada una de las opciones anteriores debe ser diferente.  
  
12. La ventana Reglas de características se pasará automáticamente si se cumplen todas las reglas.  
  
13. En la página Configuración de instancia, especifique si desea instalar una instancia predeterminada o una instancia con nombre. Para obtener más información, vea [Instance Configuration](../../sql-server/install/instance-configuration.md#instance-configuration).  
  
     **Id. de instancia** : de manera predeterminada, el nombre de instancia se usa como identificador de la instancia. Se usa para identificar los directorios de instalación y las claves del Registro para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es así en las instancias predeterminadas y en las instancias con nombre. Con una instancia predeterminada, el nombre y el identificador serían MSSQLSERVER. Para usar un identificador de instancia no predeterminado, especifique un valor diferente en el cuadro de texto **Id. de instancia** .  
  
    > [!NOTE]  
    >  Las instancias independientes típicas de [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)], tanto si son predeterminadas como si son instancias con nombre, no usan un valor no predeterminado para el cuadro **Id. de instancia**.  
  
     Todos los Service Pack y actualizaciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se aplicarán a cada componente de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     **Instancias instaladas:** la cuadrícula muestra las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que están en el equipo en el que se ejecuta el programa de instalación. Si ya hay una instancia predeterminada instalada en el equipo, debe instalar una instancia con nombre de [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)].  
  
     El flujo de trabajo del resto de la instalación depende de las características que haya especificado en la instalación. Dependiendo de las selecciones, es posible que no vea todas las páginas.  
  
14. Use la página Configuración del servidor - Cuentas de servicio para especificar las cuentas de inicio de sesión para los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los servicios reales que se configuran en esta página dependen de las características que se van a instalar.  Para obtener más información acerca de los valores de configuración, vea [Ayuda del Asistente para instalación](../../sql-server/install/instance-configuration.md#serverconfig).
  
     Puede asignar la misma cuenta de inicio de sesión a todos los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , o configurar cada cuenta de servicio individualmente. También puede especificar si los servicios se inician de forma automática o manual, o si están deshabilitados. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recomienda configurar las cuentas de servicio de forma individual para proporcionar a cada servicio los privilegios mínimos; así, los servicios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] obtendrán los permisos mínimos que necesitan para completar sus tareas. Para obtener más información, vea [Configurar los permisos y las cuentas de servicio de Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Para especificar la misma cuenta de inicio de sesión para todas las cuentas de servicio en esta instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], las credenciales se proporcionan en los campos de la parte inferior de la página.  
  
    > [!IMPORTANT]  
    > [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
    
    > [!NOTE]
    > A partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], marque la casilla *Conceder el privilegio de realización de tareas de mantenimiento de volumen al servicio del motor de la base de datos de SQL Server* para permitir que la cuenta de servicio [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] pueda usar [inicialización instantánea de archivos de bases de datos](../../relational-databases/databases/database-instant-file-initialization.md).
  
     Use la página Configuración del servidor - Intercalación para especificar intercalaciones no predeterminadas para [!INCLUDE[ssDE](../../includes/ssde-md.md)] y [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para más información, vea [Compatibilidad con la intercalación y Unicode](../../relational-databases/collations/collation-and-unicode-support.md).  
  
15. Use la pestaña **[!INCLUDE[ssDE](../../includes/ssde-md.md)] Configuración - Configuración del servidor** para especificar lo siguiente:  
  
    -   Modo de Seguridad: seleccione la autenticación de Windows o la autenticación de modo mixto para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si selecciona la autenticación de modo mixto, debe proporcionar una contraseña segura para la cuenta de administrador del sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integrada.  
  
       Una vez que un dispositivo establece una conexión correcta con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el mecanismo de seguridad es el mismo para la autenticación de Windows y para el modo mixto. Para obtener más información, vea [Configuración del motor de base de datos: configuración del servidor](../../sql-server/install/instance-configuration.md#serverconfig).
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administradores: debe especificar al menos un administrador del sistema para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para agregar la cuenta en la que se ejecuta el programa de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , haga clic en **Agregar usuario actual**. Para agregar o quitar cuentas de la lista de administradores del sistema, haga clic en **Agregar** o en **Quitar**y, a continuación, modifique la lista de usuarios, grupos o equipos que tendrán privilegios de administrador para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Use la página **[!INCLUDE[ssDE](../../includes/ssde-md.md)] Configuración - Directorios de datos** para especificar los directorios de instalación no predeterminados. Para instalar en los directorios predeterminados, haga clic en **Siguiente**.  
  
    > [!IMPORTANT]  
    > Si especifica los directorios de instalación no predeterminados, asegúrese de que las carpetas de instalación sean únicas para esta instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ninguno de los directorios de este cuadro de diálogo se debe compartir con los de otras instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Para obtener más información, vea [Configuración del motor de base de datos - Directorios de datos](../../sql-server/install/instance-configuration.md#datadir). 

     Use la pestaña **[!INCLUDE[ssDE](../../includes/ssde-md.md)]Configuración - tempdb** para configurar el tamaño de archivo, el número de archivos, los directorios de instalación no predeterminados y la configuración del crecimiento de archivos para tempdb. Para obtener más información, vea [Configuración del motor de base de datos: TempDB](../../sql-server/install/instance-configuration.md#tempdb).  

     ::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
     Use la pestaña **[!INCLUDE[ssDE](../../includes/ssde-md.md)] Configuración - MaxDOP** para especificar el grado máximo de paralelismo. Esta configuración determina cuántos procesadores puede usar una única instrucción durante la ejecución y se calcula automáticamente el valor recomendado durante la instalación. Para obtener más información, vea [Directrices sobre el grado máximo de paralelismo](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines).
     ::: moniker-end

     Use la página **[!INCLUDE[ssDE](../../includes/ssde-md.md)] Configuración - FILESTREAM** para habilitar FILESTREAM en su instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener más información, vea [Configuración del motor de base de datos - Secuencia de archivo](../../sql-server/install/instance-configuration.md#database-engine-configuration---filestream).  
  
  
16. Use la página Configuración de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] - Aprovisionamiento de cuentas para especificar el modo de servidor y los usuarios o las cuentas que tendrán permisos de administrador para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. El modo servidor determina los subsistemas de memoria y de almacenamiento que se utilizan en el servidor. Tipos diferentes de solución se ejecutan en modos servidor diferentes. Si tiene previsto ejecutar bases de datos multidimensionales de cubo en el servidor, elija la opción predeterminada, el modo servidor multidimensional y de minería de datos. En lo que respecta a los permisos de administrador, debe especificar al menos un administrador del sistema para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para agregar la cuenta en la que se ejecuta el programa de instalación de SQL Server, haga clic en **Agregar usuario actual**. Para agregar o quitar cuentas de la lista de administradores del sistema, haga clic en **Agregar** o **Quitar**y, a continuación, modifique la lista de usuarios, grupos o equipos que tendrán privilegios de administrador para [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para obtener más información sobre los permisos de administrador y de modo de servidor, vea [Configuración de Analysis Services - Aprovisionamiento de cuentas](../../sql-server/install/instance-configuration.md#analysis-services-configuration---account-provisioning).  

    Cuando haya terminado de modificar la lista, haga clic en **Aceptar**. Compruebe la lista de administradores en el cuadro de diálogo de configuración. Cuando la lista esté completa, haga clic en **Siguiente**.

    Use la página Configuración de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] - Directorios de datos para especificar los directorios de instalación no predeterminados. Para instalar en los directorios predeterminados, haga clic en **Siguiente**.  
   
    > [!IMPORTANT]  
    > Si, al instalar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se especifica la misma ruta de directorio para INSTANCEDIR y para SQLUSERDBDIR, el Agente SQL Server y la búsqueda de texto completo no se inician debido a que faltan permisos.  
    >  
    > Si especifica los directorios de instalación no predeterminados, asegúrese de que las carpetas de instalación sean únicas para esta instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ninguno de los directorios de este cuadro de diálogo se debe compartir con los de otras instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
   
    Para obtener más información, vea [Configuración de Analysis Services - Directorios de datos](../../sql-server/install/instance-configuration.md#analysis-services-configuration---data-directories).  
   
17. Use la página Configuración de Distributed Replay Controller para especificar los usuarios a los que desee conceder permisos administrativos para el servicio Distributed Replay Controller. Los usuarios con permisos administrativos tendrán acceso ilimitado al servicio Controlador de Distributed Replay.  
  
     Haga clic en el botón **Agregar usuario actual** para agregar los usuarios a los que desee conceder permisos de acceso para el servicio Distributed Replay Controller. Haga clic en el botón **Agregar** para agregar permisos de acceso para el servicio Distributed Replay Controller. Haga clic en el botón **Quitar** para quitar permisos de acceso del servicio Distributed Replay Controller.  
  
     Para continuar, haga clic en **Siguiente**.  
  
18. Use la página Configuración de Distributed Replay Client para especificar los usuarios a los que desee conceder permisos administrativos para el servicio Distributed Replay Client. Los usuarios con permisos administrativos tendrán acceso ilimitado al servicio Distributed Replay Client.  
  
     **Nombre del controlador** es un parámetro opcional y el valor predeterminado es \<*blank*>. Escriba el nombre del controlador con el que se comunicará el equipo cliente para el servicio Distributed Replay Client. Observe lo siguiente:  
  
    -   Si ya ha configurado un controlador, escriba el nombre del controlador mientras configura cada cliente.  
  
    -   Si aún no ha configurado ningún controlador, puede dejar el nombre del controlador en blanco. Sin embargo, debe escribir manualmente el nombre del controlador en el archivo de **configuración de cliente** .  
  
     Especifique el **Directorio de trabajo** para el servicio Distributed Replay Client. El directorio de trabajo predeterminado es \<*letra de unidad*>:\Archivos de programa\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
     Especifique el **Directorio de resultados** para el servicio Distributed Replay Client. El directorio de resultados predeterminado es \<*letra de unidad*>:\Archivos de programa\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
     Para continuar, haga clic en **Siguiente**.  
  
19. La página Listo para instalar muestra una vista de árbol de las opciones de instalación que se especificaron durante la instalación. En esta página, el programa de instalación indica si la característica de actualización de producto está habilitada o deshabilitada y la versión final de actualización.  
  
     Para continuar, haga clic en **Instalar**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] El programa de instalación instalará primero los requisitos previos necesarios para las características seleccionadas y a continuación realizará la instalación de características.  
  
20. La página Progreso de la instalación muestra el estado para que pueda supervisar el progreso de la instalación durante la ejecución del programa de instalación.  
  
21. Después de la instalación, la página Operación completada proporciona un vínculo al archivo de registro de resumen para la instalación y otras notas importantes. Para completar el proceso de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , haga clic en **Cerrar**.  
  
22. Si el programa indica que se reinicie el equipo, hágalo ahora. Es importante leer el mensaje del Asistente para la instalación tras finalizar el programa de instalación. Para obtener más información, vea [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Configurar la nueva instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Para reducir el área expuesta de un sistema susceptible de recibir ataques, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala y habilita de manera selectiva los servicios y características clave. Para obtener más información, vea [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Validar una instalación de SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)   
 [Reparar una instalación de SQL Server 2016 con errores](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)   
 [Ver y leer los archivos de registro de instalación de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [Actualización a SQL Server 2016 mediante el Asistente para instalación &#40;programa de instalación&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)   
 [Instalar SQL Server 2016 desde el símbolo del sistema](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
  
  
