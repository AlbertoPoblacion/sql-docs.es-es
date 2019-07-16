---
title: Cuantificar las expresiones (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- universal quantifiers
- effective Boolean value [XQuery]
- quantified expressions [XQuery]
- XQuery, quantified expressions
- every expression [XQuery]
- existential quantifiers [XQuery]
- some expression [XQuery]
- EBV
- expressions [XQuery], quantifiers
ms.assetid: a3a75a6c-8f67-4923-8406-1ada546c817f
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cdbff23d2158dec00b6b8d050d6a4a90341bd23
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946375"
---
# <a name="quantified-expressions-xquery"></a>Expresiones cuantificadas (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Los cuantificadores existenciales y universales especifican semánticas distintas para los operadores booleanos que se aplican a dos secuencias. Esto se muestra en la tabla siguiente.  
  
 *Cuantificador existencial*  
 Dadas dos secuencias, si algún elemento de la primera tiene una coincidencia en la segunda, según el operador de comparación utilizado, el valor devuelto será True.  
  
 *Cuantificador universal*  
 Dadas dos secuencias, si cada elemento de la primera tiene una coincidencia en la segunda, el valor devuelto será True.  
  
 XQuery admite las expresiones cuantificadas de la forma siguiente:  
  
```  
( some | every ) <variable> in <Expression> (,...) satisfies <Expression>  
```  
  
 Puede utilizar estas expresiones en una consulta para aplicar explícitamente una cuantificación existencial o universal a una expresión en una o varias secuencias. En [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la expresión de la cláusula `satisfies` debe dar uno de los resultados siguientes: una secuencia de nodos, una secuencia vacía o un valor booleano. El valor booleano efectivo del resultado de la expresión se utilizará en la cuantificación. La cuantificación existencial que utilice **algunos** devolverá True si al menos uno de los valores enlazados por el cuantificador tiene un resultado True en la expresión de satisfacción. La cuantificación universal que utilice **cada** debe tener True para todos los valores enlazados por el cuantificador.  
  
 Por ejemplo, la siguiente consulta comprueba cada \<ubicación > elemento para ver si tiene un atributo LocationID.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        if (every $WC in //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID)  
        then  
             <Result>All work centers have workcenterLocation ID</Result>  
         else  
             <Result>Not all work centers have workcenterLocation ID</Result>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Puesto que LocationID es un atributo necesario del \<ubicación > elemento, recibirá el resultado esperado:  
  
```  
<Result>All work centers have Location ID</Result>   
```  
  
 En lugar de usar el [método query()](../t-sql/xml/query-method-xml-data-type.md), puede usar el [método value()](../t-sql/xml/value-method-xml-data-type.md) para devolver el resultado al mundo relacional, como se muestra en la siguiente consulta. La consulta devolverá True si todas las ubicaciones de centro de trabajo tienen atributos LocationID. De lo contrario, la consulta devolverá False.  
  
```  
SELECT Instructions.value('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        every $WC in  //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID',   
  'nvarchar(10)') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 La consulta siguiente comprueba si una de las imágenes de producto es pequeña. En el XML de catálogo de productos, se almacenan varios ángulos para cada imagen de producto de distinto tamaño. Asegúrese también de que cada XML de catálogo de productos incluye al menos una imagen pequeña. La consulta siguiente permite comprobarlo:  
  
```  
SELECT ProductModelID, CatalogDescription.value('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     some $F in /PD:ProductDescription/PD:Picture  
        satisfies $F/PD:Size="small"', 'nvarchar(20)') as SmallPicturesStored  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Éste es un resultado parcial:  
  
```  
ProductModelID SmallPicturesStored   
-------------- --------------------  
19             true        
```  
  
## <a name="implementation-limitations"></a>Limitaciones de la implementación  
 Éstas son las limitaciones:  
  
-   La aserción de tipos no se admite como parte del enlazamiento de la variable en las expresiones cuantificadas.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones XQuery](../xquery/xquery-expressions.md)  
  
  
