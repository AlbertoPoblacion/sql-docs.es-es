---
title: Cómo recopila datos el almacén de consultas | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store, data collection
ms.assetid: 8d5eec36-0013-480a-9c11-183e162e4c8e
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||= azure-sqldw-latest||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 83fbc6c183216cedcbb664a0c3a2e3a9337e1513
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946779"
---
# <a name="how-query-store-collects-data"></a>Introducción a la recopilación de datos del almacén de consultas
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  El almacén de consultas funciona como una **caja negra de datos** que recopila en todo momento información de compilación y runtime relacionada con las consultas y los planes. Los datos relacionados con las consultas se guardan en las tablas internas y se presentan a los usuarios a través de un conjunto de vistas.  
  
## <a name="views"></a>Vistas  
 En el diagrama siguiente se muestran las vistas del almacén de consultas y sus relaciones lógicas (la información de tiempo de compilación se presenta como entidades de color azul):  
  
 ![query-store-process-2views](../../relational-databases/performance/media/query-store-process-2views.png "query-store-process-2views")  
**Descripciones de las vistas**  
  
|Ver|Descripción|  
|----------|-----------------|  
|**sys.query_store_query_text**|Presenta los textos de consultas únicas ejecutadas en la base de datos. Se omiten los comentarios y espacios antes y después del texto de consulta. No se omiten los comentarios y espacios dentro del texto. Cada instrucción del lote genera una entrada de texto de consulta independiente.|  
|**sys.query_context_settings**|Presenta las combinaciones únicas de configuraciones que afectan al plan con las que se ejecutan las consultas. El mismo texto de consulta ejecutado con distintas configuraciones que afecten al plan genera una entrada de consulta distinta en el almacén de consultas. Esto se debe a que `context_settings_id` forma parte de la clave de consulta.|  
|**sys.query_store_query**|Entradas de consulta a las que se realiza un seguimiento y que se aplican por separado en el almacén de consultas. Un texto de consulta solo puede generar varias entradas de consulta si se ejecuta con opciones de contexto distintas, o bien si se ejecuta fuera, en lugar de dentro de distintos módulos de [!INCLUDE[tsql](../../includes/tsql-md.md)] (procedimientos almacenados, desencadenadores, etc.).|  
|**sys.query_store_plan**|Presenta el plan estimado para la consulta con las estadísticas de tiempo de compilación. El plan almacenado equivale a uno que se obtendría utilizando `SET SHOWPLAN_XML ON`.|  
|**sys.query_store_runtime_stats_interval**|El almacén de consultas divide el tiempo en periodos (intervalos) generados de forma automática y almacena estadísticas agregadas en ese intervalo para cada plan ejecutado. El tamaño del intervalo se controla mediante la opción de configuración Intervalo de recopilación de estadísticas (en [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]) o `INTERVAL_LENGTH_MINUTES` con [Opciones de ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).|  
|**sys.query_store_runtime_stats**|Estadísticas agregadas del runtime para los planes ejecutados. Todas las métricas capturadas se expresan en forma de cuatro funciones estadísticas: Average, Minimum, Maximum y Standard Deviation.|  
  
 Para obtener más información sobre las vistas del almacén de consultas, vea la sección **Vistas, funciones y procedimientos relacionados** de [Supervisión del rendimiento mediante el almacén de consultas](monitoring-performance-by-using-the-query-store.md).  
  
## <a name="query-processing"></a>Procesamiento de consultas  
 El almacén de consultas interactúa con la canalización de procesamiento de consultas en los siguientes puntos clave:  
  
1.  Cuando se compila la consulta por primera vez, el texto de consulta y el plan inicial se envían al almacén de consultas.  
  
2.  Cuando la consulta se vuelve a compilar, se está actualizando el plan en el almacén de consultas. Si se crea un nuevo plan, el almacén de consultas agrega la nueva entrada de plan para la consulta, pero conserva los anteriores junto con sus estadísticas de ejecución.  
  
3.  Tras la ejecución de la consulta, se envían las estadísticas del runtime al almacén de consultas. El almacén de consultas mantiene precisas estadísticas agregadas para todos los planes que se ejecutan dentro del intervalo activo en ese momento.  
  
4.  Durante las fases de compilación y de comprobación para detectar una nueva compilación, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de termina si hay algún plan en el almacén de consultas que se deba aplicar para la consulta que se esté ejecutando en ese momento. Si hay un plan forzado y el plan de la caché de procedimientos es distinto al forzado, la consulta se vuelve a compilar, del mismo modo que si se aplicara PLAN HINT a ella. Este proceso se produce de forma transparente para la aplicación de usuario.  
  
 En el siguiente diagrama se muestran los aspectos de la integración explicados con anterioridad:  
  
 ![query-store-process-2processor](../../relational-databases/performance/media/query-store-process-2processor.png "query-store-process-2processor")  
  
 Para minimizar la sobrecarga de E/S, los nuevos datos se capturan en memoria. Las operaciones de escritura se ponen en cola y se vacían posteriormente en el disco. La información de consulta y plan (planear el almacén en el diagrama siguiente) se vacían con una latencia mínima. Las estadísticas en tiempo de ejecución (Estadísticas en tiempo de ejecución) se mantienen en memoria durante un período de tiempo definido con la opción `DATA_FLUSH_INTERVAL_SECONDS` de la instrucción `SET QUERY_STORE` . El cuadro de diálogo Almacén de consultas de SSMS permite especificar la opción **Intervalo de vaciado de datos (minutos)** , que se convierte a segundos.  
  
 ![query-store-process-3plan](../../relational-databases/performance/media/query-store-process-3.png "query-store-process-3plan")  
  
 Si el sistema se bloquea, el almacén de consultas puede perder datos del runtime hasta la cantidad definida con `DATA_FLUSH_INTERVAL_SECONDS`. El valor predeterminado de 900 segundos (15 minutos) ofrece un equilibrio óptimo entre el rendimiento de la captura de consultas y la disponibilidad de los datos.  
Si el sistema está bajo presión de memoria, es posible vaciar las estadísticas del runtime en el disco antes de lo definido con `DATA_FLUSH_INTERVAL_SECONDS`.  
Durante la lectura del almacén de consultas, los datos en memoria y en disco se unifican de manera transparente.
Si se termina una sesión o la aplicación cliente se reinicia o bloquea, las estadísticas de consulta no se registrarán.  
  
 ![query-store-process-4planinfo](../../relational-databases/performance/media/query-store-process-4planinfo.png "query-store-process-4planinfo")    

  
## <a name="see-also"></a>Consulte también  
 [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Procedimiento recomendado con el Almacén de consultas](../../relational-databases/performance/best-practice-with-the-query-store.md)   
 [Query Store Catalog Views (Vistas de catálogo del almacén de consultas) &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  
  
  
