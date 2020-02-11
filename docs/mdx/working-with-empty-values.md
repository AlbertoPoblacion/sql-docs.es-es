---
title: Trabajar con valores vacíos | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ae8d6262f6502add09376b76a767a3076c830cb8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125847"
---
# <a name="working-with-empty-values"></a>Trabajar con valores vacíos


  Un valor vacío indica que un miembro, tupla o celda específicos están vacíos. Una valor de celda vacío significa que no se han podido encontrar los datos de la celda indicada en la tabla de hechos subyacente, o bien que la tupla de la celda especificada representa una combinación de miembros no aplicable al cubo.  
  
> [!NOTE]  
>  Aunque un valor vacío es distinto del valor cero, el valor vacío suele tratarse como si fuera un cero la mayoría de las veces.  
  
 La consulta siguiente muestra el comportamiento de valores vacíos y valores iguales a cero:  
  
```  
WITH  
//A calculated Product Category that always returns 0  
MEMBER [Product].[Category].[All Products].ReturnZero AS 0  
//Will return true for any null value  
MEMBER MEASURES.ISEMPTYDemo AS ISEMPTY([Measures].[Internet Tax Amount])  
//Will true for any null or zero value  
//To be clear: the expression 0=null always returns true in MDX  
MEMBER MEASURES.IsZero AS [Measures].[Internet Tax Amount]=0  
SELECT  
{[Measures].[Internet Tax Amount],MEASURES.ISEMPTYDemo,MEASURES.IsZero}  
ON COLUMNS,  
[Product].[Category].[Category].ALLMEMBERS  
ON ROWS  
FROM [Adventure Works]  
WHERE([Date].[Calendar].[Calendar Year].&[2001])  
```  
  
 La siguiente información se aplica a los valores vacíos:  
  
-   La función [IsEmpty](../mdx/isempty-mdx.md) devuelve **true** solo si la celda identificada por la tupla especificada en la función está vacía. De lo contrario, la función devuelve **false**.  
  
    > [!NOTE]  
    >  La función **IsEmpty** no puede determinar si una expresión de miembro devuelve un valor null. Para determinar si un miembro NULL se devuelve de una expresión, use el operador [is](../mdx/is-mdx.md).  
  
-   Si el valor de la celda vacía es un operando correspondiente a cualquier de los operadores numéricos (+, -, *, /), el valor de la celda vacía se trata como si fuera un cero cuando el otro operando no es un valor no vacío. Si ambos operandos están vacíos, el operador numérico devuelve el valor de la celda vacía.  
  
-   Si el valor de la celda vacía es un operando correspondiente al operador de concatenación de cadenas (+), el valor de la celda vacía se trata como si fuera una cadena vacía cuando el otro operando no es un valor vacío. Si ambos operandos están vacíos, el operador de concatenación de cadenas devuelve el valor de la celda vacía.  
  
-   Si el valor de la celda vacía es un operando de uno de los operadores de comparación (=. <>, >=, \<=, >, <), el valor de la celda vacía se trata como cero o como una cadena vacía, dependiendo de si el tipo de datos del otro operando es numérico o de cadena, respectivamente. Si ambos operandos están vacíos, los dos se tratan como cero.  
  
-   Cuando se intercalan valores numéricos, el valor de la celda vacía se intercala en el mismo lugar que el cero. Entre el valor de la celda vacía y el cero, la celda vacía se intercala antes que el cero.  
  
-   Cuando se intercalan valores de cadena, el valor de la celda vacía se intercala en el mismo lugar que la cadena vacía. Entre el valor de la celda vacía y la cadena vacía, el valor de la celda vacía se intercala antes que la cadena vacía.  
  
## <a name="dealing-with-empty-values-in-mdx-statements-and-cubes"></a>Administrar valores vacíos de instrucciones MDX y cubos  
 En las instrucciones de expresiones multidimensionales (MDX) se pueden buscar valores vacíos para luego realizar determinados cálculos en las celdas con datos válidos (es decir, no vacías). La eliminación de los valores vacíos para realizar cálculos puede ser importante porque algunos cálculos (como los promedios) pueden ser incorrectos si se incluyen valores de celdas vacías.  
  
 Si los valores vacíos están almacenados en los datos de la tabla de hechos subyacente, se convertirán en ceros de forma predeterminada cuando se procese el cubo. Puede utilizar la opción de **procesamiento de valores NULL** en una medida para controlar si los hechos nulos se convierten en 0, se convierten en un valor vacío, o incluso produce un error durante el procesamiento. Si no desea que aparezcan valores de celdas vacías en los resultados de la consulta, debe crear consultas, miembros calculados o instrucciones de script MDX que eliminen los valores vacíos o que los reemplacen por algún otro valor.  
  
 Para quitar las filas o columnas vacías de una consulta, puede usar la instrucción NON EMPTY previamente a la definición del conjunto de ejes. Por ejemplo, la consulta siguiente solo devuelve la categoría de productos Bikes (bicicletas) porque es la única categoría que se vendió en el año 2001:  
  
 `SELECT`  
  
 `{[Measures].[Internet Tax Amount]}`  
  
 `ON COLUMNS,`  
  
 `//Comment out the following line to display all the empty rows for other Categories`  
  
 `NON EMPTY`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
 De forma más general, para quitar las tuplas vacías de un conjunto puede usar la función NonEmpty. La consulta siguiente muestra dos medidas calculadas; la primera de ellas cuenta el número de categorías de productos y la segunda muestra el número de categorías de productos que tienen valores para la medida [Internet Tax Amount] y el año natural 2001:  
  
 `WITH`  
  
 `MEMBER MEASURES.CategoryCount AS`  
  
 `COUNT([Product].[Category].[Category].MEMBERS)`  
  
 `MEMBER MEASURES.NonEmptyCategoryCountFor2001 AS`  
  
 `COUNT(`  
  
 `NONEMPTY(`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `,([Date].[Calendar].[Calendar Year].&[2001], [Measures].[Internet Tax Amount])`  
  
 `))`  
  
 `SELECT`  
  
 `{MEASURES.CategoryCount,MEASURES.NonEmptyCategoryCountFor2001 }`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 Para obtener más información, vea [unempty &#40;MDX&#41;](../mdx/nonempty-mdx.md).  
  
## <a name="empty-values-and-comparison-operators"></a>Valores vacíos y operadores de comparación  
 Cuando hay valores vacíos en los datos, los operadores lógicos y de comparación pueden devolver un tercer resultado EMPTY en lugar de simplemente TRUE o FALSE. Esta necesidad de una lógica de tres valores es el origen de muchos errores de la aplicación. En estas tablas se destaca el efecto que supone escribir comparaciones con valores vacíos.  
  
 En la siguiente tabla se muestra el resultado de aplicar un operador AND a dos operandos booleanos.  
  
|y|TRUE|EMPTY|FALSE|  
|---------|----------|-----------|-----------|  
|**TRUE**|TRUE|FALSE|FALSE|  
|**VACÍA**|FALSE|EMPTY|FALSE|  
|**FALSE**|FALSE|FALSE|FALSE|  
  
 En la siguiente tabla se muestra el resultado de aplicar un operador OR a dos operandos booleanos.  
  
|O BIEN|TRUE|FALSE|  
|--------|----------|-----------|  
|**TRUE**|TRUE|TRUE|  
|**VACÍA**|TRUE|TRUE|  
|**FALSE**|TRUE|FALSE|  
  
 En esta tabla se muestra cómo el operador NOT niega, o invierte, el resultado de un operador booleano.  
  
|Expresión booleana a la que se aplica el operador NOT|Se evalúa como|  
|-------------------------------------------------------------|------------------|  
|TRUE|FALSE|  
|EMPTY|EMPTY|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de funciones MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Referencia de operadores MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Expresiones &#40;&#41;MDX](../mdx/expressions-mdx.md)  
  
  
