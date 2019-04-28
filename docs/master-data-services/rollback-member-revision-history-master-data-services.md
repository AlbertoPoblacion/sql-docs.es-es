---
title: Reversión del historial de revisiones de miembro (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7616ec615e70015abc671740d7a18b7a18e35c74
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62704460"
---
# <a name="rollback-member-revision-history-master-data-services"></a>Reversión del historial de revisiones de miembro (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cada vez que se cambia un miembro, se registra un historial de revisiones de miembro. Se puede revertir un historial de revisiones de miembro a una versión anterior.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Debe tener permiso para actualizar al menos uno de los atributos del miembro seleccionado. Al revertir un historial de revisiones, todos los valores de atributo que se puedan actualizar se revertirán a los valores de la versión anterior.  
  
-   El historial de revisiones solo está disponible cuando el tipo de registro de transacciones de la entidad es miembro.  
  
 **Para revertir el historial de revisiones de miembro**  
  
1.  En Master Data Manager, haga clic en Explorador.  
  
2.  Elija la entidad y el miembro de la reversión.  
  
3.  Haga clic en **Ver historial**.  
  
4.  Elija la revisión para revertir y luego haga clic en **Revertir**.  
  
## <a name="see-also"></a>Vea también  
 [Historial de revisiones de miembro &#40;Master Data Services&#41;](../master-data-services/member-revision-history-master-data-services.md)   
 [Cambio del tipo de registro de transacciones de entidad &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
