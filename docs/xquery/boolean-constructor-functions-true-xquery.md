---
title: True (función de XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 611d23ad84df3087a259cbaf60870129b841715b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047619"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Funciones de constructor booleano: true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el valor xs:boolean True. Es equivalente a `xs:boolean("1")`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Ejemplos  
 En este tema se proporciona ejemplos de XQuery con instancias XML almacenadas en varias **xml** columnas de tipo en la base de datos AdventureWorks.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Utilizar la función booleana true() de XQuery  
 En el ejemplo siguiente se consulta sin tipo **xml** variable. La expresión en el **value()** método devuelve un valor booleano **true()** si "aaa" es el valor del atributo. El **value()** método de la **xml** tipo de datos se convierte el valor booleano en bit y lo devuelve.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 En el ejemplo siguiente, la consulta se especifica con un tipo **xml** columna. El `if` expresión comprueba el valor con tipo booleano de la <`ROOT`> elemento y devuelve el XML generado, según corresponda. En el ejemplo, se realizan las tareas siguientes:  
  
-   Crea una colección de esquemas XML que define el <`ROOT`> elemento del tipo xs: Boolean.  
  
-   Crea una tabla con un tipo **xml** columna mediante el uso de la colección de esquemas XML.  
  
-   Se guarda una instancia XML en la columna y se consulta.  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones de Constructor booleano &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
