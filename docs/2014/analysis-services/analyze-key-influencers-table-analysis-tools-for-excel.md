---
title: Analizar Influenciadores clave (herramientas de análisis de tabla para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: df6622abc3a507d917aefd2a8a5a1bf9505a2622
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062258"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a>Analizar influenciadores clave (Herramientas de análisis de tabla para Excel)
  ![Botón de analizar Influenciadores clave en la cinta de opciones](media/tat-aki.gif "botón Analizar Influenciadores clave en la cinta de opciones")  
  
 Con el **analizar Influenciadores clave** herramienta, elija la columna que contiene un resultado de destino, y el algoritmo determinará qué factores han influido más en el resultado.  
  
 La herramienta crea nuevas tablas de datos que informan sobre los factores asociados con cada resultado e ilustra gráficamente la probabilidad de la relación. Puede filtrar las tablas por factores y resultados diferentes para explorar los resultados de forma más minuciosa.  
  
 También puede seleccionar un par de resultados posibles y compararlos. Por ejemplo, puede comparar grupos de consumidores para determinar los posibles factores que influyen en la toma de decisiones.  
  
## <a name="using-the-analyze-key-influencers-tool"></a>Usar la herramienta Analizar influenciadores clave  
  
1.  Abra una tabla de datos de Excel.  
  
2.  En **herramientas de tabla**, en el **analizar** la cinta de opciones, haga clic en **analizar Influenciadores clave.**  
  
3.  Seleccione la columna individual que constituye el objetivo del análisis.  
  
4.  Si lo desea, haga clic en **elegir las columnas que se usará para el análisis**. En el **selección avanzada de columnas** cuadro de diálogo, seleccione las columnas que suelen contener datos relevantes. Para mejorar el rendimiento y la precisión, anule la selección de las columnas que contengan identificadores o nombres, que no son importantes para el análisis de patrones. Haga clic en **Aceptar** para cerrar el **selección avanzada de columnas** cuadro de diálogo.  
  
5.  Haga clic en **Ejecutar**.  
  
     El **analizar Influenciadores clave** herramienta lleva a cabo un análisis de los datos para determinar la configuración óptima y establece automáticamente todos los parámetros.  
  
6.  Si no se detecta ningún modelo, el asistente crea una nueva hoja de cálculo que contiene una descripción del problema.  
  
7.  Si se detectan patrones, el asistente crea un informe en una nueva hoja de cálculo que muestra los patrones. El informe se denomina **Influenciadores clave de \<columna >**. Puede personalizar el informe como se describe en el procedimiento siguiente.  
  
#### <a name="create-a-custom-report"></a>Crear un informe personalizado  
  
1.  En el **distinción basada en influenciadores clave** cuadro de diálogo, seleccione los dos valores que desee comparar seleccionándolos en la **valor 1** y **valor 2** listas desplegables . Por ejemplo, puede comparar los compradores con los no compradores.  
  
2.  Haga clic en **Agregar informe**.  
  
     El asistente crea una nueva hoja de cálculo y agrega una tabla por cada par de comparaciones de factores clave.  
  
3.  Cuando haya terminado de hacer comparaciones, haga clic en **cerrar**.  
  
## <a name="understanding-the-key-influencers-report"></a>Descripción del informe de influenciadores clave  
 Una vez creado el modelo de datos, el **analizar Influenciadores clave** herramienta crea informes que le ayudarán a explorar y comparar los influenciadores clave.  
  
-   El informe del lado izquierdo es el que se ha generado de forma predeterminada. Muestra los predictores más eficaces de la columna de resultados (la variable dependiente).  
  
-   El informe del lado derecho es opcional y puede crearlo comparando dos valores específicos de resultados. Este informe compara a los compradores y a los no compradores.  
  
-   Tenga en cuenta que se agrega una nueva hoja de cálculo para cada informe que cree. Puede mover las tablas una vez creadas; las colocamos en paralelo para la comparación.  
  
 ![DM13](media/dm13-tat-aki-report.gif "DM13")  
  
 **Impacto relativo**  
 La barra sombreada en el primer informe indica la solidez de la asociación de este atributo con el resultado.  
  
 La longitud de la barra indica la probabilidad de que el factor contribuya al resultado; por tanto, cuanto más larga sea la barra sombreada, más fuerte es la asociación.  
  
 **Favorece**  
 En el segundo informe, los valores de destino que se comparan se muestran en dos columnas, con los factores relacionados enumerados en orden de confianza descendente.  
  
-   El **azul** barra muestra los atributos que contribuyen al resultado, "No" (= no compró).  
  
-   El **rojo** barra muestra los atributos que contribuyen al resultado, "Yes" (= compró una bicicleta).  
  
 Los colores de la barra de sombreado son arbitrarios. Puede cambiar estos colores estableciendo las opciones para el diseño de la tabla en Excel.  
  
 En un informe que contrasta dos valores, el segundo informe clasifica los influenciadores clave según el impacto que tienen en los valores deseados.  
  
 Puesto que todos los gráficos se basan en las tablas de Excel, puede filtrar y ordenar para centrarse en resultados o factores específicos.  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a>Más información acerca de la herramienta Analizar influenciadores clave  
 Cuando el **analizar Influenciadores clave** herramienta analiza los datos, hace lo siguiente:  
  
-   Crea una estructura de datos que almacena información clave sobre la distribución de los datos.  
  
-   Crea un modelo usando el algoritmo Bayes Naïve de Microsoft.  
  
-   Crea predicciones que ponen en correlación cada columna de datos con el resultado especificado.  
  
-   Utiliza la puntuación de confianza para cada una de las predicciones a fin de identificar los factores que son más influyentes al generar el resultado pretendido.  
  
-   Crea un informe que describe los influenciadores clave, ordenados por las puntuaciones de confianza.  
  
### <a name="requirements"></a>Requisitos  
 Si la columna de destino contiene valores numéricos continuos, la herramienta segmenta automáticamente los valores numéricos en grupos. Estas agrupaciones representan clústeres de casos que tienen características similares. Sin embargo, los valores numéricos podrían no estar divididos en grupos fáciles de usar. Por ejemplo, el informe puede contener una agrupación como "\<12.85701", mientras que los usuarios del informe normalmente prefieren ver agrupaciones que utilizan números enteros, como 10-19, 20-29 y así sucesivamente.  
  
 Si desea agrupar los datos numéricos de otra forma, debe segmentar los datos de la forma deseada antes de crear el análisis. Por ejemplo, puede usar el [cambiar etiquetas](relabel-sql-server-data-mining-add-ins.md) herramienta en el cliente de minería de datos para Excel crear una nueva etiqueta de agrupación en una columna independiente y, a continuación, usar solo la columna nueva en el análisis.  
  
### <a name="related-tools"></a>Herramientas relacionadas  
 El **minería de datos** cinta proporciona herramientas más avanzadas, incluida la capacidad para personalizar los modelos de minería de datos  
  
 Si guarda el modelo utilizando el **analizar Influenciadores clave** herramienta, puede usar el cliente de minería de datos para examinar el modelo y explorar las relaciones con más detalle. Para obtener información, consulte [examinar modelos en Excel &#40;complementos de minería de datos de SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md). También puede usar Microsoft Office Visio para crear gráficos y diagramas que muestren las relaciones como clúster o como redes de dependencias. Para obtener más información, consulte [solución de problemas de diagramas de minería de datos de Visio datos &#40;complementos de minería de datos de SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Los modelos creados cuando se usan las Herramientas de análisis de tabla se eliminan al cerrar la hoja de cálculo o terminar la conexión con el servidor de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Por tanto, solo puede examinar los modelos mientras la conexión permanezca abierta. No puede representar los modelos en Visio si cierra la conexión o cierra la hoja de cálculo.  
  
 Para obtener más información acerca del algoritmo usado por el **analizar Influenciadores clave** herramienta, vea "Algoritmo de Bayes naive de Microsoft" en libros en pantalla de SQL Server.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de análisis de tabla para Excel](table-analysis-tools-for-excel.md)   
 [Crear un modelo de minería de datos](creating-a-data-mining-model.md)  
  
  
