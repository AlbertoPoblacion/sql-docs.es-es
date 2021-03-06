---
title: "Cambiar el tamaño de propiedad (Stream de ADO) | Documentos de Microsoft"
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
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfd7bc505122ec142e61d53cdd3502c8c6ad3075
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="size-property-ado-stream"></a>Propiedad Size (Stream de ADO)
Indica el tamaño de la secuencia en número de bytes.  
  
## <a name="return-values"></a>Valores devueltos  
 Devuelve un **largo** valor que especifica el tamaño de la secuencia en número de bytes. El valor predeterminado es el tamaño de la secuencia, o -1 si no se conoce el tamaño de la secuencia.  
  
## <a name="remarks"></a>Comentarios  
 **Tamaño** puede utilizarse solo con abierta [flujo](../../../ado/reference/ado-api/stream-object-ado.md) objetos.  
  
> [!NOTE]
>  Cualquier número de bits puede almacenarse en un **flujo** objeto, limitado por los recursos del sistema. Si el **flujo** contiene más bits que puede representarse mediante un **largo** valor, **tamaño** se trunca y por lo tanto, no se representen con precisión de la longitud de la **Flujo**.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Propiedad Size (parámetro de ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
