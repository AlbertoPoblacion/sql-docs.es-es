---
title: Descripción de DMX instrucción Select | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 114f1d52db15cd98298d855714c482d959e86a7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065341"
---
# <a name="understanding-the-dmx-select-statement"></a>Descripción de la instrucción Select de DMX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  El [seleccione](../dmx/select-dmx.md) instrucción es la base para la mayoría de las consultas que crean con extensiones de datos minería de datos (DMX) en [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Puede realizar muchos tipos distintos de tareas, como examinar modelos de minería de datos y realizar predicciones con ellos.  
  
 Siguiente es las tareas que puede completar mediante la **seleccione** instrucción:  
  
-   Examinar un modelo de minería de datos. El conjunto de filas de esquema define la estructura de un modelo.  
  
-   Descubrir los valores posibles de una columna de modelo de minería de datos.  
  
-   Examinar los casos asignados a nodos en un modelo de minería de datos u obtener un caso representativo.  
  
-   Crear predicciones mediante diversas entradas.  
  
-   Copiar modelos de minería de datos.  
  
 Cada una de estas tareas usa un conjunto diferente de datos, que llamaremos un *dominio datos*. Definir el dominio de datos en el **FROM** cláusula de la instrucción.  
  
-   Desea buscar objetos en el propio modelo de minería de datos, como la regla que define un conjunto de datos, o una fórmula empleada para realizar predicciones.  
  
     En ese caso, debe examinar los metadatos almacenados en el propio modelo. Por tanto, el dominio de datos lo forman las columnas del conjunto de filas del esquema de minería de datos.  
  
-   Desea obtener información detallada de los casos usados para generar el modelo.  
  
     En ese caso, debe obtener detalles de la estructura de minería de datos, que es el dominio de datos, y examinar las filas individuales de columnas como Gender, Bike Buyer, etc.  
  
 **IMPORTANTE:** Todo lo que se incluye en la lista de expresiones o en el **donde** cláusula debe proceder del dominio de datos definido por el **FROM** cláusula. No puede mezclar dominios de datos.  
  
##  <a name="Select_Types"></a> Seleccionar tipos  
 La sintaxis de **seleccione** instrucción admite muchas tareas diferentes. Use los patrones siguientes para realizar estas tareas:  
  
-   [Predecir](#Predicting)  
  
-   [Exploración](#Browsing)  
  
-   [Copiar](#Copying)  
  
-   [Obtención de detalles](#Drillthrough)  
  
###  <a name="Predicting"></a> Predecir  
 Puede realizar predicciones basadas en un modelo de minería usando los siguientes tipos de consulta.  
  
 Puede incluir cualquiera de la exploración o de predicción **seleccione** instrucciones dentro de la **FROM** y **donde** cláusulas de una combinación de predicción **seleccione** instrucción.  
  
|Tipo de consulta|Descripción|  
|----------------|-----------------|  
|SELECT FROM [NATURAL] PREDICTION JOIN|Devuelve una predicción que se crea combinando las columnas del modelo de minería de datos con las columnas de un origen de datos interno.<br /><br /> El dominio de este tipo de consulta lo forman las columnas de predicción del modelo y las columnas del origen de datos de entrada.<br /><br /> [SELECT FROM &#60;modelo&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)<br /><br /> [Consultas de predicción &#40;minería de datos&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
|SELECT FROM  *\<modelo >*|Devuelve el estado más probable de la columna de predicción, basándose únicamente en el modelo de minería de datos. Este tipo de consulta es un método abreviado para crear una predicción con una combinación de predicción vacía.<br /><br /> El dominio de este tipo de consulta lo forman las columnas de predicción del modelo.<br /><br /> [SELECT FROM &#60;modelo&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)<br /><br /> [Consultas de predicción &#40;minería de datos&#41;](../analysis-services/data-mining/prediction-queries-data-mining.md)|  
  
 [Volver a tipos Select](#Select_Types)  
  
###  <a name="Browsing"></a> Exploración  
 Puede examinar el contenido de un modelo de minería de datos usando los siguientes tipos de consulta.  
  
|Tipo de consulta|Descripción|  
|----------------|-----------------|  
|SELECT DISTINCT FROM  *\<modelo >*|Devuelve todos los valores de estado del modelo de minería de datos para la columna especificada.<br /><br /> El dominio de datos de este tipo de consulta es el modelo de minería de datos.<br /><br /> [SELECT DISTINCT FROM &#60;modelo &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)<br /><br /> [Consultas de contenido &#40;minería de datos&#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM  *\<modelo >* . CONTENIDO|Devuelve contenido que describe el modelo de minería de datos.<br /><br /> El dominio de datos este tipo de consulta es el conjunto de filas de esquema CONTENT.<br /><br /> [SELECT FROM &#60;modelo&#62;. CONTENIDO &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)<br /><br /> [Consultas de contenido &#40;minería de datos&#41;](../analysis-services/data-mining/content-queries-data-mining.md)|  
|SELECT FROM  *\<modelo >* . DIMENSION_CONTENT|Devuelve contenido que describe el modelo de minería de datos.<br /><br /> El dominio de datos este tipo de consulta es el conjunto de filas de esquema CONTENT.<br /><br /> [SELECT FROM &#60;modelo&#62;. DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)|  
|SELECT FROM  *\<modelo >* . PMML|Devuelve la representación PMML (Lenguaje de marcado de modelos de predicción) del modelo de minería de datos para los algoritmos que admiten esta funcionalidad.<br /><br /> El dominio de este tipo de consulta es el conjunto de filas de esquema PMML.<br /><br /> [Conjunto de filas DMSCHEMA_MINING_MODEL_CONTENT_PMML](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset)|  
  
 [Volver a tipos Select](#Select_Types)  
  
###  <a name="Copying"></a> Copiar  
 Puede copiar un modelo de minería de datos y su estructura de minería de datos asociada a un nuevo modelo y cambiar después el nombre del modelo dentro de la instrucción.  
  
|Tipo de consulta|Descripción|  
|----------------|-----------------|  
|SELECT INTO  *\<nuevo modelo >*|Crea una copia del modelo de minería de datos.<br /><br /> El dominio de este tipo de consulta es el modelo de minería de datos.<br /><br /> [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)|  
  
 [Volver a tipos Select](#Select_Types)  
  
###  <a name="Drillthrough"></a> Obtención de detalles  
 Puede examinar los escenarios (o una representación de los escenarios) que se emplearon para entrenar el modelo usando los siguientes tipos de consulta.  
  
|Tipo de consulta|Descripción|  
|----------------|-----------------|  
|SELECT FROM  *\<modelo >* . CASOS|Devuelve los casos empleados para entrenar el modelo de minería de datos.<br /><br /> El dominio de este tipo de consulta es el modelo de minería de datos.<br /><br /> [SELECT FROM &#60;modelo&#62;. CASOS &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)<br /><br /> [Crear consultas de obtención de detalles usando DMX](../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)|  
|SELECT FROM  *\<modelo >* . SAMPLE_CASES|Devuelve un caso de ejemplo, representativo de los casos empleados para entrenar el modelo de minería de datos.<br /><br /> El dominio de este tipo de consulta es el modelo de minería de datos.<br /><br /> [SELECT FROM &#60;modelo&#62;. SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)|  
|SELECT FROM  *\<estructura >* . CASOS|Devuelve las filas de datos detalladas de la estructura de minería de datos subyacente, aunque algunos detalles no se usaran al entrenar el modelo de minería de datos.<br /><br /> [SELECT FROM &#60;estructura&#62;. CASOS](../dmx/select-from-structure-cases.md)<br /><br /> [Consultas de obtención de detalles &#40;minería de datos&#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md)|  
  
 [Volver a tipos Select](#Select_Types)  
  
## <a name="see-also"></a>Vea también  
 [Referencia de Extensiones de minería de datos &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de instrucciones](../dmx/data-mining-extensions-dmx-statements.md)   
 [Extensiones de minería de datos &#40;DMX&#41; convenciones de sintaxis](../dmx/data-mining-extensions-dmx-syntax-conventions.md)  
  
  
