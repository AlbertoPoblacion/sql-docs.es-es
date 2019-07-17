---
title: Especificar una columna que se usarán como regresor en un modelo | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0cfbe8f17c14518b2acf41bdb9ecf64b1679ffb2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68182345"
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a>Especificar una columna para utilizar como regresor en un modelo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Un modelo de regresión lineal representa el valor del atributo de predicción como resultado de una fórmula que combina las entradas de manera que los datos se ajusten lo más posible a una línea de regresión estimada. El algoritmo acepta solamente valores numéricos como entradas y detecta automáticamente las entradas que proporcionan el ajuste óptimo.  
  
 Sin embargo, se puede especificar que una columna se incluya como regresor agregando el parámetro FORCE_REGRESSOR al modelo y especificando los regresores que se han de usar. Esto se puede realizar en los casos en que el atributo es significativo aunque el efecto sea demasiado bajo para ser detectado por el modelo, o cuando se desee asegurarse de que el atributo se incluya en la fórmula.  
  
 El procedimiento siguiente describe cómo crear un modelo de regresión lineal simple, utilizando los mismos datos de ejemplo que se utilizan para el [tutorial de redes neuronales](http://msdn.microsoft.com/library/42c3701a-1fd2-44ff-b7de-377345bbbd6b). El modelo no es necesariamente robusto, pero muestra cómo se usa el Diseñador de minería de datos para personalizar un modelo de regresión lineal.  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a>Cómo se crea un modelo de regresión lineal simple  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en el **Explorador de soluciones**, expanda **Estructuras de minería de datos**.  
  
2.  Haga doble clic en Call Center.dmm para abrirlo en el diseñador.  
  
3.  En el menú **Modelo de minería de datos** , seleccione **Nuevo modelo de minería de datos**.  
  
4.  Para el algoritmo, seleccione **Regresión lineal de Microsoft**. Para el nombre, escriba **Call Center Regression**.  
  
5.  En la pestaña **Modelos de minería de datos** , cambie el uso de columnas como se indica a continuación. Todas las columnas que no estén en la lista siguiente deben establecerse en **Ignore**, si no lo están.  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Total Operators**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  En el menú **Modelo de minería de datos** , seleccione **Establecer parámetros de algoritmo**.  
  
7.  Para el parámetro, FORCE_REGRESSOR, en la columna **Valor** , escriba los nombres de columna ente corchetes y separados por una coma, como se indica abajo:  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  El algoritmo detectará automáticamente qué columnas son los regresores óptimos. Tan solo es necesario forzar los regresores cuando se desee asegurarse de que una columna esté incluida en la fórmula final.  
  
8.  En el menú **Modelo de minería de datos** , seleccione **Procesar modelo**.  
  
     En el visor, el modelo se representa en un solo nodo que contiene la fórmula de regresión. Se puede ver la fórmula en la **Leyenda de minería de datos**o se pueden extraer los coeficientes para la fórmula mediante el uso de consultas.  
  
## <a name="see-also"></a>Vea también  
 [Algoritmo de regresión lineal de Microsoft](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [Consultas de minería de datos](../../analysis-services/data-mining/data-mining-queries.md)   
 [Referencia técnica del algoritmo de regresión lineal de Microsoft](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [Contenido del modelo de minería de datos para los modelos de regresión lineal &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
