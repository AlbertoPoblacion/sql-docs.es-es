---
title: Agregar un grupo
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5c9bbcdca2cdbab0d3d92e90e5b343fda196a027
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812851"
---
# <a name="add-a-group-master-data-services"></a>Agregar un grupo (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Agregue un grupo a la lista **Grupos** en [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] a fin de comenzar el proceso para asignar el permiso a la aplicación web. Para que un usuario del grupo pueda tener acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], debe conceder el permiso de grupo a una o más áreas funcionales, y objetos de modelo.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional **Permisos de usuario y de grupo** .  
  
### <a name="to-add-a-group"></a>Agregar un grupo  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Permisos de usuario y de grupo**.  
  
2.  En la página **Usuarios** de la barra de menús, haga clic en **Administrar grupos**.  
  
3.  Haga clic en **Agregar grupos**.  
  
4.  Escriba el nombre del grupo precedido por el nombre de dominio de Active Directory o por el nombre del equipo servidor, como en *dominio\nombre_grupo* o *equipo\nombre_grupo*.  
  
5.  Si lo desea, haga clic en **Comprobar nombres**.  
  
6.  Haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  Cuando el usuario obtiene acceso por primera vez a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], su nombre se agrega a la lista de usuarios de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="next-steps"></a>Pasos siguientes  
  
-   [Asignar permisos del área funcional &#40;Master Data Services&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
