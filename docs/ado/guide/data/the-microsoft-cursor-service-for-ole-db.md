---
title: El servicio de cursores de Microsoft para OLE DB | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dd9f4b279bd38028bb529dcdd0a49f32ffd7cc7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>El servicio de cursores de Microsoft para OLE DB
Cuando se selecciona un cursor de cliente, o establecer la **CursorLocation** propiedad **adUseClient**, que se está invocando el servicio de cursores de Microsoft para OLE DB. También puede ver referencias a "Client Cursor Engine", que es básicamente lo mismo en el contexto de ADO. Este servicio complementa las funciones de compatibilidad de cursor de proveedores de datos. Como resultado, pueden percibir una funcionalidad relativamente uniforme en todos los proveedores de datos.  
  
 El servicio de cursores para OLE DB hace que las propiedades dinámicas estén disponibles y mejora el comportamiento de ciertos métodos. Por ejemplo, el **optimizar** propiedad dinámica permite la creación de índices temporales para facilitar determinadas operaciones, como el **buscar** método.  
  
 El servicio de cursores habilita la compatibilidad con actualización por lotes en todos los casos. También simula más compatible con tipos de cursor, como los cursores dinámicos, cuando un proveedor de datos solo puede proporcionar cursores menos eficaces, como los cursores estáticos.  
  
## <a name="see-also"></a>Vea también  
 [Servicio de cursores de Microsoft para OLE DB (componente de servicio de ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
