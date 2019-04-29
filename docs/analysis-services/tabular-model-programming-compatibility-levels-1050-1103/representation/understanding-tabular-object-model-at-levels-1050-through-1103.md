---
title: Descripción de modelo de objetos tabulares en niveles de 1050 a 1103 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad3963cd7b0b2b40e6b3a08cab68ad809378bff1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025392"
---
# <a name="understanding-tabular-object-model-at-levels-1050-through-1103"></a>Descripción del modelo de objetos tabulares en niveles de 1050 a 1103
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]

  Un modelo tabular es una representación lógica de tablas, relaciones, jerarquías, perspectivas, medidas y rendimiento clave. En esta sección se presenta la implementación interna mediante AMO. Consulte [desarrollar con objetos de administración de análisis &#40;AMO&#41; ](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo) si aún no ha usado AMO antes.  
  
 El método empleado es de arriba abajo: todos los objetos pertinentes del modelo tabular se asignan de forma lógica a objetos de AMO y se explica la interacción o el flujo de trabajo necesario. Un ejemplo de código fuente para crear un modelo tabular con AMO, ejemplo AMO a Tabular está disponible en Codeplex. Nota importante sobre el código del ejemplo: se proporciona únicamente como apoyo a los conceptos lógicos explicados aquí y no se debe usar en un entorno de producción. El ejemplo se proporciona sin soporte técnico o garantía.  
  
## <a name="database-representation"></a>Representación de la base de datos  
 Una base de datos proporciona el objeto contenedor para el modelo tabular. Todos los objetos de un modelo tabular se encuentran en la base de datos. Por lo que respecta a los objetos de AMO, la representación de una base de datos tiene una relación de asignación uno a uno con `xref:Microsoft.AnalysisServices.Database` y no se necesitan otros objetos principales de AMO. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en el objeto de base de datos de AMO se puedan usar para realizar el modelado.  
  
 Consulte [representación de la base de datos&#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/database-representation-tabular.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de la base de datos.  
  
## <a name="connection-representation"></a>Representación de conexión  
 Una conexión establece la relación entre los datos que se van a incluir en una solución de modelo tabular y el propio modelo. En cuanto a los objetos de AMO, una conexión tiene una relación de asignación uno a uno con `xref:Microsoft.AnalysisServices.DataSource` y no se necesitan otros objetos principales de AMO. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en el objeto de origen de datos de AMO se puedan usar para realizar el modelado.  
  
 Consulte [representación de conexión &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/connection-representation-tabular.md) para obtener una explicación detallada sobre cómo crear y manipular la representación del origen de datos.  
  
## <a name="table-representation"></a>Representación de tabla  
 Las tablas son objetos de base de datos que contienen los datos de la base de datos. En términos de objetos de AMO, una tabla tiene una relación de asignación uno a varios. Una tabla se representa mediante el uso de los siguientes objetos AMO: `xref:Microsoft.AnalysisServices.DataSourceView`, `xref:Microsoft.AnalysisServices.Dimension`, `xref:Microsoft.AnalysisServices.Cube`, `xref:Microsoft.AnalysisServices.CubeDimension`, `xref:Microsoft.AnalysisServices.MeasureGroup` y `xref:Microsoft.AnalysisServices.Partition` son los objetos necesarios principales. Sin embargo, es importante tener en cuenta que esto no significa que todos los objetos incluidos en los objetos AMO mencionados anteriormente se puedan usar al modelar.  
  
 Consulte [representación de tablas &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-representation-tabular.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de tabla.  
  
### <a name="calculated-column-representation"></a>Representación de la columna calculada  
 Las columnas calculadas son expresiones evaluadas que generan una columna en una tabla, donde un nuevo valor se calcula y se almacena en cada fila de la tabla. En términos de objetos AMO, una columna calculada tiene una relación de asignación uno a varios. Una columna calculada se representa mediante el uso de los siguientes objetos de AMO: `xref:Microsoft.AnalysisServices.Dimension` y `xref:Microsoft.AnalysisServices.MeasureGroup` son los objetos principales necesarios. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en los objetos de AMO mencionados anteriormente se puedan usar para realizar el modelado.  
  
 Consulte [representación de la columna calculada &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-calculated-column-representation.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de la columna calculada.  
  
### <a name="calculated-measure-representation"></a>Representación de la medida calculada  
 Las medidas calculadas son expresiones almacenadas que se evalúan a petición una vez implementado el modelo. En términos de objetos de AMO, una medida calculada tiene una relación de asignación uno a varios. Una columna calculada se representa mediante el uso de los siguientes objetos de AMO: `xref:Microsoft.AnalysisServices.MdxScript.Commands%2A` y `xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A` son los objetos principales necesarios. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en los objetos de AMO mencionados anteriormente se puedan usar para realizar el modelado.  
  
> [!NOTE]  
>  Los objetos `xref:Microsoft.AnalysisServices.Measure` no tienen relación con las medidas calculadas en los modelos tabulares y no se admiten en dichos modelos.  
  
 Consulte [representación de la medida calculada &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-calculated-measure-representation.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de la medida calculada.  
  
### <a name="hierarchy-representation"></a>Representación de jerarquía  
 Las jerarquías son un mecanismo para proporcionar una experiencia de resumen y exploración en profundidad más completa al usuario final. Por lo que respecta a los objetos de AMO, las representaciones de jerarquías tienen una relación de asignación uno a uno con `xref:Microsoft.AnalysisServices.Hierarchy` y no se necesitan otros objetos principales de AMO. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en el objeto de base de datos de AMO se puedan usar para realizar el modelado tabular.  
  
 Consulte [representación de jerarquía &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-hierarchy-representation.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de jerarquía.  
  
### <a name="key-performance-indicator--kpi--representation"></a>La clave de rendimiento de representación de KPI - indicadores  
 Los KPI se usan para medir el rendimiento de un valor, definido por una medida base, con respecto a un valor de destino. En términos de objetos de AMO, una representación de KPI tiene una relación de asignación uno a varios. Los KPI se representa mediante el uso de los siguientes objetos AMO: `xref:Microsoft.AnalysisServices.MdxScript.Commands%2A` y `xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A` son los objetos necesarios principales.  Es importante tener en cuenta que esto no significa que todos los objetos contenidos en los objetos de AMO mencionados anteriormente se puedan usar para realizar el modelado.  
  
> [!NOTE]  
>  Además, existe una distinción importante, los objetos de `xref:Microsoft.AnalysisServices.Kpi` no tienen relación con los KPI de los modelos tabulares. Y no se admiten en los modelos tabulares.  
  
 Consulte [representación de indicadores clave de rendimiento &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-key-performance-indicator-representation.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de KPI.  
  
### <a name="partition-representation"></a>Representación de partición  
 Efectos operativos, se puede dividir una tabla en distintos subconjuntos de filas que, al combinarse juntas, forman la tabla. Cada uno de esos subconjuntos es una partición de la tabla. Por lo que respecta a los objetos de AMO, las representaciones de particiones tienen una relación de asignación uno a uno con `xref:Microsoft.AnalysisServices.Partition` y no se necesitan otros objetos principales de AMO. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en el objeto de base de datos de AMO se puedan usar para realizar el modelado.  
  
 Consulte [representación de partición &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/tables-partition-representation.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de partición.  
  
## <a name="relationship-representation"></a>Representación de relaciones  
 Una relación es una conexión entre dos tablas de datos. La relación establece cómo se deben relacionar los datos de las dos tablas.  
  
 En los modelos tabulares, se pueden definir varias relaciones entre dos tablas. Cuando se definen varias relaciones entre dos tablas, solo se puede definir una de ellas como la relación activa predeterminada. Todas las demás relaciones son inactivas.  
  
 Por lo que respecta a los objetos de AMO, todas las relaciones inactivas tienen una representación de una relación de asignación uno a uno con `xref:Microsoft.AnalysisServices.Relationship` y no se necesitan otros objetos principales de AMO. Para la relación activa, existen otros requisitos y también se necesita una asignación a `xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension`. Es importante tener en cuenta que esto no significa que todos los objetos contenidos en la relación AMO o en el objeto referenceMeasureGroupDimension se puedan usar para realizar el modelado.  
  
 Consulte [representación de relaciones &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/relationship-representation-tabular.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de relación.  
  
## <a name="perspective-representation"></a>Representación de perspectiva  
 Una perspectiva es un mecanismo para simplificar o centrar el modo. Por lo que respecta a los objetos de AMO, las representaciones de relaciones tienen una relación de asignación uno a uno con `xref:Microsoft.AnalysisServices.Perspective` y no se necesitan otros objetos principales de AMO. Es importante tener en cuenta que esto no significa que todos los objetos incluidos en el objeto de perspectiva AMO se puedan usar al realizar el modelado tabular.  
  
 Consulte [representación de perspectiva &#40;Tabular&#41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/perspective-representation-tabular.md) para obtener una explicación detallada sobre cómo crear y manipular la representación de perspectiva.  
  
> [!WARNING]  
>  Las perspectivas no son un mecanismo de seguridad. Se podrá tener acceso a los objetos que están fuera de la perspectiva mediante otras interfaces.  
  
  
