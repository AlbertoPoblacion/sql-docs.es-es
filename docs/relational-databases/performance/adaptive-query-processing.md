---
title: Procesamiento de consultas adaptable en bases de datos de Microsoft SQL | Microsoft Docs | Microsoft Docs
description: Características de procesamiento de consultas adaptable para mejorar el rendimiento de las consultas en SQL Server (2017 y versiones posteriores) y Azure SQL Database.
ms.custom: ''
ms.date: 02/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aba4aa388cb9ffac518b09077d535b618206ab71
ms.sourcegitcommit: 769b71f01052ec9b4fc5eb02d9da9a1a58118029
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56319266"
---
# <a name="adaptive-query-processing-in-sql-databases"></a>Procesamiento de consultas adaptable en bases de datos SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

En este artículo se presentan las características de procesamiento de consultas adaptables que se pueden usar para aumentar el rendimiento de las consultas en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) y [!INCLUDE[ssSDS](../../includes/sssds-md.md)]:
- Comentarios de concesión de memoria de modo de proceso por lotes
- Comentarios de concesión de memoria del modo de filas (versión preliminar pública en el nivel de compatibilidad de base de datos 150)
- Combinación adaptable de modo de proceso por lotes
- Ejecución intercalada

En un nivel general, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ejecuta una consulta del modo siguiente:
1. El proceso de optimización de consultas genera un conjunto de planes de ejecución factibles para una consulta concreta. Durante este tiempo se calcula el costo de las opciones del plan y se usa el plan con el menor costo estimado.
1. El proceso de ejecución de consultas toma el plan elegido por el optimizador de consultas y lo usa para la ejecución.

Para obtener más información sobre el procesamiento de consultas y los modos de ejecución de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea la [Guía de arquitectura de procesamiento de consultas](../../relational-databases/query-processing-architecture-guide.md).

A veces, el plan elegido por el optimizador de consultas no es óptimo por una serie de motivos. Por ejemplo, el número estimado de filas que pasan por el plan de consulta puede ser incorrecto. Los costos estimados ayudan a determinar el plan que se selecciona para la ejecución. Si las estimaciones de cardinalidad son incorrectas, se sigue usando el plan original a pesar de los deficientes supuestos originales.

### <a name="how-to-enable-adaptive-query-processing"></a>Cómo habilitar el procesamiento de consultas adaptable
Puede hacer que las cargas de trabajo sean aptas automáticamente para el procesamiento de consultas adaptable si habilita el nivel de compatibilidad 140 para la base de datos.  Puede establecerlo con Transact-SQL. Por ejemplo:  

```sql
ALTER DATABASE [WideWorldImportersDW] SET COMPATIBILITY_LEVEL = 140;
```

## <a name="batch-mode-memory-grant-feedback"></a>Comentarios de concesión de memoria de modo de proceso por lotes
El plan posterior a la ejecución de una consulta en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] incluye la memoria mínima necesaria para la ejecución y el tamaño de concesión de memoria ideal para que todas las filas quepan en la memoria. El rendimiento se ve afectado si los tamaños de concesión de memoria son incorrectos. A su vez, unas concesiones excesivas se traducen en memoria desperdiciada y en simultaneidad reducida. Las concesiones de memoria insuficientes provocan un costoso desbordamiento en disco. Al ocuparse de las cargas de trabajo repetidas, los comentarios de concesión de memoria de modo de proceso por lotes vuelven a calcular la memoria real necesaria para una consulta y luego actualizan el valor de la concesión del plan almacenado en caché.  Cuando se ejecuta una instrucción de consulta idéntica, la consulta usa el tamaño de concesión de memoria revisado, con lo que se reducen las concesiones de memoria excesivas que afectan a la simultaneidad y se solucionan las concesiones de memoria subestimadas que provocan costosos desbordamientos en disco.
El gráfico siguiente muestra un ejemplo de uso de los comentarios de concesión de memoria adaptable de modo de proceso por lotes. Para la primera ejecución de la consulta, la duración es de  **88 segundos** debido a los grandes desbordamientos:   

```sql
DECLARE @EndTime datetime = '2016-09-22 00:00:00.000';
DECLARE @StartTime datetime = '2016-09-15 00:00:00.000';
SELECT TOP 10 hash_unique_bigint_id
FROM dbo.TelemetryDS
WHERE Timestamp BETWEEN @StartTime and @EndTime
GROUP BY hash_unique_bigint_id
ORDER BY MAX(max_elapsed_time_microsec) DESC;
```

![Grandes desbordamientos](./media/2_AQPGraphHighSpills.png)

Con los comentarios de concesión de memoria habilitados para la segunda ejecución, la duración es de  **1 segundo** (partiendo de 88 segundos), los desbordamientos se eliminan por completo y la concesión es superior: 

![Sin desbordamientos](./media/3_AQPGraphNoSpills.png)

### <a name="memory-grant-feedback-sizing"></a>Tamaño de los comentarios de concesión de memoria
En el caso de una condición de concesión de memoria excesiva, si la memoria concedida es más de dos veces el tamaño de la memoria usada real, los comentarios de concesión de memoria volverán a calcular la concesión de memoria y actualizarán el plan almacenado en caché. Los planes con concesiones de memoria por debajo de 1 MB no se vuelven a calcular para usos por encima del límite.
En el caso de condiciones de concesión de memoria de tamaño insuficiente, que provocan un desbordamiento en disco para operadores de modo de proceso por lotes, los comentarios de concesión de memoria desencadenarán un nuevo cálculo de la concesión de memoria. Los eventos de desbordamiento se notifican a los comentarios de concesión de memoria y se pueden mostrar a través del evento de xEvent *spilling_report_to_memory_grant_feedback*. Este evento devuelve el identificador de nodo del plan y el tamaño de los datos desbordados de ese nodo.

### <a name="memory-grant-feedback-and-parameter-sensitive-scenarios"></a>Comentarios de concesión de memoria y escenarios confidenciales de parámetros
Los distintos valores de parámetros también pueden necesitar diferentes planes de consulta para seguir siendo óptimos. Este tipo de consulta se define como "sensible a parámetros". En el caso de los planes sensibles a parámetros, los comentarios de concesión de memoria se deshabilitarán en una consulta si esta tiene requisitos de memoria inestables. El plan se deshabilita después de que se ejecute la consulta de forma repetida y esto puede observarse mediante la supervisión de xEvent *memory_grant_feedback_loop_disabled*. Para obtener más información sobre la sensibilidad y el examen de los parámetros, consulte la [Guía de arquitectura de procesamiento de consulta](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing).

### <a name="memory-grant-feedback-caching"></a>Almacenamiento en caché de los comentarios de concesión de memoria
Los comentarios pueden almacenarse en el plan almacenado en caché para una sola ejecución. Pero son las ejecuciones consecutivas de esa instrucción las que se benefician de los ajustes de los comentarios de concesión de memoria. Esta característica se aplica a la ejecución repetida de instrucciones. Los comentarios de concesión de memoria solo cambian el plan almacenado en caché. Los cambios no se capturan actualmente en el almacén de consultas.
Si el plan se elimina de la memoria caché, no se conservan los comentarios. Los comentarios también se pierden si se produce una conmutación por error. Una instrucción con `OPTION (RECOMPILE)` crea un plan y no lo almacena en caché. Puesto que no se almacena, no se generan comentarios de concesión de memoria y no se almacenan para esa compilación y ejecución.  Pero si una instrucción equivalente (es decir, con el mismo hash de consulta) que **no** ha usado `OPTION (RECOMPILE)` se ha almacenado en caché y luego se ha vuelto a ejecutar, la instrucción consecutiva puede beneficiarse de los comentarios de concesión de memoria.

### <a name="tracking-memory-grant-feedback-activity"></a>Seguimiento de la actividad de los comentarios de concesión de memoria
Puede realizar un seguimiento de los eventos de comentarios de concesión de memoria mediante el evento de xEvent *memory_grant_updated_by_feedback*. Este evento realiza un seguimiento del historial de recuentos de ejecución actual, del número de veces que los comentarios de concesión de memoria han provocado una actualización del plan, de la concesión de memoria adicional ideal antes de la modificación y de la concesión de memoria adicional ideal después de que los comentarios de concesión de memoria hayan modificado el plan almacenado en caché.

### <a name="memory-grant-feedback-resource-governor-and-query-hints"></a>Comentarios de concesión de memoria, regulador de recursos y sugerencias de consulta
La memoria real concedida respeta el límite de memoria de consulta determinado por el regulador de recursos o la sugerencia de consulta.

### <a name="disabling-batch-mode-memory-grant-feedback-without-changing-the-compatibility-level"></a>Deshabilitar los comentarios de concesión de memoria en modo de lote sin cambiar el nivel de compatibilidad
Los comentarios de concesión de memoria se pueden deshabilitar en el ámbito de base de datos o de instrucción mientras se mantiene el nivel de compatibilidad de base de datos 140 o posterior. Para deshabilitar los comentarios de concesión de memoria en modo por lotes para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK = ON;
```

Cuando se habilita, esta opción aparecerá como habilitada en [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md).

Para volver a habilitar los comentarios de concesión de memoria en modo por lotes para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK = OFF;
```

También puede deshabilitar los comentarios de concesión de memoria en modo por lotes para una consulta específica si designa `DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK` como [sugerencia de consulta USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint). Por ejemplo:

```sql
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (USE HINT ('DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK')); 
```

Una sugerencia de consulta USE HINT tiene prioridad sobre una configuración de ámbito de base de datos o una opción de marca de seguimiento.

## <a name="row-mode-memory-grant-feedback"></a>Comentarios de concesión de memoria del modo de fila
**Se aplica a:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] como característica de versión preliminar pública.

> [!NOTE]
> Los comentarios de concesión de memoria del modo de fila es una característica en vista previa (GB) pública.  

Los comentarios de concesión de memoria del modo de fila se expanden en la característica de comentarios de concesión de memoria de modo de proceso por lotes al ajustar los tamaños de concesión de memoria tanto para los operadores del modo de proceso por lotes como del modo de fila.  

Para habilitar la versión preliminar pública de los comentarios de concesión de memoria del modo de fila en [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], habilite el nivel 150 de compatibilidad de la base de datos para la base de datos a la que se conecta cuando ejecuta la consulta.

La actividad de comentarios de concesión de memoria del modo de fila será visible a través del evento extendido **memory_grant_updated_by_feedback**. 

A partir de los comentarios de concesión de memoria del modo de fila, se mostrarán dos atributos nuevos de plan de consulta para los planes reales posteriores a la ejecución: ***IsMemoryGrantFeedbackAdjusted*** y ***LastRequestedMemory***, que se agregan al elemento XML de plan de consulta *MemoryGrantInfo*. 

*LastRequestedMemory* muestra la memoria concedida en Kilobytes (KB) desde la ejecución de consulta anterior. El atributo *IsMemoryGrantFeedbackAdjusted* permite comprobar el estado de los comentarios de concesión de memoria para la instrucción dentro de un plan de ejecución de consulta real. Los valores que se exponen en este atributo son los siguientes:

| Valor IsMemoryGrantFeedbackAdjusted | Descripción |
|---|---|
| No: First Execution | Los comentarios de concesión de memoria no ajustan la memoria para la primera compilación y la ejecución asociada.  |
| No: Accurate Grant | Si no hay ningún desbordamiento al disco y la instrucción usa al menos 50 % de la memoria concedida, no se desencadenan los comentarios de concesión de memoria. |
| No: Feedback disabled | Si los comentarios de concesión de memoria se desencadenan de manera continúa y fluctúan entre operaciones de aumento de memoria y operaciones de disminución de memoria, se deshabilitarán los comentarios de concesión de memoria para la instrucción. |
| Yes: Adjusting | Se aplicaron los comentarios de concesión de memoria y se pueden seguir ajustando para la próxima ejecución. |
| Yes: Stable | Se aplicaron los comentarios de concesión de memoria y ahora la memoria concedida es estable, lo que significa que lo último que se concedió para la ejecución anterior es lo que se concedió para la ejecución actual. |

> [!NOTE]
> Los atributos del plan de comentarios de concesión de memoria del modo de fila en versión preliminar pública son visibles en los planes de ejecución de consultas gráficas de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en las versiones 17.9 y superiores. 

### <a name="disabling-row-mode-memory-grant-feedback-without-changing-the-compatibility-level"></a>Deshabilitar los comentarios de concesión de memoria en modo de fila sin cambiar el nivel de compatibilidad
Los comentarios de concesión de memoria en modo de fila se pueden deshabilitar en el ámbito de base de datos o de instrucción mientras se mantiene el nivel de compatibilidad de base de datos 150 o posterior. Para deshabilitar los comentarios de concesión de memoria en modo de fila para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ROW_MODE_MEMORY_GRANT_FEEDBACK = OFF;
```

Para volver a habilitar los comentarios de concesión de memoria en modo de fila para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ROW_MODE_MEMORY_GRANT_FEEDBACK = ON;
```

También puede deshabilitar los comentarios de concesión de memoria en modo de fila para una consulta específica si designa `DISABLE_ROW_MODE_MEMORY_GRANT_FEEDBACK` como [sugerencia de consulta USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint). Por ejemplo:

```sql
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (USE HINT ('DISABLE_ROW_MODE_MEMORY_GRANT_FEEDBACK')); 
```

Una sugerencia de consulta USE HINT tiene prioridad sobre una configuración de ámbito de base de datos o una opción de marca de seguimiento.


## <a name="batch-mode-adaptive-joins"></a>Combinaciones adaptables del modo por lotes
La característica de combinaciones adaptables del modo por lotes permite elegir un método [Combinación hash o combinación de bucles anidados](../../relational-databases/performance/joins.md) que se aplace hasta **después** de que se haya examinado la primera entrada. El operador de combinaciones adaptables define un umbral que se usa para decidir cuándo cambiar a un plan de bucles anidados. El plan, por tanto, puede cambiar de forma dinámica para una mejor estrategia de combinación durante la ejecución.
Funcionamiento:
-  Si el recuento de filas de la entrada de combinación de compilación es lo suficientemente pequeño como para que una combinación de bucles anidados sea una opción más óptima que una combinación hash, el plan cambia a un algoritmo de bucles anidados.
-  Si la entrada de combinación de compilación supera un umbral de recuento de filas determinado, no se produce ningún cambio y el plan continúa con una combinación hash.

La siguiente consulta se usa para mostrar un ejemplo de combinación adaptable:

```sql
SELECT [fo].[Order Key], [si].[Lead Time Days], [fo].[Quantity]
FROM [Fact].[Order] AS [fo]
INNER JOIN [Dimension].[Stock Item] AS [si]
       ON [fo].[Stock Item Key] = [si].[Stock Item Key]
WHERE [fo].[Quantity] = 360;
```

La consulta devuelve 336 filas. Al habilitar las [estadísticas de consultas activas](../../relational-databases/performance/live-query-statistics.md) se ve el siguiente plan:

![La consulta da lugar a 336 filas](./media/4_AQPStats336Rows.png)

En el plan se ve lo siguiente:
1. Hay una exploración de índice de almacén de columnas que se usa para proporcionar filas para la fase de compilación de combinación hash.
1. Hay un nuevo operador de combinación adaptable. Este operador define un umbral que se usa para decidir cuándo cambiar a un plan de bucle anidado. En el ejemplo, el umbral es 78 filas. Todo lo que tenga &gt; = 78 filas usará una combinación hash. Si es inferior al umbral, se usará una combinación de bucle anidado.
1. Puesto que se devuelven 336 filas, se supera el umbral y la segunda rama representa la fase de sondeo de una operación de combinación hash estándar. Observe que las estadísticas de consultas dinámicas muestran las filas que pasan por los operadores, en este caso "672 de 672".
1. La última rama es la búsqueda en índice clúster que usa la combinación de bucle anidado si no se ha superado el umbral. Observe que se ve "0 de 336" filas mostradas (la rama no se usa).
 Ahora vamos a comparar el plan con la misma consulta, pero esta vez para un valor *Cantidad* que solo tiene una fila en la tabla:
 
```sql
SELECT [fo].[Order Key], [si].[Lead Time Days], [fo].[Quantity]
FROM [Fact].[Order] AS [fo]
INNER JOIN [Dimension].[Stock Item] AS [si]
       ON [fo].[Stock Item Key] = [si].[Stock Item Key]
WHERE [fo].[Quantity] = 361;
```
La consulta devuelve una fila. Al habilitar las estadísticas de consultas activas se ve el siguiente plan:

![La consulta da lugar a una fila](./media/5_AQPStatsOneRow.png)

En el plan se ve lo siguiente:
- Con una fila devuelta, ahora pasan filas por la búsqueda en índice clúster.
- Y puesto que no se ha continuado con la fase de compilación de combinación hash, no pasan filas por la segunda rama.

### <a name="adaptive-join-benefits"></a>Ventajas de la combinación adaptable
La cargas de trabajo con oscilaciones frecuentes entre análisis de entrada de combinación pequeños y grandes son las que más se benefician de esta característica.

### <a name="adaptive-join-overhead"></a>Sobrecarga de la combinación adaptable
Las combinaciones adaptables tienen unos requisitos de memoria superiores a un plan equivalente de combinación de bucle anidado de índice. La memoria adicional se solicita como si el bucle anidado fuera una combinación hash. También hay sobrecarga para la fase de compilación como una operación de detención e inicio frente a una combinación equivalente de transmisión de bucle anidado. Ese costo adicional va acompañado de flexibilidad en escenarios donde los recuentos de filas pueden fluctuar en la entrada de compilación.

### <a name="adaptive-join-caching-and-re-use"></a>Almacenamiento en caché y reutilización de combinación adaptable
Las combinaciones adaptables de modo de proceso por lotes funcionan para la ejecución inicial de una instrucción y, una vez compiladas, las ejecuciones consecutivas seguirán siendo adaptables según el umbral de combinación adaptable compilado y las filas de runtime que pasan a través de la fase de compilación de la entrada externa.

### <a name="tracking-adaptive-join-activity"></a>Seguimiento de la actividad de combinación adaptable
El operador de combinación adaptable tiene los siguientes atributos de operador de plan:

| Atributo de plan | Descripción |
|--- |--- |
| AdaptiveThresholdRows | Muestra el uso de umbral para cambiar de una combinación hash a una combinación de bucle anidado. |
| EstimatedJoinType | El tipo de combinación probable. |
| ActualJoinType | En un plan real, se muestra qué algoritmo de combinación se ha elegido finalmente según el umbral. |

El plan estimado muestra la forma del plan de combinación adaptable, junto con un umbral de combinación adaptable definido y un tipo de combinación estimado.

### <a name="adaptive-join-and-query-store-interoperability"></a>Combinación adaptable e interoperabilidad del Almacén de consultas
El Almacén de consultas captura y puede aplicar un plan de combinación adaptable de modo de proceso por lotes.

### <a name="adaptive-join-eligible-statements"></a>Instrucciones aptas de combinación adaptable
Algunas condiciones convierten a una combinación lógica en apta como combinación adaptable de modo de proceso por lotes:
- El nivel de compatibilidad de la base de datos es 140.
- La consulta es una instrucción SELECT (las instrucciones de modificación de datos no son aptas actualmente).
- La combinación es apta para ejecutarla tanto con una combinación de bucles anidados indexada como con un algoritmo físico de combinación hash.
- La combinación hash usa el modo por lotes, ya sea mediante la presencia de un índice de almacén de columnas en la consulta global o una referencia directa a la tabla con índice de almacén de columnas por parte de la combinación.
- Las soluciones alternativas generadas de la combinación de bucles anidados y la combinación hash deben tener el mismo primer elemento secundario (referencia externa).

### <a name="adaptive-joins-and-nested-loop-efficiency"></a>Combinaciones adaptables y eficacia del bucle anidado
Si una combinación adaptable cambia a una operación de bucles anidados, usa las filas ya leídas por la compilación de combinación hash. El operador **no** vuelve a leer las filas de la referencia externa.

### <a name="adaptive-threshold-rows"></a>Filas de umbral adaptable
El gráfico siguiente muestra una intersección de ejemplo entre el costo de una combinación hash y el de una alternativa de combinación de bucles anidados.  En este punto de intersección, se determina el umbral que a su vez determina el algoritmo real usado para la operación de combinación.

![Umbral de combinación](./media/6_AQPJoinThreshold.png)

### <a name="disabling-adaptive-joins-without-changing-the-compatibility-level"></a>Deshabilitar las combinaciones adaptables sin cambiar el nivel de compatibilidad

Las combinaciones adaptables se pueden deshabilitar en el ámbito de base de datos o de instrucción mientras se mantiene el nivel de compatibilidad de base de datos 140 o posterior.  
Para deshabilitar las combinaciones adaptables para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_ADAPTIVE_JOINS = ON;
```

Cuando se habilita, esta opción aparecerá como habilitada en [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md).
Para volver a habilitar las combinaciones adaptables para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_ADAPTIVE_JOINS = OFF;
```

También puede deshabilitar las combinaciones adaptables para una consulta específica si designa `DISABLE_BATCH_MODE_ADAPTIVE_JOINS` como una [sugerencia de consulta USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint). Por ejemplo:

```sql
SELECT s.CustomerID,
       s.CustomerName,
       sc.CustomerCategoryName
FROM Sales.Customers AS s
LEFT OUTER JOIN Sales.CustomerCategories AS sc
       ON s.CustomerCategoryID = sc.CustomerCategoryID
OPTION (USE HINT('DISABLE_BATCH_MODE_ADAPTIVE_JOINS')); 
```

Una sugerencia de consulta USE HINT tiene prioridad sobre una configuración de ámbito de base de datos o una opción de marca de seguimiento.

## <a name="interleaved-execution-for-multi-statement-table-valued-functions"></a>Ejecución intercalada de funciones con valores de tabla de múltiples instrucciones
La ejecución intercalada cambia el límite unidireccional entre las fases de optimización y ejecución de una ejecución de una sola consulta y permite que los planes se adapten en función de las estimaciones de cardinalidad revisadas. Durante la optimización, si se detecta un candidato para la ejecución intercalada, que son actualmente las **funciones con valores de tabla de múltiples instrucciones (MSTVF)**, se detiene la optimización, se ejecuta el subárbol aplicable, se capturan las estimaciones de cardinalidad precisas y luego se reanuda la optimización de las operaciones de nivel inferior.   

Las MSTVF tienen una estimación de cardinalidad fija de 100 a partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], y de 1 en versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La ejecución intercalada ayuda con los problemas de rendimiento de las cargas de trabajo debidos a estas estimaciones de cardinalidad fijas asociadas a las MSTVF. Para obtener más información sobre las MSTVF, vea [Creación de funciones definidas por el usuario (motor de base de datos)](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF).

En la imagen siguiente se muestran los resultados de [estadísticas de consultas dinámicas](../../relational-databases/performance/live-query-statistics.md), un subconjunto de un plan de ejecución global que refleja el impacto de las estimaciones de cardinalidad fijas de las MSTVF. Puede ver el flujo de filas real frente a las filas estimadas. Hay tres áreas reseñables del plan (el flujo va de derecha a izquierda):
1. El recorrido de tabla de MSTVF tiene una estimación fija de 100 filas. Pero en este ejemplo hay 527.597 filas que pasan por este recorrido de tabla de MSTVF, como se muestra en las estadísticas de consultas dinámicas a través de *527597 de 100* reales de estimados, por lo que la estimación fija está considerablemente desviada.
1. En el caso de la operación de bucles anidados, se supone que el lado externo de la combinación solo devuelve 100 filas. Dado el gran número de filas que las MSTVF devuelven en realidad, es probable que lo mejor sea un algoritmo de combinación totalmente diferente.
1. En el caso de la operación de coincidencia de hash, observe el pequeño símbolo de advertencia, que en este caso indica un desbordamiento en el disco.

![Flujo de filas frente a filas estimadas](./media/7_AQPFlowThreeAreas.png)

Compare el plan anterior con el plan real generado con la ejecución intercalada habilitada:

![Plan intercalado](./media/8_AQPInterleavedEnabledPlan.png)

1. Observe que el recorrido de tabla de MSTVF ahora refleja una estimación de cardinalidad precisa. Observe también la reordenación de este recorrido de tabla y las demás operaciones.
1. Con respecto a los algoritmos de combinación, se ha pasado de una operación de bucle anidado a una operación de coincidencia de hash, que es más adecuada dado el gran número de filas implicadas.
1. Observe también que ya no hay advertencias de desbordamiento, dado que se ha concedido más memoria en función del recuento real de filas que pasan desde el recorrido de tabla de MSTVF.

### <a name="interleaved-execution-eligible-statements"></a>Instrucciones aptas de ejecución intercalada
Las instrucciones que hacen referencia a las MSTVF en la ejecución intercalada de momento deben ser de solo lectura y no formar parte de ninguna operación de modificación de datos. Además, las MSTVF no son aptas para la ejecución intercalada si no usan constantes en tiempo de ejecución.

### <a name="interleaved-execution-benefits"></a>Ventajas de la ejecución intercalada
En general, cuanta mayor sea la distorsión entre el número de filas real y el estimado, además del número de operaciones de nivel inferior del plan, mayor será el impacto sobre el rendimiento.
En general, la ejecución intercalada beneficia a las consultas donde:
1. Hay una gran distorsión entre el número real de filas y el estimado del conjunto de resultados intermedio (en este caso, las MSTVF).
1. Y la consulta global es sensible a un cambio en el tamaño del resultado intermedio. Esto suele suceder cuando hay un árbol complejo por encima de ese subárbol en el plan de consulta.
Un simple instrucción `SELECT *` de una MSTVF no se beneficiará de la ejecución intercalada.

### <a name="interleaved-execution-overhead"></a>Sobrecarga de la ejecución intercalada
La sobrecarga debe ser de mínima a ninguna. Las MSTVF ya se estaban materializando antes de la introducción de la ejecución intercalada; la diferencia es que ahora se permite la optimización diferida y luego se aprovecha la estimación de cardinalidad del conjunto de filas materializado.
Al igual que cualquier plan que afecte a los cambios, algunos planes podrían cambiar de modo que con la mejor cardinalidad del subárbol se obtuviera un plan peor para la consulta en general. La mitigación puede incluir la reversión del nivel de compatibilidad o el uso del Almacén de consultas para aplicar la versión no revertida del plan.

### <a name="interleaved-execution-and-consecutive-executions"></a>Ejecución intercalada y ejecuciones consecutivas
Una vez que se almacena en caché un plan de ejecución intercalada, el plan con las estimaciones revisadas en la primera ejecución se usa para las ejecuciones consecutivas sin volver a crear una instancia de ejecución intercalada.

### <a name="tracking-interleaved-execution-activity"></a>Seguimiento de la actividad de ejecución intercalada
Puede ver los atributos de uso en el plan de ejecución de consulta real:

| Atributo del plan de ejecución | Descripción |
| --- | --- |
| ContainsInterleavedExecutionCandidates | Se aplica al nodo *QueryPlan*. Si *true* significa que el plan contiene candidatos de ejecución intercalada. |
| IsInterleavedExecuted | Atributo del elemento *RuntimeInformation* bajo el elemento RelOp del nodo de TVF. Si es *true*, significa que la operación se ha materializado como parte de una operación de ejecución intercalada. |

También puede realizar el seguimiento de repeticiones de ejecución intercalada mediante los siguientes eventos de xEvents:

| xEvent | Descripción |
| ---- | --- |
| interleaved_exec_status | Este evento se desencadena cuando se está produciendo la ejecución intercalada. |
| interleaved_exec_stats_update | Este evento describe las estimaciones de cardinalidad actualizadas por la ejecución intercalada. |
| Interleaved_exec_disabled_reason | Este evento se desencadena cuando una consulta con un posible candidato para la ejecución intercalada no consigue realmente la ejecución intercalada. |

Se debe ejecutar una consulta para permitir que la ejecución intercalada revise las estimaciones de cardinalidad de MSTVF. Pero el plan de ejecución estimado aún muestra cuándo hay candidatos de ejecución intercalada a través del atributo del plan de presentación de `ContainsInterleavedExecutionCandidates`.    

### <a name="interleaved-execution-caching"></a>Almacenamiento en caché de la ejecución intercalada
Si un plan se borra o se elimina de la memoria caché, al ejecutarse la consulta se genera una nueva compilación que usa la ejecución intercalada.
Una instrucción con `OPTION (RECOMPILE)` creará un plan con ejecución intercalada y no lo almacenará en la memoria caché.     

### <a name="interleaved-execution-and-query-store-interoperability"></a>Ejecución intercalada e interoperabilidad del Almacén de consultas
Los planes con ejecución intercalada se pueden aplicar. El plan es la versión que ha corregido las estimaciones de cardinalidad basándose en la ejecución inicial.    

### <a name="disabling-interleaved-execution-without-changing-the-compatibility-level"></a>Deshabilitar la ejecución intercalada sin cambiar el nivel de compatibilidad

La ejecución intercalada se puede deshabilitar en el ámbito de base de datos o de instrucción mientras se mantiene el nivel de compatibilidad de base de datos 140 o posterior.  Para deshabilitar la ejecución intercalada para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_INTERLEAVED_EXECUTION_TVF = ON;
```

Cuando se habilita, esta opción aparecerá como habilitada en [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md).
Para volver a habilitar la ejecución intercalada para todas las ejecuciones de consultas que se originan en la base de datos, ejecute lo siguiente en el contexto de la base de datos aplicable:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_INTERLEAVED_EXECUTION_TVF = OFF;
```

También puede deshabilitar la ejecución intercalada para una consulta específica si designa `DISABLE_INTERLEAVED_EXECUTION_TVF` como una [sugerencia de consulta USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint). Por ejemplo:

```sql
SELECT [fo].[Order Key], [fo].[Quantity], [foo].[OutlierEventQuantity]
FROM [Fact].[Order] AS [fo]
INNER JOIN [Fact].[WhatIfOutlierEventQuantity]('Mild Recession',
                            '1-01-2013',
                            '10-15-2014') AS [foo] ON [fo].[Order Key] = [foo].[Order Key]
                            AND [fo].[City Key] = [foo].[City Key]
                            AND [fo].[Customer Key] = [foo].[Customer Key]
                            AND [fo].[Stock Item Key] = [foo].[Stock Item Key]
                            AND [fo].[Order Date Key] = [foo].[Order Date Key]
                            AND [fo].[Picked Date Key] = [foo].[Picked Date Key]
                            AND [fo].[Salesperson Key] = [foo].[Salesperson Key]
                            AND [fo].[Picker Key] = [foo].[Picker Key]
OPTION (USE HINT('DISABLE_INTERLEAVED_EXECUTION_TVF'));
```

Una sugerencia de consulta USE HINT tiene prioridad sobre una configuración de ámbito de base de datos o una opción de marca de seguimiento.

## <a name="see-also"></a>Consulte también
[Procesamiento de consultas inteligente en bases de datos SQL](../../relational-databases/performance/intelligent-query-processing.md)   
[Performance Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)    (Centro de rendimiento para el motor de base de datos SQL Server y Azure SQL Database)  
[Query Processing Architecture Guide](../../relational-databases/query-processing-architecture-guide.md)   (Guía de arquitectura de procesamiento de consultas)  
[Referencia de operadores lógicos y físicos del plan de presentación](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Combinaciones](../../relational-databases/performance/joins.md)    
[Demostración del procesamiento de consultas adaptable](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)    
[Sugerencias de consulta USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint)   
[Crear funciones definidas por el usuario (motor de base de datos)](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF)  
