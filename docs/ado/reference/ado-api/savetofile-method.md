---
title: "Método SaveToFile | Documentos de Microsoft"
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
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64fa2093400ac9c003397659be3d9d6f4251eee2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="savetofile-method"></a>Método SaveToFile
Guarda el contenido binario de un [flujo](../../../ado/reference/ado-api/stream-object-ado.md) a un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Parámetros  
 *FileName*  
 A **cadena** valor que contiene el nombre completo del archivo a la que el contenido de la **flujo** se guardarán. Puede guardar en cualquier ubicación local válida o cualquier ubicación tiene acceso a través de un valor UNC.  
  
 *Objeto SaveOptions*  
 A [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) valor que especifica si se debe crear un nuevo archivo por **SaveToFile**, si aún no existe. Valor predeterminado es **adSaveCreateNotExists**. Con estas opciones se puede especificar que se produce un error si el archivo especificado no existe. También puede especificar que **SaveToFile** sobrescribe el contenido actual de un archivo existente.  
  
> [!NOTE]
>  Si se sobrescribe un archivo existente (cuando **adSaveCreateOverwrite** está establecido), **SaveToFile** truncará los bytes del archivo existente original que siguen a la nueva [sobrecargas eléctricas](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Comentarios  
 **SaveToFile** puede utilizarse para copiar el contenido de un **flujo** objeto en un archivo local. No hay ningún cambio en el contenido o las propiedades de la **flujo** objeto. El **flujo** objeto debe estar abierto antes de llamar a **SaveToFile**.  
  
 Este método no cambia la asociación de la **flujo** objeto a su origen subyacente. El **flujo** objeto seguirá estando asociado a la dirección URL original o **registro** que era su origen al abrirse.  
  
 Después de un **SaveToFile** operación, la posición actual ([posición](../../../ado/reference/ado-api/position-property-ado.md)) en la secuencia se establece en el principio de la secuencia (0).  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Open (método) (Stream de ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Save (método)](../../../ado/reference/ado-api/save-method.md)
