---
title: "Ampliar un conjunto de datos con la transformación Combinación de mezcla | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00aaf46bb6b24813a79300be3a23d2a3aab28e41
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a>Ampliar un conjunto de datos con la transformación Combinación de mezcla
  Para agregar y configurar una transformación Combinación de mezcla, el paquete ya debe incluir por lo menos una tarea Flujo de datos y dos componentes de flujo de datos que proporcionen entradas a la transformación Combinación de mezcla.  
  
 La transformación Combinación de mezcla requiere dos entradas ordenadas. Para obtener más información, vea [Ordenar datos para las transformaciones Mezclar y Combinación de mezcla](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
### <a name="to-extend-a-dataset"></a>Para ampliar un conjunto de datos  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  En el Explorador de soluciones, haga doble clic en el paquete para abrirlo.  
  
3.  Haga clic en la pestaña **Flujo de datos** y, a continuación, desde el **cuadro de herramientas**, arrastre la transformación Combinación de mezcla a la superficie de diseño.  
  
4.  Conecte la transformación Combinación de mezcla con el flujo de datos arrastrando el conector desde un origen de datos o una transformación anterior a la transformación Combinación de mezcla.  
  
5.  Haga doble clic en la transformación Combinación de mezcla.  
  
6.  En el cuadro de diálogo **Editor de transformación Combinación de mezcla** , seleccione el tipo de combinación que se debe usar en la lista **Tipo de combinación** .  
  
    > [!NOTE]  
    >  Si selecciona el tipo **Combinación externa izquierda** , puede hacer clic en **Intercambiar entradas** para intercambiar las entradas y convertir la combinación externa izquierda en una combinación externa derecha.  
  
7.  Arrastre las columnas de la entrada izquierda a las columnas de la entrada derecha para especificar las columnas de combinación. Si las columnas tienen el mismo nombre, puede activar la casilla **Clave de combinación** y la transformación Combinación de mezcla automáticamente crea la combinación.  
  
    > [!NOTE]  
    >  Se pueden crear combinaciones solo entre columnas que tengan la misma posición de ordenación y las combinaciones se deben crear en el orden especificado por la posición de ordenación. Si intenta crear las combinaciones no ordenadas, el **Editor de transformación Combinación de mezcla** le indica que debe crear combinaciones adicionales para las posiciones de ordenación omitidas.  
  
    > [!NOTE]  
    >  Como opción predeterminada, la salida se ordena en las columnas de combinación.  
  
8.  En las entradas derecha e izquierda, active las casillas de columnas adicionales que se deben incluir en la salida. Las columnas de combinación se incluyen como opción predeterminada.  
  
9. Opcionalmente, actualice los nombres de las columnas de salida en la columna **Alias de salida** .  
  
10. Haga clic en **Aceptar**.  
  
11. Para guardar el paquete actualizado, haga clic en **Guardar los elementos seleccionados** , en el menú **Archivo** .  
  
## <a name="see-also"></a>Ver también  
 [Merge Join Transformation](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Transformaciones de Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Rutas de Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Tarea Flujo de datos](../../../integration-services/control-flow/data-flow-task.md)  
  
  
