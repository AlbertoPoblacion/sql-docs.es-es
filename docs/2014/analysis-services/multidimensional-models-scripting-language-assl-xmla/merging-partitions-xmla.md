---
title: Mezclar particiones (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f09255372478bdb9956b64283c8b94477598239
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62702041"
---
# <a name="merging-partitions-xmla"></a>Mezclar particiones (XMLA)
  Si las particiones tienen el mismo diseño de agregaciones y la estructura, puede combinar la partición mediante la [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) comando XML for Analysis (XMLA). Combinar particiones es una acción importante que se debe realizar cuando se administran particiones, sobre todo aquellas particiones que contienen datos históricos con particiones por fecha.  
  
 Por ejemplo, un cubo financiero puede usar dos particiones:  
  
-   Una partición representa los datos financieros del año en curso, usando la configuración de almacenamiento de OLAP relacional (ROLAP) en tiempo real para el rendimiento.  
  
-   Otra partición contiene los datos financieros de años anteriores, usando la configuración de almacenamiento de OLAP multidimensional (MOLAP) para el almacenamiento.  
  
 Ambas particiones usan valores de almacenamiento diferentes, pero utilizan el mismo diseño de agregaciones. En lugar de procesar el cubo a través de años de datos históricos al final del año, puede usar en su lugar el comando `MergePartitions` para combinar la partición del año en curso en la partición de años anteriores. Con ello se conservan los datos de agregación sin tener que realizar un proceso completo del cubo que puede requerir mucho tiempo.  
  
## <a name="specifying-partitions-to-merge"></a>Especificar particiones para combinar  
 Cuando el `MergePartitions` comando se ejecuta, los datos de agregación almacenados en las particiones de origen especificadas en el [origen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) propiedad se agrega a la partición de destino especificada en el [destino](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) propiedad.  
  
> [!NOTE]  
>  La propiedad `Source` puede contener más de una referencia de objeto de partición. Sin embargo, la propiedad `Target` no puede.  
  
 Para que la combinación se realice correctamente, las particiones especificadas tanto en `Source` como en `Target` deben incluirse en del mismo grupo de medida y usar el mismo diseño de agregaciones. De lo contrario, se produce un error.  
  
 Se eliminan las particiones especificadas en `Source` una vez que el comando `MergePartitions` se ha completado correctamente.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente combina todas las particiones de la **Customer Counts** grupo de medida de la **Adventure Works** del cubo en el **Adventure Works DW** ejemplo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en la base de datos la **Customers_2004** partición.  
  
### <a name="code"></a>Código  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo con XMLA en Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
