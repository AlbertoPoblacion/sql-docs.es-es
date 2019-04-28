---
title: Uso de las propiedades de celda (MDX) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49cf92537bf0289765dca7b3a04c76fe0bf50fd8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800022"
---
# <a name="mdx-cell-properties---using-cell-properties"></a>Propiedades de celdas MDX: uso de las propiedades de celda
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Las propiedades de celda de las expresiones multidimensionales (MDX) contienen información sobre el contenido y el formato de las celdas de un origen de datos multidimensional, como un cubo.  
  
 MDX admite la palabra clave CELL PROPERTIES en una instrucción MDX SELECT para recuperar propiedades de celda intrínsecas. Las propiedades de celda intrínsecas se suelen utilizar para facilitar la presentación visual de los datos de las celdas.  
  
## <a name="cell-properties-keyword-syntax"></a>Sintaxis de la palabra clave CELL PROPERTIES  
 Utilice la siguiente sintaxis para la palabra clave **CELL PROPERTIES** de la instrucción MDX **SELECT** :  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 En la siguiente sintaxis se muestra el formato del valor `<cell_props>` y cómo este usa la palabra clave **CELL PROPERTIES** junto con una o más propiedades de celda intrínsecas:  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>Propiedades de celda intrínsecas compatibles  
 En la siguiente tabla figuran las propiedades de celda intrínsecas compatibles que se utilizan en el valor `<property>` .  
  
|Property|Descripción|  
|--------------|-----------------|  
|**ACTION_TYPE**|Máscara de bits que indica los tipos de acciones de la celda. Esta propiedad admite cualquiera de los siguientes valores:<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> Nota: Acciones de obtención de detalles no se incluyen para las consultas que contienen un conjunto de where cláusula.|  
|**BACK_COLOR**|Color de fondo para mostrar las propiedades **VALUE** o **FORMATTED_VALUE**. Para obtener más información, vea [Contenido de FORE_COLOR y BACK_COLOR &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|**CELL_ORDINAL**|Número ordinal de la celda en el conjunto de datos.|  
|**FONT_FLAGS**|Máscara de bits que detalla los efectos de la fuente. El valor es el resultado de una operación de bits OR de una o varias de las siguientes constantes:<br /><br /> **MDFF_BOLD** = 1<br /><br /> **MDFF_ITALIC** = 2<br /><br /> **MDFF_UNDERLINE** = 4<br /><br /> **MDFF_STRIKEOUT** = 8<br /><br /> <br /><br /> Por ejemplo, el valor 5 representa la combinación de los efectos de fuente negrita (**MDFF_BOLD**) y subrayado (**MDFF_UNDERLINE**).|  
|**FONT_NAME**|Fuente usada para mostrar la propiedad **VALUE** o **FORMATTED_VALUE** .|  
|**FONT_SIZE**|Tamaño de fuente usado para mostrar la propiedad **VALUE** o **FORMATTED_VALUE** .|  
|**FORE_COLOR**|Color de primer plano para mostrar las propiedades **VALUE** o **FORMATTED_VALUE**. Para obtener más información, vea [Contenido de FORE_COLOR y BACK_COLOR &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|**FORMAT**|Equivalente a **FORMAT_STRING**.|  
|**FORMAT_STRING**|Cadena de formato usada para crear el valor de la propiedad **FORMATTED_VALUE**. Para obtener más información, vea [FORMAT_STRING, contenido &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).|  
|**FORMATTED_VALUE**|Cadena de caracteres que representa una visualización con formato de la propiedad **VALUE** .|  
|**LANGUAGE**|Configuración regional a la que se aplicará **FORMAT_STRING** . **LANGUAGE** suele utilizarse para la conversión de moneda.|  
|**UPDATEABLE**|Valor que indica si la celda puede actualizarse. Esta propiedad admite cualquiera de los siguientes valores:|  
||**MD_MASK_ENABLED** (0x00000000)   La celda puede actualizarse.|  
||**MD_MASK_NOT_ENABLED** (0x10000000)   La celda no puede actualizarse.|  
||**CELL_UPDATE_ENABLED** (0x00000001)   La celda puede actualizarse en el conjunto de celdas.|  
||**CELL_UPDATE_ENABLED_WITH_UPDATE** (0x00000002)   La celda puede actualizarse con una instrucción de actualización. La actualización puede no realizarse correctamente si se actualiza una celda hoja no habilitada para escritura.|  
||**CELL_UPDATE_NOT_ENABLED_FORMULA** (0x10000001)   La celda no puede actualizarse porque tiene un miembro calculado entre sus coordenadas; la celda se ha recuperado con un conjunto en la cláusula WHERE. Las celdas pueden actualizarse incluso si tienen una fórmula que incida en el valor de una celda, o si hay una celda calculada activa (en algún punto de la ruta de agregación). Con este escenario, es posible que el valor final de la celda no sea el valor actualizado, puesto que el cálculo afecta al resultado.|  
||**CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE** (0x10000002)   La celda no puede actualizarse porque no se pueden actualizar las medidas que no son de tipo Sum (count, min, max, distinct count, semi-additive).|  
||**CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE** (0 x 10000003) la celda no puede actualizarse porque no existe como tal en la intersección de una medida y un miembro de dimensión no relacionados con el grupo de medida de la medida.|  
||**CELL_UPDATE_NOT_ENABLED_SECURE** (0x10000005)   La celda no puede actualizarse porque está protegida.|  
||**CELL_UPDATE_NOT_ENABLED_CALCLEVEL** (0x10000006)   Reservado para uso futuro.|  
||**CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE** (0x10000007)   La celda no puede actualizarse por motivos internos.|  
||**CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE** (0x10000009)   La celda no puede actualizarse porque no se admite la actualización en dimensiones indirectas, de minería de datos o de modelos de minería de datos.|  
|**VALUE**|Valor sin formato de la celda.|  
  
 Solo son obligatorias las propiedades de celda **CELL_ORDINAL**, **FORMATTED_VALUE**y **VALUE** . Todas las propiedades de celda, intrínsecas o específicas del proveedor, se definen en el conjunto de filas de esquema **PROPERTIES** , incluidos los tipos de datos y la compatibilidad con el proveedor. Para obtener más información sobre el conjunto de filas de esquema **PROPERTIES** , vea [Conjunto de filas MDSCHEMA_PROPERTIES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset).  
  
 De forma predeterminada, si no se usa la palabra clave **CELL PROPERTIES** , las propiedades de celda devueltas son **VALUE**, **FORMATTED_VALUE**y **CELL_ORDINAL** (en este orden). Si se utiliza la palabra clave **CELL PROPERTIES** , se devuelven únicamente las propiedades de celda especificadas explícitamente con la palabra clave.  
  
 En el siguiente ejemplo se muestra el uso de la palabra clave **CELL PROPERTIES** en una consulta MDX:  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 No se devuelven las propiedades de celda de consultas MDX que devuelven conjuntos de filas planas; en este caso, cada celda se representa como si solo se hubiese devuelto la propiedad de celda **FORMATTED_VALUE** .  
  
## <a name="setting-cell-properties"></a>Establecer las propiedades de celda  
 Las propiedades de celda se pueden establecer en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en diversos sitios. Por ejemplo, la propiedad Cadena de formato se puede establecer para medidas normales en la pestaña Estructura de cubo del Editor de cubos en [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]; la misma propiedad puede establecerse para medidas calculadas definidas en el cubo en la pestaña Cálculos del Editor de cubos; las medidas calculadas definidas en la cláusula WITH de una consulta también definen su cadena de formato aquí. La consulta siguiente muestra cómo las propiedades de celda se pueden establecer sobre una medida calculada:  
  
```  
WITH MEMBER MEASURES.CELLPROPERTYDEMO AS [Measures].[Internet Sales Amount]  
, FORE_COLOR=RGB(0,0,255)  
, BACK_COLOR=IIF([Measures].[Internet Sales Amount]>7000000, RGB(255,0,0), RGB(0,255,0))  
, FONT_SIZE=10  
, FORMAT_STRING='#,#.000'  
SELECT MEASURES.CELLPROPERTYDEMO ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS ON 1  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORE_COLOR, BACK_COLOR, FONT_SIZE  
```  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de las consultas MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
