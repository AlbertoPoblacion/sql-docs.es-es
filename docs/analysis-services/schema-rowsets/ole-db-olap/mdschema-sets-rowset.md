---
title: Conjunto de filas MDSCHEMA_SETS | Documentos de Microsoft
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
apiname: MDSCHEMA_SETS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d861c23e40464535fbde4b666c2e1429f65c772c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemasets-rowset"></a>Conjunto de filas MDSCHEMA_SETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Describe los conjuntos definidos actualmente en una base de datos, incluidos los juegos de ámbito de sesión.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El **MDSCHEMA_SETS** filas contiene las columnas siguientes.  
  
|Nombre de columna|Indicador de tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|El nombre de la base de datos.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|No compatible.|  
|**RESTRICCIONES OBLIGATORIAS CUBE_NAME**|**DBTYPE_WSTR**|Nombre del cubo.|  
|**SET_NAME**|**DBTYPE_WSTR**|El nombre del conjunto, como se especifica en el **CREATE SET** instrucción.|  
|**ÁMBITO**|**DBTYPE_I4**|Ámbito del conjunto:<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|No compatible.|  
|**EXPRESIÓN**|**DBTYPE_WSTR**|Expresión para el conjunto.|  
|**DIMENSIONES**|**DBTYPE_WSTR**|Lista delimitada por comas de las jerarquías incluidas en el conjunto.|  
|**SET_CAPTION**|**DBTYPE_WSTR**|Etiqueta o título asociado al conjunto. La etiqueta o el título se utilizan principalmente para la presentación.|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Cadena que identifica la ruta de la carpeta que usa la aplicación cliente para mostrar el conjunto. La aplicación cliente define el separador de niveles de carpetas. Para las herramientas y clientes proporcionados por [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barra diagonal inversa (\\) es el separador de niveles. Asignar varias carpetas para mostrar, utilice un punto y coma (;) para separar las carpetas.|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|Contexto para el conjunto. El conjunto puede ser estático o dinámico. Esta columna admite cualquiera de los siguientes valores:<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 El conjunto de filas se ordena en **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El **MDSCHEMA_SETS** se puede restringir el conjunto de filas en las columnas enumeradas en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**RESTRICCIONES OBLIGATORIAS CUBE_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**SET_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**ÁMBITO**|**DBTYPE_I4**|Opcional.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Opcional.<br /><br /> Nota: Una sola jerarquía pueden incluir, y solo los conjuntos con nombre cuyas jerarquías coinciden exactamente con la restricción se devuelven.|  
  
## <a name="see-also"></a>Vea también  
 [OLE DB para los conjuntos de filas de esquema OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
