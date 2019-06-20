---
title: Diseñar agregaciones (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9f681b3c99bd0e8351a844f28b16be6249de199
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288501"
---
# <a name="designing-aggregations-xmla"></a>Diseñar agregaciones (XMLA)
  Los diseños de agregaciones están asociados a las particiones de un grupo de medida determinado para asegurar que las particiones usan la misma estructura al almacenar agregaciones. Con la misma estructura de almacenamiento para particiones le permite definir fácilmente las particiones que pueden combinarse más tarde mediante el [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) comando. Para obtener más información acerca de los diseños de agregaciones, vea [agregaciones y diseños de agregaciones](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Para definir agregaciones para un diseño de agregaciones, puede usar el [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) comando XML for Analysis (XMLA). El **DesignAggregations** comando tiene propiedades que identifican el diseño de agregaciones que se usará como una referencia y cómo controlar el proceso de diseño basado en esa referencia. Mediante el **DesignAggregations** comandos y sus propiedades, puede diseñar agregaciones de forma iterativa o por lotes y, a continuación, ver las estadísticas de diseño resultantes para evaluar el proceso de diseño.  
  
## <a name="specifying-an-aggregation-design"></a>Especificar un diseño de agregaciones  
 El [objeto](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propiedad de la **DesignAggregations** comando debe contener una referencia de objeto a un diseño de agregaciones existente. La referencia de objeto contiene un identificador de la base de datos, identificador de cubo, identificador de grupo de medida e identificador de diseño de agregaciones. Si el diseño de agregaciones aún no existe, se produce un error.  
  
## <a name="controlling-the-design-process"></a>Controlar el proceso de diseño  
 Puede usar las siguientes propiedades de la **DesignAggregations** comandos para controlar el algoritmo utilizado para definir agregaciones para el diseño de agregaciones:  
  
-   El [pasos](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/steps-element-xmla) propiedad determina cuántas iteraciones el **DesignAggregations** comando debe realizar antes de devolver el control a la aplicación cliente.  
  
-   El [tiempo](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/time-element-xmla) propiedad determina cuántos milisegundos del **DesignAggregations** comando debe realizar antes de devolver el control a la aplicación cliente.  
  
-   El [optimización](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/optimization-element-xmla) propiedad determina el porcentaje estimado de mejora del rendimiento del **DesignAggregations** comando debería intentar alcanzar. Si diseña agregaciones de forma iterativa, solo tendrá que enviar esta propiedad en el primer comando.  
  
-   El [almacenamiento](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/storage-element-xmla) propiedad determina la cantidad estimada de almacenamiento en disco, en bytes, utilizado por el **DesignAggregations** comando. Si diseña agregaciones de forma iterativa, solo tendrá que enviar esta propiedad en el primer comando.  
  
-   El [Materialize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/materialize-element-xmla) propiedad determina si el **DesignAggregations** comando debe crear las agregaciones definidas durante el proceso de diseño. Si diseña agregaciones de forma iterativa, esta propiedad debería establecerse en false hasta que esté listo para guardar las agregaciones diseñadas. Cuando la propiedad está establecida en true, finaliza el proceso de diseño actual y las agregaciones definidas se agregan al diseño de agregaciones especificado.  
  
## <a name="specifying-queries"></a>Especificar consultas  
 El comando DesignAggregations admite el comando de optimización basada en uso incluyendo uno o más **consulta** elementos en el [consultas](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/queries-element-xmla) propiedad. El **consultas** propiedad puede contener uno o varios [consulta](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla) elementos. Si el **consultas** propiedad no contiene ningún **consulta** elementos, el diseño de agregaciones especificado en el **objeto** elemento usa una estructura predeterminada que contiene un conjunto general de agregaciones. Este conjunto general de agregaciones está diseñado para cumplir los criterios especificados en el **optimización** y **almacenamiento** propiedades de la **DesignAggregations** comando.  
  
 Cada elemento **Query** representa una consulta de objetivo que utiliza el proceso de diseño para definir agregaciones dirigidas a las consultas utilizadas con más frecuencia. Puede especificar sus propias consultas de objetivo, o puede usar la información almacenada por una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el registro de consultas para recuperar información sobre con más frecuencia utiliza las consultas. El Asistente de optimización basada en el uso utiliza el registro de consultas para recuperar las consultas de objetivo según la hora, uso o un usuario especificado cuando envía un **DesignAggregations** comando. Para obtener más información, consulte [ayuda F1 del Asistente para optimización basada en uso](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763).  
  
 Si está diseñando agregaciones de forma repetitiva, solo tiene que incluir consultas de objetivo en el primer comando **DesignAggregations** porque la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] almacena estas consultas de objetivo y las usa durante la ejecución de posteriores comandos **DesignAggregations** . Después de incluir las consultas del objetivo en el primer comando **DesignAggregations** de un proceso iterativo, cualquier comando **DesignAggregations** posterior que contenga las consultas de objetivo en la propiedad **Queries** generará un error.  
  
 El elemento **Query** contiene un valor delimitado por comas que contiene los siguientes argumentos:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Frecuencia*  
 Un factor de ponderación que corresponde al número de veces que se ha ejecutado con anterioridad la consulta. Si el elemento **Query** representa una nueva consulta, el valor *Frequency* representa el factor de ponderación utilizado por el proceso del diseño para evaluar la consulta. A medida que el valor de frecuencia se vuelve mayor, el valor de ponderación que se asigna a la consulta durante el proceso de diseño va aumentando.  
  
 *Conjunto de datos*  
 Una cadena numérica que especifica qué atributos de una dimensión se van a incluir en la consulta. Esta cadena debe tener el mismo número de caracteres que el número de atributos de la dimensión. El cero (0) indica que el atributo de la posición ordinal especificada no está incluido en la consulta de la dimensión especificada, mientras que el uno (1) indica que el atributo de la posición ordinal especificada está incluido en la consulta de la dimensión especificada.  
  
 Por ejemplo, la cadena "011" haría referencia a una consulta que implicaría una dimensión con tres atributos, de los que el segundo y el tercero estarían incluidos en la consulta.  
  
> [!NOTE]  
>  Algunos atributos no se tienen en cuenta en el conjunto de datos. Para obtener más información sobre los atributos excluidos, vea [elemento Query &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla).  
  
 Cada dimensión del grupo de medida que contiene el diseño de agregaciones está representada por un valor *Dataset* en el elemento **Query** . El orden de los valores de *Dataset* debe coincidir con el orden de las dimensiones incluidas en el grupo de medidas.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Diseñar agregaciones mediante el proceso iterativo o proceso por lotes  
 Puede usar el **DesignAggregations** comandos como parte de un proceso iterativo o un proceso por lotes, dependiendo de la interactividad que requiere el proceso de diseño.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Diseñar agregaciones mediante un proceso iterativo  
 Para diseñar de forma iterativa agregaciones, enviar varias **DesignAggregations** comandos para proporcionar un control exhaustivo sobre el proceso de diseño. El Asistente para diseñar agregaciones usa este mismo enfoque para proporcionar un control exhaustivo sobre el proceso de diseño. Para obtener más información, consulte [ayuda de F1 de Asistente de diseño de agregaciones](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d).  
  
> [!NOTE]  
>  Para diseñar agregaciones de forma iterativa, se requiere una sesión explícita. Para obtener más información acerca de sesiones explícitas, consulte [administrar conexiones y sesiones &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
 Para iniciar el proceso iterativo, envíe primero un **DesignAggregations** comando que contiene la información siguiente:  
  
-   El **almacenamiento** y **optimización** valores de propiedad en la que va dirigido el proceso de diseño completo.  
  
-   El **pasos** y **tiempo** valores de propiedad en el que se limita el primer paso del proceso de diseño.  
  
-   Si desea que la optimización basada en uso, el **consultas** propiedad que contiene el objetivo de las consultas en las que va dirigido el proceso de diseño completo.  
  
-   El **Materialize** propiedad establecida en false. Establecer esta propiedad en false indica que el proceso de diseño no guarda las agregaciones definidas en el diseño de agregaciones una vez completado el comando.  
  
 Cuando la primera **DesignAggregations** comando finaliza, el comando devuelve un conjunto de filas que contiene estadísticas de diseño. Puede evaluar estas estadísticas de diseño para determinar si el proceso de diseño debe continuar o si ha finalizado. Si debe continuar el proceso, a continuación, envía otro **DesignAggregations** comando que contiene el **pasos** y **tiempo** valores con el que se procese este paso del diseño está limitado. Evalúe las estadísticas resultantes y, a continuación, determine si el proceso de diseño debe continuar. Este proceso iterativo de enviar **DesignAggregations** comandos y evaluar los resultados continúa hasta que llegue a sus objetivos y tiene un conjunto adecuado de agregaciones definidas.  
  
 Una vez que haya obtenido el conjunto de agregaciones que desee, envíe un último **DesignAggregations** comando. Este último **DesignAggregations** comando debe tener su **pasos** propiedad establecida en 1 y su **Materialize** propiedad establecida en true. Mediante el uso de estos valores, este último **DesignAggregations** comando se completa el proceso de diseño y guarda la agregación definida en el diseño de agregaciones.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Diseñar agregaciones mediante un proceso por lotes  
 También puede diseñar agregaciones en un proceso por lotes mediante el envío de una sola **DesignAggregations** comando que contiene el **pasos**, **tiempo**, **almacenamiento** , y **optimización** los valores de propiedad en el que el proceso de diseño completo está dirigido y limitado. Si desea que la optimización basada en uso, las consultas de objetivo en el que está dirigido el proceso de diseño también deben incluirse en el **consultas** propiedad. Además, asegúrese de que el **Materialize** propiedad se establece en true, para que el proceso de diseño guarda las agregaciones definidas en el diseño de agregaciones cuando finaliza el comando.  
  
 Puede diseñar agregaciones mediante un proceso por lotes en una sesión tanto implícita como explícita. Para obtener más información acerca de las sesiones implícitas y explícitas, consulte [administrar conexiones y sesiones &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Devolver estadísticas de diseño  
 Cuando el **DesignAggregations** comando devuelve el control a la aplicación cliente, el comando devuelve un conjunto de filas que contiene una sola fila que representa las estadísticas de diseño para el comando. El conjunto de filas contiene las columnas que se muestran en la tabla siguiente.  
  
|columna|Data type|Descripción|  
|------------|---------------|-----------------|  
|Pasos|Integer|El número de pasos que realiza el comando antes de devolver el control a la aplicación cliente.|  
|Time|Entero largo|El número de milisegundos que tarda el comando antes de devolver el control a la aplicación cliente.|  
|Optimization|Double|El porcentaje estimado de mejora del rendimiento que alcanza el comando antes de devolver el control a la aplicación cliente.|  
|Storage|Entero largo|El número estimado de bytes que toma el comando antes de devolver el control a la aplicación cliente.|  
|Agregaciones|Entero largo|El número de agregaciones definido por el comando antes de devolver el control a la aplicación cliente.|  
|LastStep|Boolean|Indica si los datos en el conjunto de filas representan el último paso del proceso de diseño. Si el **Materialize** propiedad del comando se estableció en true, el valor de esta columna se establece en true.|  
  
 Puede utilizar las estadísticas de diseño que se encuentran en el conjunto de filas devuelto después de cada **DesignAggregations** comandos en ambos diseños, iterativo y por lotes. En diseño iterativo, puede usar estadísticas de diseño para determinar y mostrar el progreso. Cuando diseña agregaciones por lotes, puede usar estadísticas de diseño para determinar el número de agregaciones que crea el comando.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo con XMLA en Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
