---
title: Asignar permisos de objeto de modelo (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 03939fad90ad71e00245671d3586282a3eb8cc89
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="assign-model-object-permissions-master-data-services"></a>Asignar permisos de objeto de modelo (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], asigne permisos a los objetos de modelo cuando necesite proporcionar a un usuario o grupo acceso a los datos en el área funcional del **Explorador** de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]o cuando necesite convertir en administrador a un usuario o grupo.  
  
> [!NOTE]  
>  Al asignar el permiso a un modelo, implícitamente se deniega el permiso a todos los otros modelos. Si no asigna permisos del objeto de modelo, el usuario o grupo no pueden tener acceso a ningún dato en el **Explorador**.  
  
## <a name="prerequisites"></a>Prerequisites  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional **Permisos de usuario y de grupo** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Asignar permisos de objeto de modelo  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Permisos de usuario y de grupo**.  
  
2.  En la página **Usuarios** o **Grupos** , seleccione la fila para el usuario o grupo que desea modificar.  
  
3.  Haga clic en **Editar usuario seleccionado**.  
  
4.  Haga clic en la pestaña **Modelos** .  
  
5.  Si lo desea, seleccione un modelo en la lista desplegable **Modelo** .  
  
6.  Haga clic en **Editar**.  
  
7.  Expanda el árbol y haga clic en el objeto de modelo al que desea asignar los permisos.  
  
8.  En el menú, seleccione una combinación de lectura, creación, actualización y eliminación, o denegación.  
  
9. En el nivel superior del modelo, seleccione **Admin** si necesita convertir a un usuario en administrador de modelos.  
  
10. Haga clic en **Guardar**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   (Opcional) [Asignar los permisos de los miembros de una jerarquía &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Ver también  
 [Eliminar permisos de objeto de modelo &#40;Master Data Services&#41;](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Permisos de objeto del modelo &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Crear un administrador de modelo &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
