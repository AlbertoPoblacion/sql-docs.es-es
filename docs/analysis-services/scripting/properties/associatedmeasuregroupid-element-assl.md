---
title: Elemento AssociatedMeasureGroupID (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AssociatedMeasureGroupID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AssociatedMeasureGroupID
helpviewer_keywords: AssociatedMeasureGroupID element
ms.assetid: a18ff25b-00a2-4ddf-abcc-ef4d52c8a462
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 14ddb275cf2462812fdbed1430a2503f2f79130d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="associatedmeasuregroupid-element-assl"></a>Elemento AssociatedMeasureGroupID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene el identificador de la [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) elemento asociado con un [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) elemento o un [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<CalculationProperty> <!-- or Kpi -->  
   ...  
   <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se aplica a **CalculationProperty** elementos, el **AssociatedMeasureGroupID** propiedad se aplica a los elementos con un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) de *miembro* .  
  
 Los elementos que corresponden a los elementos primarios de **AssociatedMeasureGroupID** en el modelo de objetos de Analysis Management Objects (AMO) son <xref:Microsoft.AnalysisServices.CalculationProperty> y <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Vea también  
 [Calculationproperties, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
