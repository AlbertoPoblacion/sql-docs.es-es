---
title: '&lt;consulta de origen de datos&gt; | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 83dbe0c2ea6eb066f208223acd2c6062f964fcf3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938087"
---
# <a name="ltsource-data-querygt"></a>&lt;consulta de origen de datos&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Para entrenar un modelo de minería de datos y crear predicciones a partir de un modelo de minería de datos, debe tener acceso a datos externos a la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de datos. Usa el \<consulta de origen de datos > cláusula minería de datos extensiones (DMX) para definir esos datos externos. El [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md), [SELECT FROM &#60;modelo&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), y [SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) todas las instrucciones usan  **\<consulta de origen de datos >** .  
  
## <a name="query-types"></a>Tipos de consulta  
 Las tres formas más habituales de especificar datos de origen son:  
  
 [OPENQUERY &#40;DMX&#41;](../dmx/source-data-query-openquery.md)  
 Esta instrucción consulta datos externos a una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usando un origen de datos existente.  
  
 Mientras **OPENQUERY** es una función similar a **OPENROWSET**, **OPENQUERY** tiene las siguientes ventajas:  
  
-   Es mucho más fácil escribir con una consulta DMX **OPENQUERY**. En lugar de crear una nueva cadena de conexión cada vez que se escribe una consulta, puede aprovechar la cadena de conexión existente del origen de datos. El objeto de origen de datos también puede controlar el acceso a datos para usuarios individuales.  
  
-   El administrador dispone de más control sobre el modo de acceso a los datos del servidor. Por ejemplo, el administrador puede administrar los proveedores que se cargan en el servidor y los datos externos a los que se puede obtener acceso.  
  
 [OPENROWSET &#40;DMX&#41;](../dmx/source-data-query-openrowset.md)  
 Esta instrucción consulta datos externos a una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usando un origen de datos existente.  
  
 [FORMA &#40;DMX&#41;](../dmx/source-data-query-shape.md)  
 Esta instrucción consulta varios orígenes de datos para crear una tabla anidada. Mediante el uso de **forma**, puede combinar datos de varios orígenes en una única tabla jerárquica. Esto le permite aprovechar la capacidad de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de anidar tablas incrustando una tabla dentro de otra tabla.  
  
 Para especificar los datos de origen, también puede usar las siguientes opciones:  
  
-   Cualquier instrucción DMX válida  
  
-   Cualquier instrucción MDX (Expresiones multidimensionales) válida  
  
-   Una tabla que devuelve un procedimiento almacenado  
  
-   Un conjunto de filas de XML for Analysis (XMLA)  
  
-   Un parámetro de conjunto de filas  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de minería de datos &#40;DMX&#41; instrucciones de manipulación de datos](../dmx/dmx-statements-data-manipulation.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de instrucciones](../dmx/data-mining-extensions-dmx-statements.md)   
 [Tablas anidadas &#40;Analysis Services - minería de datos&#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
