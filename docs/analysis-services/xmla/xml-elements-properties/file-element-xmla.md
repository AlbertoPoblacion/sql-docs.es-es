---
title: Archivo de elemento (XMLA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: File Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords: File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dfa962e11cc0beaa830e4f5e21144d52822b8b70
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="file-element-xmla"></a>Elemento File (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Identifica un archivo que va a usar el elemento primario [copia de seguridad](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [restaurar](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando, o por el elemento primario [ubicación](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Copia de seguridad](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ubicación](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [restaurar](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Comentarios  
 El **archivo** elemento contiene un nombre de archivo UNC y el elemento primario determina el uso de la **archivo** elemento.  
  
 Para **copia de seguridad** comandos, el **archivo** elemento determina el nombre del archivo de copia de seguridad creado por el **copia de seguridad** comando. Si no se especifica una ruta de acceso como parte del nombre de archivo, la ruta de acceso especificada en el **BackupDir** propiedad de configuración para la instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] se utiliza. Si el archivo especificado ya existe, se produce un error a menos que la **AllowOverwrite** elemento del elemento primario **copia de seguridad** comando está establecido en **True**.  
  
 Para **restaurar** comandos, el **archivo** elemento determina el nombre del archivo de copia de seguridad que se restaurarán por la **restaurar** comando.  
  
 Para **ubicación** elementos, el **archivo** elemento describe un archivo de copia de seguridad remoto para un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instancia que contiene las particiones remotas. Para obtener más información acerca de la copia de seguridad y restaurar las particiones remotas, consulte [realizar copias de seguridad, restauración y sincronizar bases de datos &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [AllowOverwrite, elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Propiedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
