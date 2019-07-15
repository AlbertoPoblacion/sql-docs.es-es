---
title: Elemento DTAXML (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8bc5977952c32fdf4fa6b81bae20068ab47bb97a
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729410"
---
# <a name="dtaxml-element-dta"></a>DTAXML (DTA, elemento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El elemento raíz de un archivo de entrada o salida XML del Asistente para la optimización de motor de base de datos, **DTAXML** , contiene todos los elementos que describen la entrada y la salida de optimización que genera el Asistente para la optimización de motor de base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>Atributos del elemento  
  
|Attribute|Descripción|  
|---------------|-----------------|  
|**xmlns:xsi**|Requerido. Identifica el espacio de nombres de la instancia del esquema XML. Los atributos de este espacio de nombres se utilizan para hacer referencia al esquema usado para validar el archivo XML del Asistente para la optimización de motor de base de datos.<br /><br /> Valor requerido: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Requerido. Identifica el espacio de nombres del Asistente para la optimización de motor de base de datos.<br /><br /> Si se modifica el archivo XML del Asistente para la optimización de motor de base de datos mediante el editor XML de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], este valor es utilizado por F1 Ayuda y la Ayuda dinámica para encontrar posibles temas de referencia en los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Valor requerido:<br /><br /> Espacio de nombres del[Esquema XML del Asistente para la optimización de motor de base de datos](https://go.microsoft.com/fwlink/?LinkId=43100)|  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Una obligatoria por archivo XML DTA|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|None|  
|**Elementos secundarios**|[DTAInput &#40;DTA, elemento&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> Elemento **DTAOutput** (para obtener información, vea [Database Engine Tuning Advisor XML schema (Esquema XML del Asistente para la optimización de motor de base de datos)](https://schemas.microsoft.com/sqlserver/)).|  
  
## <a name="remarks"></a>Notas  
 Para obtener más información acerca de los espacios de nombres XML, vea el artículo sobre [espacios de nombres en un documento XML](https://go.microsoft.com/fwlink/?LinkId=7341) en [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="example"></a>Ejemplo  
 Para ver ejemplos de elementos **DTAXML** típicos, consulte [Ejemplos de archivos de entrada XML &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Iniciar y utilizar el Asistente para la optimización de motor de base de datos](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
