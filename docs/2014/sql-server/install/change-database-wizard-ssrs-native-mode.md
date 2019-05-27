---
title: Cambiar el Asistente para la base de datos (modo nativo de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc07e94db985ce156fdd5cd59620c2e7fddc2d73
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096668"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Cambiar el asistente para la base de datos (Modo nativo de SSRS)
  El Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] proporciona el Asistente para cambiar base de datos que le guía por los pasos para crear una nueva base de datos del servidor de informes o para seleccionar una base de datos del servidor de informes existente que se usará con la instancia actual del servidor de informes.  
  
 Si selecciona una base de datos de una versión anterior, se actualizará para que coincida con la versión de la sesión del servidor de informes a la que está conectado. Cuando el servicio se inicia, comprueba la versión de la base de datos y la actualiza automáticamente al esquema actual.  
  
 Para iniciar el asistente, haga clic en **Cambiar base de datos** en la página Base de datos del Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para obtener instrucciones sobre cómo iniciar el [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, vea [Reporting Services Configuration Manager &#40;modo nativo&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
 **Acción**  
 Seleccione la tarea que desea realizar. Puede crear una base de datos nueva en modo nativo o integrado de SharePoint. O bien, puede seleccionar una base de datos existente para utilizarla con la sesión del servidor de informes actual.  
  
 **Servidor de base de datos**  
 Especifique el nombre de la sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] que hospeda la base de datos del servidor de informes. Puede utilizar una instancia predeterminada o con nombre en un equipo local o remoto. Si se conecta a una instancia con nombre, escriba el nombre del servidor en este formato: \< *server*>\\<*instancia*>.  
  
 Para conectarse a la instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , debe usar credenciales que tengan permiso para iniciar sesión en el servidor y para actualizar la información de las bases de datos. El Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa sus credenciales actuales de Windows, pero si no tiene permisos de inicio de sesión o de base de datos, debe especificar un inicio de sesión de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . No puede especificar credenciales de Windows diferentes. Si desea conectarse como otro usuario de Windows, inicie sesión como ese usuario y, a continuación, inicie el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 La conexión a una sesión remota requiere que primero habilite en dicha sesión las conexiones remotas. Algunas versiones y ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no habilitan las conexiones remotas de forma predeterminada. Para confirmar si se permiten las conexiones remotas, use el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y confirme que los protocolos TCP/IP y Canalizaciones con nombre están habilitados. Si la instancia remota es también una instancia con nombre, compruebe que el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser está habilitado y ejecutándose en el servidor de destino. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser proporciona el número de puerto que usa la instancia con nombre en el Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 **Base de datos**  
 Especifica el nombre de la base de datos del servidor de informes que almacena los datos del servidor. Puede especificar una base de datos existente o crear una nueva.  
  
 Las propiedades que se utilizan para crear una base de datos nueva aparecen en el asistente al seleccionar **Crear nueva base de datos** en la página Acciones. El Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] crea dos bases de datos que están enlazadas por el nombre: una que contiene datos estáticos y otra temporal que almacena datos de sesión y de trabajo. Para obtener más información, consulte [base de datos de servidor de informes &#40;modo nativo de SSRS&#41; ](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libros en pantalla.  
  
 También puede elegir una base de datos del servidor de informes existente. El Administrador de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] no filtra las bases de datos no válidas. Las bases de datos válidas se basan en el esquema de la base de datos del servidor de informes (no puede seleccionar ninguna base de datos que no contenga las tablas, vistas o procedimientos almacenados necesarios). Si elige una base de datos que se creó para una versión anterior de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], se actualizará al formato actual.  
  
 **Lenguaje**  
 Solo se establece este valor al crearse una base de datos nueva del servidor de informes.  
  
 Con este valor, debe especificar el idioma en que se crean las definiciones y las descripciones de rol. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] proporciona un modelo de autorización basada en roles que incluye un conjunto de roles predefinidos. Estos roles se crean en el idioma que especifique. Los nombres y descripciones de rol nunca aparecen en otros idiomas, ni siquiera si se conecta al servidor de informes con un explorador que tenga una referencia cultural o configuración de idioma que el servidor admita. El idioma que especifica también determina el que se usa para crear el nombre de la carpeta Mis informes y de las carpetas Usuarios que forman parte de la característica Mis informes.  
  
 **Modo de servidor**  
 Una base de datos del servidor de informes admite el modo nativo o el modo integrado de SharePoint. Los modos se excluyen mutuamente.  
  
 Si está creando una base de datos del servidor de informes nueva, debe especificar un modo. El modo que seleccione determinará la estructura de la base de datos del servidor de informes y establecerá la propiedad del servidor de informes `SharePointIntegrated` en `true` o `false`.  
  
 Si está seleccionando una base de datos del servidor de informes diferente, se muestra el modo de la base de datos actual para que se sepa cómo se utiliza.  
  
 **Credenciales**  
 Especifica la cuenta con la que el servidor de informes se conecta a la base de datos del servidor de informes. Los valores válidos incluyen la cuenta de servicio web del servidor de informes, un inicio de sesión de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definido en la instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] que usa para hospedar el servidor de informes o una cuenta de Windows. Si usa una cuenta de Windows, puede especificar una cuenta local (*\<nombreDeEquipo >\\< nombre de usuario\>*) si el servidor de informes y la base de datos están en el mismo equipo o un usuario de dominio cuenta (*\<dominio >\\< nombre de usuario\>*) si están en equipos diferentes en el mismo dominio.  
  
 El servidor de informes creará un inicio de sesión de base de datos y asignará permisos de base de datos a la cuenta que especifique.  
  
 El servidor de informes no crea la propia cuenta. La cuenta que especifique ya debe existir y ser válida en la configuración de implementación. En concreto, si la base de datos está en un equipo remoto y desea utilizar una cuenta de Windows, debe especificar una cuenta que tenga permisos de inicio de sesión en ese equipo.  
  
 Si el equipo está en un dominio diferente o que no sea de confianza, considere usar un inicio de sesión de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para obtener más información acerca de cómo elegir una cuenta, consulte [configurar una conexión de base de datos del servidor de informes &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Resumen**  
 Compruebe la configuración antes de que el programa de instalación configure la conexión.  
  
 **Avanzar y finalizar**  
 Supervise el progreso de cada tarea.  
  
## <a name="see-also"></a>Vea también  
 [Base de datos &#40;modo nativo de SSRS&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Asistente para cambiar credenciales &#40;modo nativo de SSRS&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Crear una base de datos del servidor de informes de modo nativo &#40;Administrador de configuración de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Temas de Ayuda de F1 de administrador de configuración de Reporting Services &#40;modo nativo de SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Configurar una conexión a la base de datos del servidor de informes &#40;Administrador de configuración de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
