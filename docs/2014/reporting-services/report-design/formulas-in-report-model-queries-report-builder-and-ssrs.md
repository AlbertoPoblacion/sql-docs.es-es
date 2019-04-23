---
title: Fórmulas en consultas de modelo de informe (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10151"
ms.assetid: fbf68c59-7afc-4afe-bfcd-40ce84629af0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 18390c8cb1df552b746f16c5eb569f08063e7763
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59934421"
---
# <a name="formulas-in-report-model-queries-report-builder-and-ssrs"></a>Utilizar fórmulas en consultas de modelo de informe (Generador de informes y SSRS)
  Las fórmulas son los cálculos que se realizan en los valores de un informe que utiliza un modelo de informe como origen de datos. Una fórmula puede contener funciones, operadores, constantes y referencias a campos o entidades. Las fórmulas permiten combinar, agregar, filtrar y evaluar datos numéricos y de texto. Puede crear fórmulas y guardarlas como campos nuevos, o puede modificar las fórmulas de campos existentes.  
  
 Las fórmulas no son expresiones RDL y no comienzan con un signo de igual (=). Para más información sobre las expresiones RDL, vea [Expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 Las fórmulas pueden tener un aspecto similar al siguiente:  
  
-   **Sum Line Total**  
  
-   6+12  
  
-   `SUM`(`IF`(**Finished Goods Flag**, "Finished", "Unfinished"))  
  
 Después de definir una fórmula, puede ver el resultado en el diseñador de consultas.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="references"></a>References  
 Una referencia es un nombre de campo. Puede ser un nombre de campo existente en la entidad o un nombre de campo calculado que se haya creado y agregado a la lista Campos. La referencia indica al Generador de informes dónde debe buscar los valores o los datos que se desean utilizar en una fórmula. Puede hacer referencia a los campos de la entidad de contexto y a los de otras entidades de una fórmula o utilizar el valor de un campo en varias fórmulas.  
  
 Cuando se utilizan referencias, el procesador de informes ejecuta la fórmula en cada valor del campo. Por ejemplo, imagine que un campo contiene el total de ventas anuales de los últimos cinco años. Este campo contiene cinco valores; cada uno representa el total de ventas de un año determinado. Si la fórmula contiene una referencia a este campo, calcula el nuevo valor mediante cada valor individual.  
  
## <a name="operators"></a>Operadores  
 Los operadores especifican el tipo de cálculo que se desea realizar en los valores de una fórmula. Hay tres tipos diferentes de operadores de cálculo: aritmético, de comparación y de texto. Los operadores se indican mediante símbolos, como el signo más (+).  
  
 **Operadores aritméticos.** Los operadores aritméticos realizan las operaciones matemáticas básicas, como la suma, la resta o la multiplicación, combinan números y generan resultados numéricos.  
  
 **Operadores de comparación.** Puede comparar dos valores mediante los operadores de comparación. Cuando se comparan dos valores mediante estos operadores, el resultado es un valor lógico: TRUE o FALSE.  
  
 **Operador de concatenación de texto** Use la Y comercial (&) para unir, o concatenar, una o más cadenas de texto a fin de generar un único fragmento de texto.  
  
##  <a name="Constants"></a> Constantes  
 Una constante es un valor que no se calcula y que, por lo tanto, no cambia. El Generador de informes utiliza las constantes siguientes: `True`, `False` y `Empty`. Estas constantes se utilizan para evaluar campos booleanos. Por ejemplo, imagine que tiene un campo denominado IsDiscontinued. Los únicos valores válidos para este campo son True, False o Empty (" ").  
  
##  <a name="Functions"></a> Funciones  
 Las funciones son fórmulas predefinidas que realizan cálculos utilizando valores específicos, denominados *argumentos*, especificados en un orden concreto. Los argumentos pueden ser valores o campos literales, o combinaciones de ambos. Cuando se utilizan campos en las fórmulas, el nombre de campo representa a cada instancia del campo. Si el argumento es un valor literal, quizás deba indicar que lo es mediante caracteres específicos.  
  
 Las funciones se pueden utilizar para realizar cálculos sencillos o complejos. La estructura de una función consta del nombre de la función seguido de los argumentos de la función separados por comas y encerrados entre paréntesis.  
  
 ![Ejemplo de una función.](../media/functionexample.gif "Ejemplo de una función.")  
  
 Los argumentos pueden ser referencias de campo, números, texto y valores lógicos como `TRUE` o `FALSE`. Los argumentos pueden ser también constantes, fórmulas u otras funciones. Los argumentos que se escriban deben generar un valor válido para dicho argumento. Por ejemplo, si la fórmula consiste en multiplicar dos enteros, el resultado no puede ser una cadena de texto.  
  
 El Generador de informes contiene las nueve categorías de funciones de uso habitual siguientes:  
  
|||  
|-|-|  
|Funciones de agregado|`AVG`, `COUNT`, `COUNTDISTINCT`, `MAX`, `MIN`, `STDEV`, `STDEVP`, `SUM`, `VAR`, `VARP`|  
|Funciones condicionales|`IF`, `IN`, `SWITCH`|  
|Funciones de conversión|`INT`, `DECIMAL`, `FLOAT`, `TEXT`|  
|Funciones de fecha y hora|`DATE`, `DATEADD`, `DATEDIFF`, `DATETIME`, `DATEONLY`, `DAY`, `DAYOFWEEK`, `DAYOFYEAR`, `HOUR`, `MINUTE`, `MONTH`, `NOW`, `QUARTER`, `SECOND`, `TIMEONLY`, `TODAY`, `WEEK`, `YEAR`|  
|Funciones de información|`GETUSERCULTURE`, `GETUSERID`|  
|Funciones lógicas|`AND`, `NOT`, `OR`|  
|Funciones matemáticas|`MOD`, `ROUND`, `TRUNC`|  
|Operadores|Suma (+), División (/), Igual que (=), Exponenciación (^), Mayor que (&gt;), Mayor o igual que (>), Menor que (z;), Menor o igual que (<=), Multiplicación (*), Negativo (-), No es igual que (<>), Resta (-)|  
|Funciones de texto|`CONCAT`, `FIND`, `LEFT`, `LENGTH`, `LOWER`, `LTRIM`, `REPLACE`, `RIGHT`, `RTRIM`, `SUBSTRING`, `UPPER`|  
  
  
