---
title: Propiedades de rol de usuario (Management Studio) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f7c663f1a6d13b910492e21b1bd05145dc2a5833
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65575776"
---
# <a name="user-role-properties-management-studio"></a>Propiedades de rol de usuario (Management Studio)
  Use esta página para ver qué tareas se incluyen en una definición de roles de nivel de elemento. También puede usar esta página para cambiar la lista de tareas o modificar una descripción de roles.  
  
 Una definición de roles de nivel de elemento es una colección con nombre de las tareas que realizan los usuarios respecto a un elemento determinado, es decir, una carpeta, un informe, un recurso o un origen de datos compartido. Las definiciones de roles se asignan a un usuario o grupo para crear una asignación de roles en el Administrador de informes. Las tareas de la definición de roles describen lo que puede hacer el usuario o grupo.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] incluye varias definiciones de roles de nivel de elemento predeterminadas con las que podrá trabajar. Puede modificar las definiciones de roles cambiando la lista de tareas de cada una. Al editar una definición de roles, todas las asignaciones de roles que la incluyan se verán afectadas.  
  
> [!NOTE]  
>  Las asignaciones de roles de usuario solo se usan en un servidor de informes que se ejecuta en modo nativo. Si el servidor de informes se configura para la integración con SharePoint, esta página muestra la información de solo lectura sobre los roles y los niveles de permisos que se definen en el sitio de SharePoint.  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Especifica el nombre de la definición de roles.  
  
 **Descripción**  
 Muestra una descripción de la definición de roles. En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], esta descripción solo resulta visible en esta página. En el Administrador de informes, esta descripción ayuda a los usuarios a decidir si desean usar el rol en una asignación de roles.  
  
 **Tarea**  
 Muestra todas las tareas de nivel de elemento que pueden seleccionarse para esta definición de roles. Puede agregar o quitar elementos de la lista de tareas predefinidas para definir el modo en que los usuarios tienen acceso a un elemento dado a través de ese rol. No puede crear nuevas tareas y no puede modificar tareas existentes. La lista de tareas de una definición de roles solo aparece en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Descripción de la tarea**  
 Proporciona información sobre cada tarea. No puede modificar descripciones de tareas.  
  
## <a name="see-also"></a>Consulte también  
 [Tareas de nivel de elemento](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md)   
 [Definiciones de roles](../../reporting-services/security/role-definitions.md)   
 [Servidor de informes en Management Studio ayuda F1](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Tareas y permisos](../../reporting-services/security/tasks-and-permissions.md)   
 [Roles predefinidos](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
