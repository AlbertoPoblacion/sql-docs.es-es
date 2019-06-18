---
title: Función Lookup (Generador de informes y SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 333c75f3ca10d1ed6ecd738a3dc76a32a53305c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65579584"
---
# <a name="report-builder-functions---lookup-function"></a>Funciones del Generador de informes: función Lookup
  Devuelve el primer valor coincidente para el nombre especificado de un conjunto de datos que contiene pares nombre/valor.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *source_expression*  
 (**Variant**) Una expresión que se evalúa en el ámbito actual y que especifica el nombre o la clave que se buscará. Por ejemplo, `=Fields!ProdID.Value`.  
  
 *destination_expression*  
 (**Variant**) Una expresión que se evalúa para cada fila de un conjunto de datos y que especifica el nombre o la clave que se hará coincidir. Por ejemplo, `=Fields!ProductID.Value`.  
  
 *result_expression*  
 (**Variant**) Una expresión que se evalúa para la fila de un conjunto de datos donde *source_expression* = *destination_expression*, y que especifica el valor que se va a recuperar. Por ejemplo, `=Fields!ProductName.Value`.  
  
 *conjunto de datos*  
 Una constante que especifica el nombre de un conjunto de datos del informe. Por ejemplo, "Productos".  
  
## <a name="return"></a>Devolución  
 Devuelve **Variant**o **Nothing** si no hay ninguna coincidencia.  
  
## <a name="remarks"></a>Notas  
 Use **Lookup** para recuperar el valor del conjunto de datos especificado correspondiente a un par nombre/valor donde hay una relación de uno a uno. Por ejemplo, para un campo de identificador en una tabla, puede usar **Lookup** para recuperar el campo Name correspondiente de un conjunto de datos que no está enlazado a la región de datos.  
  
 **Lookup** realiza las operaciones siguientes:  
  
-   Evalúa la expresión de origen en el ámbito actual.  
  
-   Evalúa la expresión de destino para cada fila del conjunto de datos especificado una vez aplicados los filtros, según la intercalación del conjunto de datos especificado.  
  
-   En la primera coincidencia de las expresiones de origen y de destino, evalúa la expresión de resultado para dicha fila del conjunto de datos.  
  
-   Devuelve el valor de la expresión de resultado.  
  
 Para recuperar varios valores para un único nombre o campo de clave donde hay una relación de uno a varios, use la [función LookupSet &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/report-builder-functions-lookupset-function.md). Para llamar a **Lookup** para un conjunto de valores, use la [función Multilookup &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/report-builder-functions-multilookup-function.md).  
  
 Se aplican las siguientes restricciones:  
  
-   Se evalúa**Lookup** después de aplicar todas las expresiones de filtro.  
  
-   Solo se admite un nivel de búsqueda. Un origen, un destino o una expresión de resultado no pueden incluir una referencia a una función de búsqueda.  
  
-   Las expresiones de origen y de destino deben dar el mismo tipo de datos. El tipo de devolución es el mismo que el tipo de datos de la expresión de resultado evaluada.  
  
-   Las expresiones de origen, destino y resultado no pueden incluir referencias a variables de informe o de grupo.  
  
-   **Lookup** no se puede usar como una expresión para los siguientes elementos de informe:  
  
    -   Cadenas de conexión dinámicas para un origen de datos.  
  
    -   Campos calculados de un conjunto de datos.  
  
    -   Parámetros de consulta de un conjunto de datos.  
  
    -   Filtros de un conjunto de datos.  
  
    -   Parámetros de informe.  
  
    -   La propiedad Report.Language.  
  
 Para más información, vea [Funciones del generador de informes - referencia de funciones de agregado &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) y [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se supone que una tabla está enlazada a un conjunto de datos que incluye un campo para el identificador de producto ProductID. Un conjunto de datos independiente denominado "Product" contiene el identificador de producto, ID, y el nombre de producto, Name.  
  
 En la expresión siguiente, **Lookup** compara el valor de ProductID con ID en cada fila del conjunto de datos denominado "Product" y, cuando se encuentra una coincidencia, devuelve el valor del campo Name para dicha fila.  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar expresiones en informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
