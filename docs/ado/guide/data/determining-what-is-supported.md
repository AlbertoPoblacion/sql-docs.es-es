---
title: "Determinar qué se admite | Documentos de Microsoft"
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
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31d9ca56af28416f68555511a3d4a8439d370200
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="determining-what-is-supported"></a>Determinar qué se admite
El **admite** método se usa para determinar si un determinado **Recordset** objeto admite un tipo determinado de funcionalidad. Tiene la siguiente sintaxis:  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Comentarios  
 El **admite** método devuelve un valor booleano que indica si el proveedor admite todas las características identificadas por el argumento CursorOptions. Puede usar el **admite** método para determinar qué tipos de funcionalidad de un **Recordset** objeto admite. Si el **Recordset** objeto admite las funcionalidades cuyas constantes correspondientes están en *CursorOptions*, el **admite** método **True**. De lo contrario, devuelve **False**.  
  
 Mediante el **admite** método, puede comprobar la capacidad de la **Recordset** objeto para agregar nuevos registros, usar marcadores, use el **buscar** método, use desplazamiento, use el  **Índice** propiedad así como para realizar actualizaciones por lotes. Para obtener una lista completa de constantes y sus significados, vea [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Aunque la **admite** método puede devolver **True** para una funcionalidad determinada, no garantiza que el proveedor puede ofrecer la funcionalidad en todas las circunstancias. El **admite** método simplemente devuelve si el proveedor puede admitir la funcionalidad especificada, suponiendo que se cumplen ciertas condiciones. Por ejemplo, el **admite** método puede indicar que un **Recordset** objeto admita actualizaciones, aun cuando el cursor se basa en una combinación de varias tablas, algunas de las columnas no son actualizables.
