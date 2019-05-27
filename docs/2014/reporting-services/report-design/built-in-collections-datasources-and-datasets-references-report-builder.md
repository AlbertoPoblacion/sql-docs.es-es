---
title: Referencias a las colecciones DataSources y DataSets (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3b47503e9a7a2b09ea6e4d9f7f3ce309fd1b99f2
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106425"
---
# <a name="datasources-and-datasets-collection-references-report-builder-and-ssrs"></a>Usar referencias a las colecciones DataSources y DataSets (Generador de informes y SSRS)
  La colección `DataSources` representa todos los orígenes de datos usados en un informe. De igual forma, la colección `DataSets` representa todos los conjuntos de datos de todos los orígenes de datos existentes en un informe. Use el panel **Datos de informe** para obtener acceso a una vista jerárquica en la que aparezcan los conjuntos de datos de informe organizados debajo del origen de datos al que hacen referencia. Si incluye referencias a estas colecciones, no verá los valores cuando obtenga acceso a una vista previa del informe. Estas colecciones solo están disponibles una vez publicado el informe en un servidor de informes.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a>DataSources  
 La colección `DataSources` representa los orígenes de datos a los que se hace referencia en una definición de informe publicado. Puede decidir incluir esta información en el informe para documentar el origen de los datos de informe. Esta colección no está disponible en el modo **Vista previa** . En la siguiente tabla, se describen las variables de la colección `DataSources`.  
  
|**Variable**|`Type`|**Descripción**|  
|------------------|--------------|---------------------|  
|`DataSourceReference`|`String`|Ruta de acceso completa de la definición de origen de datos en el servidor de informes. Por ejemplo, puede incluir una lista de todos los orígenes de datos que usó un informe como parte de un historial de informes. En el ejemplo siguiente se muestra la ruta de acceso completa del origen de datos denominado AdventureWorks2012:<br /><br /> `/DataSources/AdventureWorks2012` |  
|`Type`|`String`|Tipo de proveedor de datos para el origen de datos. Por ejemplo, `SQL`.|  
  
## <a name="datasets"></a>DataSets  
 La colección `DataSets` representa los conjuntos de datos a los que se hace referencia en una definición de informe. Puede decidir incluir la consulta en el informe en un cuadro de texto, de modo que un usuario que esté interesado en saber exactamente qué datos están en el informe pueda ver el texto del comando original. Esta colección no está disponible en el modo **Vista previa** . En la siguiente tabla, se describen los miembros de la colección `DataSets`.  
  
|**Miembro**|`Type`|**Descripción**|  
|----------------|--------------|---------------------|  
|`CommandText`|`String`|Para los orígenes de datos de base de datos, ésta es la consulta que se utiliza para recuperar datos del origen de datos. Si la consulta es una expresión, ésta es la expresión evaluada.|  
|`RewrittenCommandText`|`String`|El valor CommandText expandido del proveedor de datos. Se utiliza normalmente en informes con parámetros de consulta que se asignan a parámetros de informe. El proveedor de datos establece esta propiedad al expandir las referencias de los parámetros de texto de comando a los valores constantes seleccionados para los parámetros de informe asignados.|  
  
### <a name="using-query-expressions"></a>Usar expresiones de consulta  
 Puede usar expresiones de consulta para definir la consulta contenida en un conjunto de datos. Puede usar esta característica para diseñar informes cuyas consultas cambien en función de la información facilitada por el usuario, de los datos de otros conjuntos de datos o de otras variables. Para más información sobre las consultas, vea [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vea también  
 [Expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
