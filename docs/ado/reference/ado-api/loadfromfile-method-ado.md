---
title: "LoadFromFile (método) (ADO) | Documentos de Microsoft"
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
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 071ba2d6a2aa5af96af07274455a7495a9650dea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile (método) (ADO)
Carga el contenido de un archivo existente en un [flujo](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Parámetros  
 *FileName*  
 A **cadena** valor que contiene el nombre de un archivo que se va a cargar en el **flujo**. *Nombre de archivo* puede contener cualquier ruta de acceso válida y un nombre en formato UNC. Si el archivo especificado no existe, se produce un error en tiempo de ejecución.  
  
## <a name="remarks"></a>Comentarios  
 Este método se puede utilizar para cargar el contenido de un archivo local en un **flujo** objeto. Esto se puede utilizar para cargar el contenido de un archivo local en un servidor.  
  
 El **flujo** objeto ya debe estar abierto antes de llamar a **LoadFromFile**. Este método no cambia el enlace de la **flujo** objeto; todavía se enlazará al objeto especificado por la dirección URL o **registro** con la que el **flujo** originalmente era Abrir.  
  
 **LoadFromFile** sobrescribe el contenido actual de la **flujo** objeto con los datos leídos desde el archivo. Los bytes existentes en el **flujo** se sobrescriben con el contenido del archivo. Los bytes restantes y previamente existentes después de la [sobrecargas eléctricas](../../../ado/reference/ado-api/eos-property.md) creado por **LoadFromFile**, se truncan.  
  
 Después de llamar a **LoadFromFile**, se establece la posición actual hasta el principio de la **flujo** ([posición](../../../ado/reference/ado-api/position-property-ado.md) es 0).  
  
 Dado que pueden agregar 2 bytes al principio de la secuencia para la codificación, el tamaño de la secuencia puede coincide exactamente con el tamaño del archivo desde el que se cargó.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
