---
title: Tipo de datos MeasureBinding (ASSL) | Documentos de Microsoft
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
apiname: MeasureBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MeasureBinding
helpviewer_keywords: MeasureBinding data type
ms.assetid: f4dac8a6-7ad6-4edb-8e5b-744bb94ee34c
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bd3e086699fd4debbee6c6469609acf48df4be9c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="measurebinding-data-type-assl"></a>Tipo de datos MeasureBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define un tipo de datos derivado que representa el enlace de una medida para el elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MeasureBinding>  
   <!-- The following elements extend Binding -->  
   <MeasureID>...</MeasureID>  
</MeasureBinding>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo de datos base|[Enlace](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Tipos de datos derivados|None|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|None|  
|Elementos secundarios|[MeasureID](../../../analysis-services/scripting/properties/measureid-element-assl.md)|  
|Elementos derivados|Vea [enlace](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información adicional sobre la **enlace** tipo, incluidas las tablas de objetos de Analysis Services Scripting Language (ASSL) de la **enlace** tipo y la jerarquía de herencia de  **Enlace** tipos, consulte [enlazar el tipo de datos &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Para obtener información general de enlaces de datos en ASSL, vea [orígenes de datos y enlaces &#40; SSAS Multidimensional &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.MeasureBinding>.  
  
## <a name="see-also"></a>Vea también  
 [Analysis Services Scripting Language tipos de datos XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
