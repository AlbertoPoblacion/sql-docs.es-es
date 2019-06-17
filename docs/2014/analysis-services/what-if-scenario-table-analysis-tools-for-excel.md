---
title: Escenario y si (herramientas de análisis de tabla para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fef8ca20bd3e137d21b5121f42a0d7fee82ae4a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66065389"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a>Escenario Y si (Herramientas de análisis de tabla para Excel)
  ![Botón escenario y si en las herramientas de análisis de tabla](media/tat-whatif.gif "botón escenario y si en las herramientas de análisis de tabla")  
  
 El **hipótesis** escenario herramienta analiza patrones en los datos existentes y, a continuación, le permite evaluar el efecto que tendrían los cambios en una columna en el valor de una columna diferente.  
  
 Por ejemplo, se podría estudiar el efecto de una subida del precio de un artículo sobre las ventas totales.  
  
 La herramienta es flexible en cuanto al número de predicciones que se pueden crear. Una vez finalizado el análisis inicial, puede predecir cambios para todos los datos de la tabla o especificar valores de prueba de uno en uno.  
  
## <a name="using-the-what-if-scenario-tool"></a>Usar la herramienta de escenario Y si  
  
1.  Abra una tabla de datos de Excel.  
  
2.  Haga clic en **escenarios**y, a continuación, seleccione **hipótesis**.  
  
3.  En el **escenario** , seleccione la columna que contiene el valor que se va a cambiar y especifique el cambio como un valor específico o como un porcentaje de cambio (ya sea aumenta o disminuye) en los valores actuales.  
  
4.  En el **¿qué ocurre con** , especifique la columna que desea evaluar el efecto.  
  
5.  Si lo desea, haga clic en **elegir las columnas que se usará para el análisis** para seleccionar las columnas que suelen ser útil para realizar una predicción. También se puede anular la selección de las columnas que pueden resultar de poca utilidad a la hora de detectar patrones, como las que contienen identificadores de fila o nombres.  
  
6.  En el **especificar fila o tabla** cuadro, elija si desea que el impacto que se evalúa para la fila seleccionada actualmente sólo, o para el conjunto completo de datos de la tabla.  
  
7.  Si selecciona **en esta fila**, la herramienta muestra el resultado en el cuadro de diálogo. Mientras el cuadro de diálogo permanece abierto, puede modificar las selecciones para probar otros escenarios.  
  
8.  Si selecciona **toda la tabla**, la herramienta muestra un mensaje de estado en el cuadro de diálogo y agrega dos nuevas columnas a la tabla de datos original. Haga clic en **cerrar** para ver los resultados completos en la hoja de cálculo.  
  
### <a name="requirements"></a>Requisitos  
 Esta herramienta utiliza el algoritmo de regresión logística de Microsoft, que admite la predicción de valores numéricos o discretos. Sin embargo, para obtener los mejores resultados, se recomienda seguir las prácticas recomendadas siguientes:  
  
-   Seleccione columnas para el análisis que contengan información útil.  
  
-   Si incluye muy pocas columnas, puede ser difícil obtener un resultado.  
  
-   Si usas el **al valor** opción, debe escribir un valor en el cuadro o seleccione un valor de la lista.  
  
-   Si usas el **porcentaje** , establezca el cambio como un porcentaje de aumento o disminución. El valor predeterminado es 120%, lo que supone un incremento del 20% sobre el valor actual.  
  
> [!NOTE]  
>  Si no establece un valor, se podría producir un error.  
  
## <a name="understanding-the-results-of-what-if-analysis"></a>Descripción de los resultados de un análisis Y si  
 Cuando creas un **hipótesis** escenario, la herramienta hace tres cosas:  
  
-   Crea una estructura de minería de datos que almacena hechos clave sobre los datos de la tabla.  
  
-   Crea un modelo de minería de datos de regresión logística basado en los datos.  
  
-   Crea una consulta de predicción para cada uno de los valores especificados.  
  
 Puede generar todas las predicciones al mismo tiempo mediante la especificación de **toda la tabla**. En ese caso, la herramienta crea dos nuevas columnas en la tabla de datos original.  
  
 Las columnas que se agregan a la tabla contienen dos tipos de información: el valor de predicción dado el cambio y su confianza. La confianza significa la probabilidad de que la predicción sea correcta.  
  
 También se pueden especificar los valores de cambio uno a uno en el cuadro de diálogo y ver las predicciones de forma interactiva. Esto es lo mismo que crear un *consulta de predicción singleton*. Los resultados de la consulta de predicción incluyen la siguiente información: el éxito o el fracaso de la predicción, el valor de predicción y el nivel de confianza. El nivel de confianza aparece como una barra que contiene una línea de puntos. Cuanto más larga sea la línea de puntos, mayor será la confianza en el resultado.  
  
 Por ejemplo, si intenta determinar el efecto de aumentar la edad de sobre su voluntad los clientes a comprar y aumentar la edad en 25, la **hipótesis** herramienta consulta el modelo de minería de datos y devuelve el resultado siguiente:  
  
 **Análisis y si de Purchases Bicycle encontró una solución.**  
  
 **'Purchases Bicycle' = Sí**  
  
 **Confianza: Razonable**  
  
 Dado que este resultado se basa en una fila existente de la tabla de datos, eso significa que, para un cliente concreto, si todos los datos sobre ese cliente permanecen iguales pero la edad se aumenta a 25, probablemente compraría una bicicleta.  
  
 El obtener las predicciones con la tabla de datos original podría facilitar la determinación de si las predicciones son útiles.  
  
## <a name="related-tools"></a>Herramientas relacionadas  
 El Cliente de minería de datos para Excel, que es un complemento independiente que ofrece funciones de minería de datos más avanzadas, incluye asistentes para crear modelos de minería de datos que predicen el comportamiento. Para obtener más información, consulte [crear un modelo de minería de datos](creating-a-data-mining-model.md).  
  
 Para obtener más información acerca del algoritmo usado por el **hipótesis** escenario herramienta, vea el tema "Algoritmo de regresión logística de Microsoft" en libros en pantalla de SQL Server.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de análisis de tablas para Excel](table-analysis-tools-for-excel.md)  
  
  
