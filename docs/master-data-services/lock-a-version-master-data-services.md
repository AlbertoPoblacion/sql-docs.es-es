---
title: Bloquear una versión
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 693eeda37e65dbf1d83fdf59eaf546e711827b7e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728056"
---
# <a name="lock-a-version-master-data-services"></a>Bloquear una versión (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], bloquee una versión de un modelo para impedir cambios en los miembros del modelo y en sus atributos.  
  
> [!NOTE]  
>  Aunque se bloquee una versión, los superusuarios y administradores del modelo pueden continuar agregando, modificando y quitando miembros. Otros usuarios con permiso en el modelo solo pueden ver los miembros.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 Para realizar este procedimiento:  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   El estado de la versión debe ser **Abierta**.  
  
-   Debe disponer del permiso para tener acceso al área funcional de Administración de versiones. Para obtener más información, consulte [Permisos del área funcional &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-lock-a-version"></a>Para bloquear una versión  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración de versiones**.  
  
2.  En la página **Administrar versiones** , seleccione la fila de la versión que desea bloquear.  
  
3.  Haga clic en **Bloquear**.  
  
4.  En el cuadro de diálogo de confirmación, haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Pasos a seguir  
  
-   [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Confirmar una versión &#40;Master Data Services&#41;](../master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Consulte también  
 [Versiones &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Desbloquear una versión &#40;Master Data Services&#41;](../master-data-services/unlock-a-version-master-data-services.md)  
  
  
