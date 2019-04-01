---
title: Columnas con el nombre de una prueba de nodo XPath | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6b6e5209bea06a5b1fa951cb8bcaa2b004870b8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510132"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>Columnas con el nombre de una prueba de nodo XPath
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Si el nombre de columna es una de las pruebas de nodo XPath, se asignará el contenido tal y como se muestra en la tabla siguiente. Cuando el nombre de la columna es una prueba de nodo XPath, se asigna el contenido al nodo correspondiente. Si el tipo SQL de la columna es **xml**, se devolverá un error.  
  
|Nombre de la columna|Comportamiento|  
|-----------------|--------------|  
|text()|En el caso de las columnas con el nombre text(), el valor de cadena de la misma se agregará como un nodo de texto.|  
|comment()|En el caso de las columnas con el nombre comment(), el valor de cadena de la misma se agregará como un comentario XML.|  
|node()|En el caso de las columnas con el nombre node(), el resultado será el mismo que cuando el nombre de la columna es un carácter comodín (*).|  
|processing-instruction(name)|En el caso de las columnas con el nombre de una instrucción de procesamiento, su valor de cadena se agregará como el valor PI para el nombre de destino de la instrucción de procesamiento.|  
  
 La siguiente consulta muestra el uso de las pruebas de nodo como nombres de columna. Agrega nodos de texto y comentarios en el XML resultante.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 El resultado es el siguiente:  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>Consulte también  
 [Usar el modo PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
