---
title: Permisos de objeto de modelo (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d41bad7792d21a5eae26b890bcbbfe43808b3faa
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65489182"
---
# <a name="model-object-permissions-master-data-services"></a>Permisos de objeto del modelo (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Los permisos del objeto de modelo son obligatorios. Determinan los atributos a los que un usuario puede tener acceso en el área funcional del **Explorador** de la interfaz de usuario.  
  
 Por ejemplo, si asigna a un usuario el permiso **Actualizar** para la entidad Product, el usuario puede actualizar todos los atributos de la entidad Product. Si asigna el permiso **Actualizar** a un único atributo, el usuario solo podrá actualizar el atributo.  
  
 Para determinar la seguridad asignada en cada valor de atributo individual, los permisos de objeto de modelo se combinan con los permisos de miembros de jerarquía, que determinan los miembros a los que un usuario puede tener acceso.  
  
 Para conceder a un usuario acceso a un área funcional que no sea el **Explorador**, el usuario debe ser un administrador del modelo, lo que implica también la asignación de permisos de administración en el modelo de objeto. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
 Los permisos del objeto de modelo se asignan en la interfaz de usuario de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], en el área funcional **Permisos de grupos y usuarios** de la pestaña **Modelos**. En esta pestaña, el modelo se representa como una estructura de árbol. Cuando asigne un permiso a un objeto en el árbol, todos los objetos subordinados heredan ese permiso. Para invalidar esa herencia asignando el permiso a objetos individuales.  
  
 Puede asignar una combinación de permisos de lectura, creación, actualización y eliminación o denegación a los objetos de modelo. Si no asigna permisos en la pestaña **Modelos** , el usuario no podrá ver ningún modelo ni ningún dato en [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Práctica recomendada  
 En general, debe asignar el permiso **ALL** al objeto de modelo y después asignar explícitamente permisos a los objetos subordinados.  
  
## <a name="external-resources"></a>Recursos externos  
 Entrada de blog, [Security Improvements](https://go.microsoft.com/fwlink/p/?LinkId=615376)(Mejoras de seguridad), en msdn.com.  
  
## <a name="see-also"></a>Vea también  
 [Asignar permisos de objeto de modelo &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Permisos de modelo &#40;Master Data Services&#41;](../master-data-services/model-permissions-master-data-services.md)   
 [Permisos del área funcional &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)   
 [Permisos de miembros de la jerarquía &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Cómo se determinan los permisos &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
