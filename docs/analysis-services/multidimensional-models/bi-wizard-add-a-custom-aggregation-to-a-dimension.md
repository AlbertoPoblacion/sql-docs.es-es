---
title: Agregar una agregación personalizada a una dimensión | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cbe5c4a1f043ccc8e7f442213b8b024a3920663e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62717382"
---
# <a name="bi-wizard---add-a-custom-aggregation-to-a-dimension"></a>Asistente de BI: Agregar una agregación personalizada a una dimensión
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Agregue una mejora de agregación personalizada a un cubo o dimensión para reemplazar las agregaciones predeterminadas asociadas a un miembro de dimensión con un operador unario diferente. Esta mejora especifica una columna de operador unario en la tabla de dimensión que define el resumen de los miembros de una jerarquía de elementos primarios y secundarios. El operador unario actúa sobre el atributo primario en una jerarquía de elementos primarios y secundarios.  
  
> [!NOTE]  
>  Una agregación personalizada solo está disponible en dimensiones basadas en los orígenes de datos existentes. En las dimensiones que se crearon sin utilizar un origen de datos, debe ejecutar el Asistente para generar esquemas para crear una vista del origen de datos antes de agregar la agregación personalizada.  
  
 Para agregar una agregación personalizada, debe utilizar el Asistente de Business Intelligence y seleccionar la opción **Especificar un operador unario** en la página **Elegir mejora** . Este asistente le indica los pasos necesarios para seleccionar la dimensión en la que desea aplicar una agregación personalizada e identificar la agregación personalizada.  
  
> [!NOTE]  
>  Antes de ejecutar el Asistente de Business Intelligence para agregar una agregación personalizada, compruebe que la dimensión que desea mejorar contiene una jerarquía de atributos primarios y secundarios. Para obtener más información, vea [Dimensiones de elementos primarios y secundarios](../../analysis-services/multidimensional-models/parent-child-dimension.md).  
  
## <a name="selecting-a-dimension"></a>Seleccionar una dimensión  
 En la primera página **Especificar un operador unario** del asistente, debe especificar la dimensión en la que desea aplicar una agregación personalizada. La agregación personalizada agregada a la dimensión seleccionada provocará cambios en la dimensión. Estos cambios son heredados por todos los cubos que incluyan la dimensión seleccionada.  
  
## <a name="adding-custom-aggregation-unary-operator"></a>Agregar agregación personalizada (operador unario)  
 En la segunda página de **Especificar un operador unario** , debe especificar el atributo primario que desea para la agregación personalizada y la columna de origen en la tabla de dimensión para el operador unario. En**Atributo primario** se muestran los atributos cuya propiedad **Usage** se ha establecido en **Parent**. Si hay más de un atributo primario, debe elegir el atributo primario que corresponda a la relación de elementos primarios y secundarios que desee utilizar. Si no se muestran atributos primarios, la dimensión no contiene una jerarquía de elementos primarios y secundarios válida.  
  
 En **Columna de origen**, debe seleccionar la columna de cadenas que contiene los operadores unarios. (Esta selección establece la propiedad **UnaryOperatorColumn** en el atributo primario). La tabla de dimensión también debe presentar una columna de cadenas que especifique el operador unario de resumen. Los valores de cadenas de esta columna deben contener operadores de agregación válidos. Si una fila está vacía, el miembro correspondiente se calcula de la forma habitual. Si la fórmula de una columna no es válida, se producirá un error en tiempo de ejecución al recuperar un valor de celda que utiliza el miembro. Para obtener más información, vea [Operadores unarios en dimensiones de elementos primarios y secundarios](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md).  
  
  
