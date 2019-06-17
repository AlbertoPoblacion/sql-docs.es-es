---
title: Procesamiento de objetos (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59a581f7e70f3fc1afd7eb7c1eaf4751d32719d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261663"
---
# <a name="processing-objects-xmla"></a>Procesar objetos (XMLA)
  En [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], procesar es el paso o serie de pasos que permiten convertir datos en información para análisis de negocios. El procesamiento varía en función del tipo de objeto, pero siempre forma parte de la conversión de datos en información.  
  
 Para procesar un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objeto, puede usar el [proceso](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) comando. El **proceso** comando puede procesar los objetos siguientes en un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia:  
  
-   Cubos  
  
-   Bases de datos  
  
-   Dimensions  
  
-   Grupos de medida  
  
-   Modelos de minería de datos  
  
-   Estructuras de minería de datos  
  
-   Particiones  
  
 Para controlar el procesamiento de objetos, el **proceso** comando tiene varias propiedades que se pueden establecer. El **proceso** comando tiene las propiedades que controlan: se realizará la cantidad de procesamiento, se procesarán los objetos que, si se debe usar los enlaces fuera de línea, cómo controlar errores y cómo administrar las tablas de reescritura.  
  
## <a name="specifying-processing-options"></a>Especificar opciones de procesamiento  
 El [tipo](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) propiedad de la **proceso** comando Especifica la opción de procesamiento deben usar al procesar el objeto. Para más información sobre las opciones de procesamiento, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 En la tabla siguiente se enumera las constantes para el **tipo** propiedad y los diversos objetos que se pueden procesar con cada una de ellas.  
  
|**Tipo** valor|Objetos aplicables|  
|--------------------|------------------------|  
|*ProcessFull*|Cubo, base de datos, dimensión, grupo de medida, modelo de minería de datos, estructura de minería de datos, partición|  
|*ProcessAdd*|Dimensión, partición|  
|*ProcessUpdate*|Dimensión|  
|*ProcessIndexes*|Dimensión, cubo, grupo de medida, partición|  
|*ProcessData*|Dimensión, cubo, grupo de medida, partición|  
|*ProcessDefault*|Cubo, base de datos, dimensión, grupo de medida, modelo de minería de datos, estructura de minería de datos, partición|  
|*ProcessClear*|Cubo, base de datos, dimensión, grupo de medida, modelo de minería de datos, estructura de minería de datos, partición|  
|*ProcessStructure*|Cubo, estructura de minería de datos|  
|*ProcessClearStructureOnly*|Estructura de minería de datos|  
|*ProcessScriptCache*|Cube|  
  
 Para obtener más información sobre el procesamiento de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objetos, vea [procesar un modelo multidimensional &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Especificar los objetos que se van a procesar  
 El [objeto](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propiedad de la **proceso** comando contiene el identificador de objeto del objeto que se va a procesar. Se puede especificar un solo objeto en un **proceso** comando, pero el procesamiento de un objeto también procesan sus objetos secundarios. Por ejemplo, al procesar un grupo de medida de un cubo se procesan todas las particiones de dicho grupo de medida, mientras que al procesar una base de datos se procesan todos los objetos contenidos en ésta (incluidos los cubos, las dimensiones y las estructuras de minería de datos).  
  
 Si establece la **ProcessAffectedObjects** atributo de la **proceso** comando en true, todas relacionadas también se procesa el objeto afectado por el procesamiento del objeto especificado. Por ejemplo, si una dimensión se actualiza de forma incremental mediante el uso de la *ProcessUpdate* procesamiento opción en el **proceso** de comandos, cualquier partición cuyas agregaciones se invaliden debido a los miembros que se va a Agregar o eliminar también procesa [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] si **ProcessAffectedObjects** está establecido en true. En este caso, una sola **proceso** comando puede procesar varios objetos en un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia, pero [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determina qué objetos además del objeto especificado en el **proceso** También se debe procesar el comando.  
  
 Sin embargo, puede procesar varios objetos, como dimensiones, al mismo tiempo mediante el uso de varios **proceso** comandos dentro de un **Batch** comando. Operaciones por lotes proporcionan un mayor nivel de control para procesamiento en serie o paralelo de los objetos en un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia que el uso de la **ProcessAffectedObjects** de atributo y permiten optimizar el enfoque del procesamiento de mayor [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bases de datos. Para obtener más información acerca de cómo realizar operaciones por lotes, vea [realizar operaciones por lotes &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Especificar enlaces fuera de línea  
 Si el **proceso** comando no está incluido en un **Batch** comando, también puede especificar enlaces fuera de línea en el [enlaces](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [delorigendedatos](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasource-element-xmla), y [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) propiedades de la **proceso** el comando para los objetos que se va a procesarse. Los enlaces fuera de línea son referencias a orígenes de datos, vistas del origen de datos y otros objetos en el que el enlace existe solamente durante la ejecución de la **proceso** comando y que invalidan los enlaces existentes asociados con el objetos que se está procesados. Si no se especifican enlaces fuera de línea, se utilizan los enlaces actualmente asociados a los objetos que se van a procesar.  
  
 Los enlaces fuera de línea se utilizan en las circunstancias siguientes:  
  
-   Procesamiento incremental de una partición, donde debe especificarse una tabla de hechos alternativa o aplicarse un filtro a la tabla de hechos existente para asegurarse de que las filas no se cuentan dos veces.  
  
-   Uso de una tarea de flujo de datos en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] para proporcionar datos al procesar una dimensión, el modelo de minería de datos o la partición.  
  
 Los enlaces fuera de línea se describen como parte de Analysis Services Scripting Language (ASSL). Para obtener más información sobre los enlaces fuera de línea en ASSL, vea [orígenes de datos y enlaces &#40;Multidimensional de SSAS&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Actualizar particiones de forma incremental  
 La actualización incremental de una partición ya procesada suele requerir un enlace fuera de línea, ya que el enlace especificado para la partición hace referencia a datos de la tabla de hechos ya agregados en la partición. Al actualizar incrementalmente una partición ya procesada mediante el uso de la **proceso** comando, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] realiza las acciones siguientes:  
  
-   Crea una partición temporal con una estructura idéntica a la de la partición que se va a actualizar incrementalmente.  
  
-   Procesa la partición temporal, utilizando el enlace fuera de línea especificado en el **proceso** comando.  
  
-   Mezcla la partición temporal con la partición existente seleccionada.  
  
 Para obtener más información acerca de cómo combinar particiones con XML for Analysis (XMLA), consulte [mezclar particiones &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Controlar los errores de procesamiento  
 El [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) propiedad de la **proceso** comando le permite especificar cómo controlar los errores detectados al procesar un objeto. Por ejemplo, durante el procesamiento de una dimensión, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encuentra un valor duplicado en la columna de clave del atributo clave. Dado que las claves de atributo deben ser únicas, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] descarta los registros duplicados. Según el [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) propiedad de **ErrorConfiguration**, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] podría:  
  
-   Omitir el error y continuar el procesamiento de la dimensión.  
  
-   Devolver un mensaje que indique que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encontró una clave duplicada y continuar el procesamiento.  
  
 Hay muchas condiciones similares para que **ErrorConfiguration** proporciona opciones durante un **proceso** comando.  
  
## <a name="managing-writeback-tables"></a>Administrar tablas de reescritura  
 Si el **proceso** comando encuentra una partición habilitada para escritura, o un cubo o grupo de medida para la partición que no se procese ya por completo, una tabla de reescritura no puede existir para esa partición. El [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) propiedad de la **proceso** comando determina si [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] debe crear una tabla de reescritura.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se procesa completamente la base de datos de ejemplo [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
### <a name="code"></a>Código  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente se procesa de forma incremental el **Internet_Sales_2004** de partición en la **Internet Sales** grupo de medida de la **Adventure Works DW** cubo en el [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ejemplo [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de datos. El **proceso** comando es agregar agregaciones para el orden de fechas posterior al 31 de diciembre de 2006 a la partición mediante el uso de un enlace de consultas fuera de línea de la **enlaces** propiedad de la **proceso**  comando para recuperar las filas de tabla de hechos desde el que se va a generar las agregaciones para agregar a la partición.  
  
### <a name="code"></a>Código  
  
```  
<Process ProcessAffectedObjects="true" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
