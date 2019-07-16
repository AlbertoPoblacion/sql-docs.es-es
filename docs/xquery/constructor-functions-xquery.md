---
title: Funciones de constructor (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- constructor functions [XQuery]
ms.assetid: 98562d0e-d0e0-4f62-b001-90acbac67277
author: rothja
ms.author: jroth
ms.openlocfilehash: 7f64c9ff6664410983d9c3ce7ebdbf07e493ca03
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038990"
---
# <a name="constructor-functions-xquery"></a>Funciones de constructor (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Desde una entrada especificada, las funciones de constructor crean instancias de cualquiera de los tipos atómicos integrados o definidos por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
TYP($atomicvalue as xdt:anyAtomicType?  
  
) as TYP?  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *$strval*  
 Cadena que se convertirá.  
  
 *TYP*  
 Cualquier tipo XSD integrado.  
  
## <a name="remarks"></a>Comentarios  
 Se admiten constructores para tipos XSD atómicos base y derivados. Sin embargo, los subtipos de **xs: Duration**, que incluye **xdt: yearmonthduration y xdt: daytimeduration**, y **xs: QName**, **NMTOKEN**, y **xs: Notation** no se admiten. Los tipos atómicos definidos por el usuario que están disponibles en las colecciones de esquemas asociadas también están disponibles, siempre que se deriven directa o indirectamente de los tipos siguientes.  
  
#### <a name="supported-base-types"></a>Tipos base compatibles  
 Éstos son los tipos base admitidos:  
  
-   xs:string  
  
-   xs:boolean  
  
-   xs:decimal  
  
-   xs:float  
  
-   xs:double  
  
-   xs:duration  
  
-   xs:dateTime  
  
-   xs:time  
  
-   xs:date  
  
-   xs:gYearMonth  
  
-   xs:gYear  
  
-   xs:gMonthDay  
  
-   xs:gDay  
  
-   xs:gMonth  
  
-   xs:hexBinary  
  
-   xs:base64Binary  
  
-   xs:anyURI  
  
#### <a name="supported-derived-types"></a>Tipos derivados compatibles  
 Éstos son los tipos derivados admitidos:  
  
-   xs:normalizedString  
  
-   xs:token  
  
-   xs:language  
  
-   xs:Name  
  
-   xs:NCName  
  
-   xs:ID  
  
-   xs:IDREF  
  
-   xs:ENTITY  
  
-   xs:integer  
  
-   xs:nonPositiveInteger  
  
-   xs:negativeInteger  
  
-   xs:long  
  
-   xs:int  
  
-   xs:short  
  
-   xs:byte  
  
-   xs:nonNegativeInteger  
  
-   xs:unsignedLong  
  
-   xs:unsignedInt  
  
-   xs:unsignedShort  
  
-   xs:unsignedByte  
  
-   xs:positiveInteger  
  
 SQL Server también admite el doblado constante para invocaciones de funciones de construcción de las formas siguientes:  
  
-   Si el argumento es un literal de cadena, la expresión se evaluará durante la compilación. Cuando el valor no satisfaga las restricciones de tipo, se producirá un error estático.  
  
-   Si el argumento es un literal de otro tipo, la expresión se evaluará durante la compilación. Cuando el valor no satisfaga las restricciones de tipo, se devolverá la secuencia vacía.  
  
## <a name="examples"></a>Ejemplos  
 En este tema se proporciona ejemplos de XQuery con instancias XML almacenadas en varias **xml** columnas de tipo en la base de datos AdventureWorks.  
  
### <a name="a-using-the-datetime-xquery-function-to-retrieve-older-product-descriptions"></a>A. Usar la función dateTime() de XQuery para recuperar descripciones antiguas de productos  
 En este ejemplo, un documento XML de ejemplo primero se asigna a un **xml** variable de tipo. Este documento contiene tres ejemplos <`ProductDescription`> elementos, con cada uno de ellos contiene un <`DateCreated`> elemento secundario.  
  
 A continuación, se realiza una consulta en la variable para recuperar solo las descripciones de producto que se crearon antes de una fecha específica. Para fines de comparación, la consulta utiliza la **xs:DateTime()** función constructora para escribir las fechas.  
  
```  
declare @x xml  
set @x = '<root>  
<ProductDescription ProductID="1" >  
  <DateCreated DateValue="2000-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
<ProductDescription  ProductID="2" >  
  <DateCreated DateValue="2001-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
<ProductDescription ProductID="3" >  
  <DateCreated DateValue="2002-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
</root>'  
  
select @x.query('  
     for $PD in  /root/ProductDescription  
     where xs:dateTime(data( ($PD/DateCreated/@DateValue)[1] )) < xs:dateTime("2001-01-01T00:00:00Z")  
     return  
        element Product  
       {   
        ( attribute ProductID { data($PD/@ProductID ) },  
        attribute DateCreated { data( ($PD/DateCreated/@DateValue)[1] ) } )  
        }  
 ')  
```  
  
 Observe lo siguiente en la consulta anterior:  
  
-   El bucle FOR... Estructura de bucle de dónde se usa para recuperar el \<ProductDescription > elemento que cumpla la condición especificada en la cláusula WHERE.  
  
-   El **dateTime() de** función constructora que se usa para construir **dateTime** escriba valores para que se puedan comparar adecuadamente.  
  
-   Finalmente, la consulta construye el XML resultante. Dado que se pretende construir una secuencia de atributos, en la construcción de XML se utilizan comas y paréntesis.  
  
 Éste es el resultado:  
  
```  
<Product   
   ProductID="1"   
   DateCreated="2000-01-01T00:00:00Z"/>  
```  
  
## <a name="see-also"></a>Vea también  
 [Construcción de XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)   
 [Funciones de XQuery con el tipo de datos xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
