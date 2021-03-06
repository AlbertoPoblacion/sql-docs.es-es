---
title: Crear un miembro consolidado (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 04/01/2016
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
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c22f62fbb00df745f75d027a756e93f4b6f1ec2
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="create-a-consolidated-member-master-data-services"></a>Crear un miembro consolidado (Master Data Services)
  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cree un miembro consolidado si desea un nodo primario para una jerarquía explícita. Si desea agregar datos de forma masiva, use las tablas de almacenamiento provisional. Para obtener más información, consulte [Importar datos de tablas &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** .  
  
-   Como mínimo, debe tener el permiso **Actualizar** para el objeto de modelo consolidado en la entidad a la que vaya a agregar un miembro, así como el **permiso de creación** para el tipo consolidado debajo de la entidad.  
  
### <a name="to-create-a-consolidated-member"></a>Crear un miembro consolidado  
  
1.  En la página principal de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , en la lista **Modelo** , seleccione un modelo.  
  
2.  En la lista **Versión** , seleccione una versión.  
  
3.  Haga clic en **Explorador**.  
  
4.  En la barra de menús, seleccione **Jerarquías** y haga clic en el nombre de la jerarquía a la que desee agregar un miembro consolidado.  
  
5.  Encima de la cuadrícula, seleccione **Miembros consolidados** o **Todos los miembros consolidados de esta jerarquía** .  
  
6.  En el panel izquierdo, seleccione un nodo raíz o un miembro consolidado en el que desee crear un miembro consolidado.  
  
7.  Haga clic en **Agregar**.  
  
8.  En el panel de la derecha, cumplimente los campos.  
  
9. Opcional. En el cuadro **Anotaciones** , escriba un comentario sobre los motivos por los que se agregó el miembro. Todos los usuarios que tienen acceso al miembro pueden ver la anotación.  
  
10. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Ver también  
 [Crear una jerarquía explícita &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Crear un miembro hoja &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)   
 [Miembros &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Jerarquías explícitas &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
