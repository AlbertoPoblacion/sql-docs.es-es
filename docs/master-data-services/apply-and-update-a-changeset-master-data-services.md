---
title: Aplicar y actualizar un conjunto de cambios (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3a6a3cf2-1e77-43d3-a64a-855ae51258e7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 710fb8783b0313a6dd46273ce1821e425f7814d3
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483982"
---
# <a name="apply-and-update-a-changeset-master-data-services"></a>Aplicar y actualizar un conjunto de cambios (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Un conjunto de cambios es una colección de cambios pendientes en los datos maestros. Puede aplicar el conjunto de cambios localmente para ver, agregar, actualizar y eliminar los cambios pendientes en el conjunto de cambios.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** . Para obtener más información, consulte [Permisos del área funcional &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Debe tener por lo menos acceso de actualización a la entidad o a uno de sus atributos.  
  
-   Solo puede ver el conjunto de cambios de su propiedad o el conjunto de cambios enviado para su aprobación si es usted el administrador de la entidad.  
  
-   Solo puede modificar el conjunto de cambios de su propiedad y cuando el estado del conjunto de cambios sea abierto o rechazado.  
  
## <a name="to-apply-and-update-a-changeset"></a>Para aplicar y actualizar un conjunto de cambios  
  
1.  En la página principal de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , seleccione un modelo y una versión y haga clic en **Explorador**.  
  
2.  Haga clic en una entidad en el menú **Entidades** .  
  
3.  En el panel derecho, seleccione **Conjuntos de cambios** y haga doble clic en el conjunto de cambios que quiera ver y cambiar.  
  
4.  Haga clic en **Aplicar**.  
  
     Se aplican los cambios pendientes al miembro de la entidad en la cuadrícula. Los cambios pendientes aparecen resaltados.  
  
     La creación, eliminación y actualización de los miembros implican cambios en el conjunto de cambios.  
  
5.  Para revertir los cambios pendientes, en el panel **Conjuntos de cambios** , haga clic con el botón derecho en la cuadrícula y luego haga clic en **Revertir**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Confirmación o envío de un conjunto de cambios &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>Vea también  
 [Creación de un conjunto de cambios &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Aprobación o rechazo de un conjunto de cambios &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
