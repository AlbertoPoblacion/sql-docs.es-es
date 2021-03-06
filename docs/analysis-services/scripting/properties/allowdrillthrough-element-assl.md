---
title: Elemento AllowDrillThrough (ASSL) | Documentos de Microsoft
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
apiname: AllowDrillThrough Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AllowDrillThrough
helpviewer_keywords: AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: "51"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3863648b3c8978fa8ac3b8ba981c6fa634c30ef0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="allowdrillthrough-element-assl"></a>Elemento AllowDrillThrough (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina si se permite la obtención de detalles en el elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
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
|Elementos primarios|[Elemento MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 Los elementos que corresponden a los elementos primarios de **AllowDrillThrough** en el modelo de objetos de Analysis Management Objects (AMO) son <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, y <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Obtención de detalles en estructuras de minería de datos  
 En [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], puede definir **AllowDrillthrough** permisos para estructuras de minería de datos, así como los modelos de minería de datos. Cuando se asigna este permiso a un rol, cualquier miembro de ese rol puede consultar el modelo de minería de datos y devolver columnas de estructura que no estaban incluidas en el modelo. Por ejemplo, se puede crear un modelo que utiliza solamente estas columnas: clave de clientes, ingresos de clientes y compras de clientes. Si habilita la obtención de detalles en el modelo, los usuarios pueden devolver información en otras columnas de la estructura de minería de datos, como nombres o correos electrónicos de clientes.  
  
 Por consiguiente, para proteger los datos confidenciales, se debe tener precaución al agregar columnas a la estructura de minería de datos. Además, solo se debe conceder el permiso **AllowDrillthrough** en una estructura cuando sea necesario.  
  
 Para obtener detalles en columnas de estructura, utilice una consulta con uno de los formatos siguientes:  
  
 `SELECT * FROM <structure>.CASES`  
  
 o Administrador de configuración de  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Vea también  
 [Elemento role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
