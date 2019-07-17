---
title: Las particiones de modelos tabulares de Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d26b1b1558ca546fb47660488b15dc777c5ad87
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162720"
---
# <a name="partitions"></a>Particiones
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Las particiones dividen una tabla en partes lógicas. A continuación, cada partición se puede procesar (actualizar) de forma independiente de las demás particiones. Las particiones creadas mediante el cuadro de diálogo particiones SSDT durante la creación del modelo se aplican a la base de datos de área de trabajo del modelo. Una vez implementado el modelo, las particiones definidas para la base de datos del área de trabajo del modelo se duplican en la base de datos del modelo implementada. Puede crear y administrar particiones para una base de datos del modelo implementado mediante el cuadro de diálogo particiones en SSMS.  La información proporcionada en este tema describe las particiones creadas durante la creación del modelo mediante el cuadro de diálogo Administrador de particiones en SSDT. Para obtener información sobre cómo crear y administrar particiones para un modelo implementado, vea [crear y administrar particiones de modelos tabulares](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_benefits"></a> Ventajas  
 En los modelos tabulares, las particiones dividen una tabla en objetos de partición lógicos. A continuación, cada partición se puede procesar de forma independiente de las demás particiones. Por ejemplo, una tabla puede incluir ciertos conjuntos de filas cuyos datos apenas cambian y otros conjuntos de filas cuyos datos cambian con frecuencia. En estos casos, no hay necesidad de procesar todos los datos si solo se desea procesar una parte de ellos. Las particiones le permiten separar los datos que necesita procesar con frecuencia de los datos que se pueden procesar con una frecuencia menor.  
  
 Un diseño de modelos eficientes usa particiones para eliminar el procesamiento innecesario y la subsiguiente carga del procesador en los servidores de Analysis Services, asegurándose al mismo tiempo de que los datos se procesan y actualizan con la frecuencia suficiente para reflejar los datos más recientes de los orígenes de datos. El modo en que se implementan y usan las particiones durante la creación de modelos puede ser muy diferente del modo en que se implementan y se usan en los modelos implementados. Tenga presente que durante la fase de creación del modelo, es posible que trabaje con un único subconjunto de datos que finalmente estará en el modelo implementado.  
  
### <a name="processing-partitions"></a>Procesar particiones  
 Para los modelos implementados, el procesamiento se produce mediante el uso de SSMS, o bien ejecutando un script que incluya el comando procesar y especifica la configuración y las opciones de procesamiento. Cuando cree modelos con SSDT, puede ejecutar operaciones de proceso mediante el uso de un comando de proceso desde el menú modelo o la barra de herramientas. Una operación de procesamiento se puede especificar para una partición, una tabla o para todas ellas.  
  
 Cuando se ejecuta una operación de procesamiento, se realiza una conexión con el origen de datos usando la conexión de datos. Los nuevos datos se importan en las tablas del modelo, las relaciones y las jerarquías se vuelven a generar para cada tabla, y se vuelven a realizar los cálculos de las medidas y columnas calculadas.  
  
 Mediante una mayor división de una tabla en particiones lógicas, puede determinar de forma selectiva qué datos se procesan de cada partición, y cuándo y cómo se procesan. Al implementar un modelo, se puede completar el procesamiento de particiones manualmente mediante el cuadro de diálogo particiones en SSMS o mediante un script que ejecuta un comando de proceso.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Particiones en la base de datos del área de trabajo del modelo  
 Puede crear nuevas particiones, editar, combinar o eliminar particiones mediante el Administrador de particiones en SSDT. Según el nivel de compatibilidad del modelo que se va a crear, Partition Manager proporciona dos modos para seleccionar tablas, filas y columnas de una partición: Para los modelos tabulares 1400, las particiones se definen mediante el uso de una consulta de M o puede usar el modo de diseño para abrir el Editor de consultas. Para tabular 1100, 1103, los modelos 1200, utilice el modo de vista previa de tabla y el modo de consulta SQL. 
  
### <a name="partitions-in-a-deployed-model-database"></a>Particiones en una base de datos del modelo implementada  
 Al implementar un modelo, las particiones de la base de datos de modelo implementada aparecerá como objetos de base de datos en SSMS. Puede crear, editar, combinar y eliminar particiones para un modelo implementado mediante el cuadro de diálogo particiones en SSMS. Administrar particiones para un modelo implementado en SSMS está fuera del ámbito de este tema. Para obtener información sobre cómo administrar particiones en SSMS, consulte [crear y administrar particiones de modelos tabulares](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Crear y administrar particiones en la base de datos del área de trabajo](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|Describe cómo crear y administrar particiones en la base de datos de área de trabajo del modelo mediante el Administrador de partición en SSDT.|  
|[Procesar particiones en la base de datos del área de trabajo](../../analysis-services/tabular-models/process-partitions-in-the-workspace-database-ssas-tabular.md)|Describe cómo procesar (actualizar) particiones en la base de datos del área de trabajo del modelo.|  
  
## <a name="see-also"></a>Vea también  
 [Modo DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Procesar datos](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  
