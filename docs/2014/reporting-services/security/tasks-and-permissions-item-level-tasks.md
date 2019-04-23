---
title: Tareas de nivel de elemento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- item-level tasks [Reporting Services]
ms.assetid: fdeb7bc3-167a-4342-84e3-32e3faa1fa39
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62009c07a7b643a3a9d0a202588f64bded967acb
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59934261"
---
# <a name="item-level-tasks"></a>Tareas de nivel de elemento
  Una tarea de nivel de elemento es una recopilación de permisos que relacionan con un informe, carpeta, modelo de informe, recurso u origen de datos compartido. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] también incluye tareas de nivel de sistema que se aplican en el sitio del servidor de informes en conjunto. Para más información, vea [Tareas de nivel de sistema](tasks-and-permissions-system-level-tasks.md). Para obtener más información acerca de tareas y permisos en general, vea [Tasks and Permissions](tasks-and-permissions.md).  
  
> [!NOTE]  
>  Si trabaja con estas tareas en programación, debe utilizar métodos que admitan tareas de nivel de elemento. Para más información, vea <xref:ReportService2010.ReportingService2010.ListTasks%2A> y <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-item-level-tasks"></a>Permisos en tareas de nivel de elemento  
 La siguiente tabla muestra las tareas de nivel de elemento, los permisos que se incluyen en cada tarea y los elementos a los que se aplican los permisos. Los permisos se incluyen con fin informativo únicamente, para proporcionar una descripción más exacta de la funcionalidad disponible con cada tarea.  
  
 Los conjuntos de datos compartidos utilizan el mismo conjunto de permisos como informes. Los elementos de informe utilizan el mismo conjunto de permisos como recursos.  
  
|Tarea|Se aplica al elemento|Permisos|  
|----------|---------------------|-----------------|  
|Usar informes|Informes|Leer contenido<br /><br /> Leer definiciones de informe<br /><br /> Leer propiedades|  
|Usar informes|Conjuntos de datos compartidos|Leer contenido<br /><br /> Leer definiciones de informe<br /><br /> Leer propiedades|  
|Crear informes vinculados|Informes|Crear vínculo<br /><br /> Leer propiedades|  
|Administrar todas las suscripciones|Informes|Leer propiedades<br /><br /> Leer cualquier suscripción<br /><br /> Crear cualquier suscripción<br /><br /> Eliminar cualquier suscripción<br /><br /> Actualizar cualquier suscripción|  
|Administrar orígenes de datos|Carpetas|Crear origen de datos|  
|Administrar orígenes de datos|Orígenes de datos|Actualizar propiedades<br /><br /> Eliminar contenido de actualización<br /><br /> Leer propiedades|  
|Administrar carpetas|Carpetas|Crear carpeta<br /><br /> Eliminar propiedades de actualización<br /><br /> Leer propiedades|  
|Administrar suscripciones individuales|Informes|Leer propiedades<br /><br /> Crear suscripción<br /><br /> Eliminar suscripción<br /><br /> Leer suscripción<br /><br /> Actualizar suscripción|  
|Administrar modelos|Carpetas|Crear modelo|  
|Administrar modelos|Modelos|Leer propiedades<br /><br /> Leer contenido<br /><br /> Eliminar contenido de actualización<br /><br /> Leer orígenes de datos<br /><br /> Actualizar orígenes de datos<br /><br /> Leer directivas de autorización de elemento de modelo<br /><br /> Actualizar directivas de autorización de elemento de modelo<br /><br /> Eliminar propiedades de actualización|  
|Administrar historial de informe|Informes|Leer propiedades<br /><br /> Crear historial de informe<br /><br /> Eliminar historial de informe<br /><br /> Ejecutar lectura de directiva<br /><br /> Actualizar directiva<br /><br /> Mostrar historial de informe|  
|Administrar informes|Carpetas|Crear informe<br /><br /> también se aplica a la creación de conjuntos de datos compartidos|  
|Administrar informes|Informes|Leer propiedades<br /><br /> Eliminar propiedades de actualización<br /><br /> Actualizar parámetros<br /><br /> Leer orígenes de datos<br /><br /> Actualizar orígenes de datos<br /><br /> Leer definición de informe<br /><br /> Actualizar definición de informe<br /><br /> Ejecutar lectura de directiva<br /><br /> Actualizar directiva|  
|Administrar informes|Conjuntos de datos compartidos|Leer propiedades<br /><br /> Eliminar propiedades de actualización<br /><br /> Actualizar parámetros<br /><br /> Leer orígenes de datos<br /><br /> Actualizar orígenes de datos<br /><br /> Leer definición de informe<br /><br /> Actualizar definición de informe<br /><br /> Ejecutar lectura de directiva<br /><br /> Actualizar directiva|  
|Administrar recursos|Carpetas|Crear recurso|  
|Administrar recursos|Recursos|Actualizar propiedades<br /><br /> Eliminar contenido de actualización<br /><br /> Leer propiedades|  
|Administrar recursos|Elementos de informe|Actualizar propiedades<br /><br /> Eliminar contenido de actualización<br /><br /> Leer propiedades|  
|Establecer la seguridad de elementos individuales|Informes, recursos, orígenes de datos, conjuntos de datos compartidos, carpetas|Leer directivas de seguridad, Actualizar directivas de seguridad|  
|Ver orígenes de datos|Orígenes de datos|Leer contenido<br /><br /> Leer propiedades|  
|Ver carpetas|Carpetas|Leer propiedades<br /><br /> Ejecutar y ver<br /><br /> Mostrar historial de informe|  
|Ver modelos|Modelos de informe|Leer propiedades<br /><br /> Leer contenido<br /><br /> Leer orígenes de datos|  
|Ver informes|Informes|Leer contenido<br /><br /> Leer propiedades|  
|Ver informes|Conjuntos de datos compartidos|Leer contenido<br /><br /> Leer propiedades|  
|Ver recursos|Recursos|Leer contenido<br /><br /> Leer propiedades|  
|Ver recursos|Elementos de informe|Leer contenido<br /><br /> Leer propiedades|  
  
## <a name="see-also"></a>Vea también  
 [Concesión de permisos en un servidor de informes en modo nativo](granting-permissions-on-a-native-mode-report-server.md)  
  
  
