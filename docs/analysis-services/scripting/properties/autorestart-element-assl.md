---
title: Elemento AutoRestart (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AutoRestart Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AutoRestart
helpviewer_keywords: AutoRestart element
ms.assetid: 4c6a0e40-8e13-4d63-bf98-9470ffe95d02
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 20afdbf4888c717eb33caa22c8760ac4183cbe14
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="autorestart-element-assl"></a>Elemento AutoRestart (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina si un [seguimiento](../../../analysis-services/scripting/objects/trace-element-assl.md) elemento debería reiniciar automáticamente si el [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] servicio se detiene y reinicia.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Trace>  
   ...  
   <AutoRestart>...</AutoRestart>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Boolean|  
|Valor predeterminado|**False**|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[Seguimiento](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 El elemento que corresponde al elemento primario de **AutoRestart** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Vea también  
 [Traces, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
