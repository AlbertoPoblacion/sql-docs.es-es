---
title: Tipo de datos Permission (ASSL) | Documentos de Microsoft
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
apiname: Permission Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Permission
helpviewer_keywords: Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 44d17cefe862e3b454bebfe98194926ef22a6773
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="permission-data-type-assl"></a>Tipo de datos Permission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define un tipo de datos primitivo abstracto que representa información sobre un permiso en particular.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipos de datos básicos|None|  
|Tipos de datos derivados|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md), [DimensionPermission](../../../analysis-services/scripting/data-type/dimensionpermission-data-type-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|None|  
|Elementos secundarios|[Anotaciones](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [descripción](../../../analysis-services/scripting/properties/description-element-assl.md), [identificador](../../../analysis-services/scripting/properties/id-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [nombre ](../../../analysis-services/scripting/properties/name-element-assl.md), [Proceso](../../../analysis-services/scripting/properties/process-element-assl.md), [lectura](../../../analysis-services/scripting/properties/read-element-assl.md), [ReadDefinition](../../../analysis-services/scripting/properties/readdefinition-element-assl.md), [RoleID](../../../analysis-services/scripting/properties/roleid-element-assl.md), [escribir](../../../analysis-services/scripting/properties/write-element-assl.md)|  
|Elementos derivados|None|  
  
## <a name="remarks"></a>Comentarios  
 **Permiso** actúa como el tipo base abstracto de un número de tipos de permisos derivados que se utilizan en una instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Este tipo de datos tiene las validaciones siguientes en el valor 2 (modo de servidor tabular) de DeploymentMode.  
  
-   El valor predeterminado del atributo*Process* se establece en **False**, salvo cuando el usuario dispone del permiso **Actualizar** . Para los usuarios con el permiso **Actualizar** el valor del atributo *Process* se establece en **True**.  
  
-   El valor del atributo*ReadDefinition* se establece en **None**; cualquier otro valor genera un error.  
  
-   El valor del atributo*Read* se establece en **Allowed** para los usuarios con el permiso **Usuario** y en **None** cuyo los usuarios tienen asignado al permiso **Actualizar** ; si un usuario tiene los permisos **Usuario** y **Actualizar** , el atributo se establece en **Allowed**. Para los usuarios con privilegios de administrador, el valor del atributo se establece en **Allowed**.  
  
-   El valor del atributo*Write* se establece en **None**; cualquier otro valor genera un error.  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Vea también  
 [Elemento role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Analysis Services Scripting Language tipos de datos XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
