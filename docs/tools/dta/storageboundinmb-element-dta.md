---
title: StorageBoundInMB (DTA, elemento) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f206c59908ab5c44c1b5026e9c7d6dd054e33f1e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105970"
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB (DTA, elemento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Especifica el espacio máximo en megabytes que puede consumir la recomendación de optimización del Asistente para la optimización de motor de base de datos (conjunto de índices y particiones).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|**unsignedInt**, longitud ilimitada.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Solo puede utilizarse una vez para el elemento **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[TuningOptions &#40;DTA, elemento&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementos secundarios**|None|  
  
## <a name="remarks"></a>Notas  
 Cuando se optimizan varias bases de datos, se tienen en cuenta las recomendaciones para todas las bases de datos sobre el cálculo del espacio. De forma predeterminada, el Asistente para la optimización de motor de base de datos asume el menor de los siguientes tamaños de almacenamiento:  
  
-   Tres veces el tamaño actual de los datos sin procesar, lo que incluye el tamaño total de los montones y los clúster de las tablas.  
  
-   El espacio disponible en todas las unidades de disco adjuntas más el tamaño de los datos sin procesar.  
  
 El tamaño de almacenamiento predeterminado no incluye los índices no clúster ni las vistas indizadas.  
  
 Si el valor especificado para el elemento **StorageBoundInMB** supera el espacio en disco real, el Asistente para la optimización de motor de base de datos devuelve un error, aunque continúa optimizando. Una vez finalizada la optimización, puede agregar espacio en disco si decide seguir la recomendación.  
  
## <a name="example"></a>Ejemplo  
  
## <a name="description"></a>Descripción  
 El siguiente ejemplo de código muestra cómo establecer un límite de 1500 megabytes como el máximo espacio en disco que una recomendación de optimización puede utilizar:  
  
## <a name="code"></a>código  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
