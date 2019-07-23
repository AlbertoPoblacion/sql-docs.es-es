---
title: Create (DTA, elemento) | Microsoft Docs
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
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3541a007b51d5813a6bc42a977ec31fedf5bab87
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104996"
---
# <a name="create-element-dta"></a>Create (DTA, elemento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Contiene información sobre los índices, las estadísticas o las estructuras de montones de una configuración especificada por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Una obligatoria por cada tipo de estructura de diseño físico (índices, estadísticas o estructuras de montones).|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento Recommendation &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Elementos secundarios**|[Index &#40;DTA, elemento&#41;](../../tools/dta/index-element-dta.md)<br /><br /> Elemento**Statistics** (para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](https://schemas.microsoft.com/sqlserver/) ).<br /><br /> Elemento**Heap** (para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](https://schemas.microsoft.com/sqlserver/) ).|  
  
## <a name="remarks"></a>Notas  
 Este elemento tiene el nombre **CreateTypecomplexType** en el esquema XML del Asistente para la optimización de motor de base de datos. Se utiliza para crear los índices, las estadísticas y las estructuras de montones de una configuración especificada por el usuario. No confunda este elemento **Create** con los otros tipos que se pueden usar para crear vistas (**CreateViewType**) o particiones (**CreatePType**). Vea el [esquema XML del Asistente para la optimización de motor de base de datos](https://schemas.microsoft.com/sqlserver/) para obtener más información sobre estos otros tipos de elementos **Create** .  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso de este elemento, vea [Ejemplo de archivo de entrada XML con configuración especificada por el usuario &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
