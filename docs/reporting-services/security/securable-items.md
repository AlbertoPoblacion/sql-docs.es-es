---
title: Elementos protegibles | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- securable items [Reporting Services]
- roles [Reporting Services], securable items
- security [Reporting Services], securable items listed
- role-based security [Reporting Services], securable items
ms.assetid: 27f58d4c-5c7b-4947-af5b-0f1fa60faf5f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b55265887b8d824e5e7d90d0fb2108efcf75fdb4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "65570608"
---
# <a name="securable-items"></a>Elementos protegibles
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa la seguridad basada en roles para controlar el acceso a los elementos que se almacenan en un servidor de informes. Cuando concede un acceso de usuario a un servidor de informes, normalmente lo hace creando un par de asignaciones de roles:  
  
-   En el nivel de sitio  
  
-   En Inicio, que es el nodo raíz de la jerarquía de carpetas del servidor de informes  
  
 La seguridad se hereda dentro de la jerarquía de carpetas del servidor de informes. La creación de asignaciones de roles en el nivel de sitio y en la carpeta Inicio establece la herencia de permisos que se extiende a todos los elementos y operaciones en un servidor de informes.  
  
 Se puede invalidar la herencia de permisos definiendo la seguridad de elementos individuales. Entre los elementos que se pueden proteger individualmente se incluyen los siguientes:  
  
-   Carpetas  
  
-   Informes  
  
-   Modelos de informe  
  
-   Recursos  
  
-   Orígenes de datos compartidos  
  
-   Conjuntos de datos compartidos  
  
 Otras construcciones, como programaciones y suscripciones, no se protegen de forma explícita. Las programaciones y suscripciones operan en el contexto de seguridad de un informe.  
  
## <a name="item-descriptions"></a>Descripciones de elementos  
 La siguiente tabla muestra los elementos protegibles y describe sus características.  
  
|Elemento|Características|  
|----------|---------------------|  
|Carpetas|La seguridad de las carpetas se aplica a la carpeta en sí y a los elementos que contiene. La carpeta Inicio es el nodo raíz de la jerarquía de carpetas. La seguridad que establezca para esta carpeta determinará la configuración de seguridad inicial de todas las carpetas, informes, recursos y orígenes de datos compartidos subordinados en la jerarquía de carpetas. Para obtener más información, vea [Proteger carpetas](../../reporting-services/security/secure-folders.md).<br /><br /> Mis informes es una carpeta especial que se protege mediante una asignación de roles implícita basada en un rol dedicado. Para obtener más información, vea [Proteger Mis informes](../../reporting-services/security/secure-my-reports.md).|  
|Informes|Los informes y los informes vinculados se pueden proteger con el fin de controlar la gama de acciones que los usuarios pueden realizar, como cambiar las propiedades de un determinado informe.<br /><br /> El historial del informe se protege a través del informe que contiene el historial. No se pueden proteger instantáneas individuales dentro del historial del informe.<br /><br /> Para obtener más información sobre la seguridad de los informes, vea [Proteger informes y recursos](../../reporting-services/security/secure-reports-and-resources.md).|  
|Modelos de informe|Puede especificar una asignación de roles para todo el modelo de informe o parte de él. Puesto que los modelos de informe pueden ser bastante extensos, es posible que desee proteger los elementos del modelo que se asignan a datos confidenciales.|  
|Recursos|Los recursos se pueden proteger para controlar el acceso al recurso en sí y a sus propiedades.<br /><br /> Solo se pueden proteger como elementos individuales los recursos independientes. Los recursos que estén incrustados en un informe no se pueden proteger independientemente de dicho informe.<br /><br /> Para obtener más información sobre la seguridad de los recursos, vea [Proteger informes y recursos](../../reporting-services/security/secure-reports-and-resources.md).|  
|Orígenes de datos compartidos|Los orígenes de datos compartidos se pueden proteger para limitar el acceso al elemento y sus páginas de propiedades. Para obtener más información, vea [Proteger elementos de orígenes de datos compartidos](../../reporting-services/security/secure-shared-data-source-items.md).|  
|Conjuntos de datos compartidos|Los conjuntos de datos compartidos se pueden proteger para controlar el intervalo de acciones que los usuarios pueden realizar, como ver o cambiar la definición, o cambiar las propiedades de un conjunto de datos compartido determinado.<br /><br /> Para obtener más información, vea [Proteger los elementos de un conjunto de datos compartido](../../reporting-services/security/secure-shared-dataset-items.md).|  
  
## <a name="see-also"></a>Consulte también  
 [Conceder permisos en un servidor de informes en modo nativo](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Crear, eliminar o modificar un rol &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)   
 [Conceder a un usuario acceso a un servidor de informes &#40;Administrador de informes&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [Modificar o eliminar una asignación de roles &#40;Administrador de informes&#41;](../../reporting-services/security/role-assignments-modify-or-delete.md)  
  
  
