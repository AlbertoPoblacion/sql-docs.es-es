---
title: Equiparación de tipos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence type matching [XQuery]
- XQuery, sequence type matching
ms.assetid: 8c56fb69-ca04-4aba-b55a-64ae216c492d
author: rothja
ms.author: jroth
ms.openlocfilehash: 164092d91a6450815662c5022ac6eb62941e3b16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946224"
---
# <a name="type-system---sequence-type-matching"></a>Sistema de tipo: Equiparación de tipos de secuencia
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Un valor de expresión XQuery siempre es una secuencia de cero o más elementos. Un elemento puede ser un valor atómico o un nodo. El tipo de secuencia hace referencia a la capacidad de equiparar el tipo de secuencia devuelto por una expresión de consulta a un tipo específico. Por ejemplo:  
  
-   Si el valor de la expresión es atómico, es posible que desee saber si es de tipo entero, decimal o cadena.  
  
-   Si el valor de la expresión es un nodo XML, es posible que desee saber si es un nodo de comentarios, un nodo de instrucciones de procesamiento o un nodo de texto.  
  
-   También puede saber si la expresión devuelve un elemento XML o un nodo de atributo con un nombre y tipo específicos.  
  
 Para conocer el tipo de secuencia correspondiente se puede utilizar el operador booleano `instance of`. Para obtener más información sobre la `instance of` expresión, vea [expresiones SequenceType &#40;XQuery&#41;](../xquery/sequencetype-expressions-xquery.md).  
  
## <a name="comparing-the-atomic-value-type-returned-by-an-expression"></a>Comparar el tipo de valor atómico devuelto por una expresión  
 Si una expresión devuelve una secuencia de valores atómicos, es posible que se deba buscar el tipo del valor en la secuencia. Los ejemplos siguientes muestran cómo se puede utilizar la sintaxis de tipo de secuencia para evaluar el tipo de valor atómico devuelto por una expresión.  
  
### <a name="example-determining-whether-a-sequence-is-empty"></a>Ejemplo: Determinar si una secuencia está vacía  
 El **empty() de** tipo de secuencia se puede usar en una expresión de tipo de secuencia para determinar si la secuencia devuelta por la expresión especificada es una secuencia vacía.  
  
 En el ejemplo siguiente, el esquema XML permite la <`root`> elemento tenga el atributo nillable:  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="root" nillable="true" type="byte"/>  
</schema>'  
GO  
```  
  
 Ahora, si una instancia XML con tipo especifica un valor para el <`root`> elemento, `instance of empty()` devuelve False.  
  
```  
DECLARE @var XML(SC1)  
SET @var = '<root>1</root>'  
-- The following returns False  
SELECT @var.query('data(/root[1]) instance of  empty() ')  
GO  
```  
  
 Si el <`root`> elemento tiene el atributo nillable en la instancia, su valor es una secuencia vacía y el `instance of empty()` devuelve True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xsi:nil="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" />'  
SELECT @var.query('data(/root[1]) instance of  empty() ')  
GO  
```  
  
### <a name="example-determining-the-type-of-an-attribute-value"></a>Ejemplo: Determinar el tipo de un valor de atributo  
 En ocasiones se desea evaluar el tipo de secuencia devuelto por una expresión antes de su procesamiento. Por ejemplo, puede haber un esquema XML en el que se defina un nodo como tipo de unión. En el ejemplo siguiente, el esquema XML de la colección define el atributo `a` como un tipo de unión cuyo valor puede ser de tipo decimal o de cadena.  
  
```  
-- Drop schema collection if it exists.  
-- DROP XML SCHEMA COLLECTION SC.  
-- GO  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
  <element name="root">  
    <complexType>  
       <sequence/>  
         <attribute name="a">  
            <simpleType>  
               <union memberTypes="decimal string"/>  
            </simpleType>  
         </attribute>  
     </complexType>  
  </element>  
</schema>'  
GO  
```  
  
 Antes de procesar una instancia XML con tipo, se puede conocer el tipo del valor `a` del atributo. En el ejemplo siguiente, el valor `a` del atributo es un tipo decimal. Por tanto `, instance of xs:decimal` devuelve True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root a="2.5"/>'  
SELECT @var.query('data((/root/@a)[1]) instance of xs:decimal')  
GO  
```  
  
 Ahora, cambie el valor `a` del atributo a un tipo de cadena. `instance of xs:string` devolverá True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root a="Hello"/>'  
SELECT @var.query('data((/root/@a)[1]) instance of xs:string')  
GO  
```  
  
### <a name="example-cardinality-in-sequence-expressions"></a>Ejemplo: Cardinalidad en expresiones de secuencia  
 Este ejemplo ilustra el efecto de la cardinalidad en una expresión de secuencia. El siguiente esquema XML define un <`root`> elemento que es de tipo byte y es "nillable".  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="root" nillable="true" type="byte"/>  
</schema>'  
GO  
```  
  
 En la consulta siguiente, dado que la expresión devuelve un singleton de tipo byte, `instance of` devuelve True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root>111</root>'  
SELECT @var.query('data(/root[1]) instance of  xs:byte ')   
GO  
```  
  
 Si realiza la <`root`> elemento nil, su valor es una secuencia vacía. En otras palabras, la expresión, `/root[1]`, devuelve una secuencia vacía. En consecuencia, `instance of xs:byte` devuelve False. Observe que, en este caso, la cardinalidad predeterminada es 1.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xsi:nil="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"></root>'  
SELECT @var.query('data(/root[1]) instance of  xs:byte ')   
GO  
-- result = false  
```  
  
 Si se especifica la cardinalidad agregando el indicador de repetición (`?`), la expresión de secuencia devuelve True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xsi:nil="true" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"></root>'  
SELECT @var.query('data(/root[1]) instance of  xs:byte? ')   
GO  
-- result = true  
```  
  
 Tenga en cuenta que la comprobación en una expresión de tipo de secuencia se realiza en dos etapas:  
  
1.  Primero, se determina si el tipo de la expresión coincide con el tipo especificado.  
  
2.  En caso afirmativo, la comprobación determina si el número de elementos devueltos por la expresión coincide con el indicador de repetición especificado.  
  
 Si se dan ambas condiciones, la expresión `instance of` devuelve True.  
  
### <a name="example-querying-against-an-xml-type-column"></a>Ejemplo: Realizar una consulta en una columna de tipo xml  
 En el ejemplo siguiente, se especifica una consulta en una columna Instructions de **xml** escriba en el [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de datos. Es una columna XML con tipo, porque tiene un esquema asociado. El esquema XML define el atributo `LocationID` del tipo entero. Por lo tanto, en la expresión de secuencia, el `instance of xs:integer?` devuelve True.  
  
```  
SELECT Instructions.query('   
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
data(/AWMI:root[1]/AWMI:Location[1]/@LocationID) instance of xs:integer?') as Result   
FROM Production.ProductModel   
WHERE ProductModelID = 7  
```  
  
## <a name="comparing-the-node-type-returned-by-an-expression"></a>Comparar el tipo de nodo devuelto por una expresión  
 Si una expresión devuelve una secuencia de nodos, es posible que se deba determinar el tipo del nodo en la secuencia. Los ejemplos siguientes muestran cómo se puede utilizar la sintaxis de tipo de secuencia para evaluar el tipo de nodo devuelto por una expresión. Puede utilizar los siguientes tipos de secuencia:  
  
-   **Item()** -coincide con cualquier elemento de la secuencia.  
  
-   **Node()** -determina si la secuencia es un nodo.  
  
-   **//processing-instruction ()** -determina si la expresión devuelve una instrucción de procesamiento.  
  
-   **Comment()** -determina si la expresión devuelve un comentario.  
  
-   **Document-Node()** -determina si la expresión devuelve un nodo de documento.  
  
 El siguiente ejemplo ilustra estos tipos de secuencia.  
  
### <a name="example-using-sequence-types"></a>Ejemplo: Uso de tipos de secuencia  
 En este ejemplo, se ejecutan varias consultas en una variable XML sin tipo. Estas consultas ilustran el uso de tipos de secuencia.  
  
```  
DECLARE @var XML  
SET @var = '<?xml-stylesheet href="someValue" type="text/xsl" ?>  
<root>text node  
  <!-- comment 1 -->   
  <a>Data a</a>  
  <!-- comment  2 -->  
</root>'  
```  
  
 En la primera consulta, la expresión devuelve el valor con tipo del elemento <`a`>. En la segunda consulta, la expresión devuelve el elemento <`a`>. Ambos son elementos. Por tanto, ambas consultas devuelven True.  
  
```  
SELECT @var.query('data(/root[1]/a[1]) instance of item()')  
SELECT @var.query('/root[1]/a[1] instance of item()')  
```  
  
 Todas las expresiones XQuery de las tres consultas siguientes devuelven el nodo de elemento secundario de la <`root`> elemento. Por tanto, la expresión de tipo de secuencia (`instance of node()`) devuelve True y las otras dos expresiones (`instance of text()` y `instance of document-node()`) devuelven False.  
  
```  
SELECT @var.query('(/root/*)[1] instance of node()')  
SELECT @var.query('(/root/*)[1] instance of text()')  
SELECT @var.query('(/root/*)[1] instance of document-node()')   
```  
  
 En la siguiente consulta, el `instance of document-node()` expresión devuelve True, porque el elemento primario de la <`root`> elemento es un nodo de documento.  
  
```  
SELECT @var.query('(/root/..)[1] instance of document-node()') -- true  
```  
  
 En la consulta siguiente, la expresión recupera el primer nodo de la instancia XML. Debido a que es un nodo de instrucciones de procesamiento, la expresión `instance of processing-instruction()` devuelve True.  
  
```  
SELECT @var.query('(/node())[1] instance of processing-instruction()')  
```  
  
### <a name="implementation-limitations"></a>Limitaciones de la implementación  
 Éstas son las limitaciones específicas:  
  
-   **Document-Node()** con el tipo de contenido no se admiten la sintaxis.  
  
-   **processing-instruction(Name)** sintaxis no es compatible.  
  
## <a name="element-tests"></a>Pruebas de elementos  
 Una prueba de elementos tiene como finalidad equiparar el nodo de elemento devuelto por una expresión a un nodo de elemento con un nombre y tipo específicos. Se pueden utilizar estas pruebas de elementos:  
  
```  
element ()  
element(ElementName)  
element(ElementName, ElementType?)   
element(*, ElementType?)  
```  
  
## <a name="attribute-tests"></a>Pruebas de atributos  
 La prueba de atributos determina si el atributo devuelto por una expresión es un nodo de atributo. Se pueden utilizar estas pruebas de atributos.  
  
 `attribute()`  
  
 `attribute(AttributeName)`  
  
 `attribute(AttributeName, AttributeType)`  
  
## <a name="test-examples"></a>Ejemplos de pruebas  
 Los ejemplos siguientes ilustran situaciones en las que son útiles las pruebas de elementos y atributos.  
  
### <a name="example-a"></a>Ejemplo A  
 El siguiente esquema XML define el `CustomerType` tipo complejo donde <`firstName`> y <`lastName`> elementos son opcionales. Puede que sea necesario determinar, para una instancia XML específica, si existe un nombre para un cliente concreto.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="myNS" xmlns:ns="myNS">  
  <complexType name="CustomerType">  
     <sequence>  
        <element name="firstName" type="string" minOccurs="0"   
                  nillable="true" />  
        <element name="lastName" type="string" minOccurs="0"/>  
     </sequence>  
  </complexType>  
  <element name="customer" type="ns:CustomerType"/>  
</schema>  
'  
GO  
DECLARE @var XML(SC)  
SET @var = '<x:customer xmlns:x="myNS">  
<firstName>SomeFirstName</firstName>  
<lastName>SomeLastName</lastName>  
</x:customer>'  
```  
  
 La consulta siguiente utiliza una `instance of element (firstName)` expresión para determinar si el primer elemento secundario de <`customer`> es un elemento cuyo nombre es <`firstName`>. En este caso, devuelve True.  
  
```  
SELECT @var.query('declare namespace x="myNS";   
     (/x:customer/*)[1] instance of element (firstName)')  
GO  
```  
  
 Si quita el <`firstName`> elemento de la instancia, la consulta devolverá False.  
  
 También se puede utilizar lo siguiente:  
  
-   La sintaxis de tipo de secuencia `element(ElementName, ElementType?)`, como se muestra en la consulta siguiente. Busca un nodo de elemento nillable o no nillable coincidente cuyo nombre sea `firstName` y cuyo tipo sea `xs:string`.  
  
    ```  
    SELECT @var.query('declare namespace x="myNS";   
    (/x:customer/*)[1] instance of element (firstName, xs:string?)')  
    ```  
  
-   La sintaxis de tipo de secuencia `element(*, type?)`, como se muestra en la consulta siguiente. Busca un nodo de elemento coincidente cuyo tipo sea `xs:string`, sin importar su nombre.  
  
    ```  
    SELECT @var.query('declare namespace x="myNS"; (/x:customer/*)[1] instance of element (*, xs:string?)')  
    GO  
    ```  
  
### <a name="example-b"></a>Ejemplo B  
 En el ejemplo siguiente se muestra cómo determinar si el nodo devuelto por una expresión es un nodo de elemento con un nombre específico. Usa el **element()** probar.  
  
 En el ejemplo siguiente, los dos <`Customer`> elementos de la instancia XML que se consultan son de dos tipos diferentes, `CustomerType` y `SpecialCustomerType`. Suponga que desea conocer el tipo de la <`Customer`> elemento devuelto por la expresión. En la siguiente colección de esquemas XML se definen los tipos `CustomerType` y `SpecialCustomerType`.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
          targetNamespace="myNS"  xmlns:ns="myNS">  
  <complexType name="CustomerType">  
    <sequence>  
      <element name="firstName" type="string"/>  
      <element name="lastName" type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="SpecialCustomerType">  
     <complexContent>  
       <extension base="ns:CustomerType">  
        <sequence>  
            <element name="Age" type="int"/>  
        </sequence>  
       </extension>  
     </complexContent>  
    </complexType>  
   <element name="customer" type="ns:CustomerType"/>  
</schema>  
'  
GO  
```  
  
 Esta colección de esquemas XML se utiliza para crear un tipo **xml** variable. La instancia XML asignada a esta variable tiene dos <`customer`> elementos de dos tipos diferentes. El primer elemento es de tipo `CustomerType` y el segundo elemento es de tipo `SpecialCustomerType`.  
  
```  
DECLARE @var XML(SC)  
SET @var = '  
<x:customer xmlns:x="myNS">  
   <firstName>FirstName1</firstName>  
   <lastName>LastName1</lastName>  
</x:customer>  
<x:customer xsi:type="x:SpecialCustomerType" xmlns:x="myNS" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <firstName> FirstName2</firstName>  
   <lastName> LastName2</lastName>  
   <Age>21</Age>  
</x:customer>'  
```  
  
 En la consulta siguiente, la expresión `instance of element (*, x:SpecialCustomerType ?)` devuelve False, porque la expresión devuelve el primer elemento de cliente que no es de tipo `SpecialCustomerType`.  
  
```  
SELECT @var.query('declare namespace x="myNS";   
    (/x:customer)[1] instance of element (*, x:SpecialCustomerType ?)')  
```  
  
 Si cambia la expresión de la consulta anterior y recuperar el segundo <`customer`> elemento (`/x:customer)[2]`), el `instance of` devolverá True.  
  
### <a name="example-c"></a>Ejemplo C  
 En este ejemplo se utiliza la prueba de atributos. El siguiente esquema XML define el tipo complejo CustomerType, con los atributos CustomerID y Age. El atributo Age es opcional. Para una instancia XML específica, que es posible que desee para determinar si el atributo Age está presente en el <`customer`> elemento.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
       targetNamespace="myNS" xmlns:ns="myNS">  
<complexType name="CustomerType">  
  <sequence>  
     <element name="firstName" type="string" minOccurs="0"   
               nillable="true" />  
     <element name="lastName" type="string" minOccurs="0"/>  
  </sequence>  
  <attribute name="CustomerID" type="integer" use="required" />  
  <attribute name="Age" type="integer" use="optional" />  
 </complexType>  
 <element name="customer" type="ns:CustomerType"/>  
</schema>  
'  
GO  
```  
  
 La consulta siguiente devuelve True porque hay un nodo de atributo cuyo nombre es `Age` en la instancia XML que se consulta. En esta expresión se utiliza la prueba de atributos `attribute(Age)`. Como los atributos no están ordenados, la consulta utiliza la expresión FLWOR para recuperar todos los atributos y, después, comprobar cada atributo mediante la expresión `instance of`. El ejemplo crea primero una colección de esquemas XML para crear un tipo **xml** variable.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<x:customer xmlns:x="myNS" CustomerID="1" Age="22" >  
<firstName>SomeFName</firstName>  
<lastName>SomeLName</lastName>  
</x:customer>'  
SELECT @var.query('declare namespace x="myNS";   
FOR $i in /x:customer/@*  
RETURN  
    IF ($i instance of attribute (Age)) THEN  
        "true"  
        ELSE  
        ()')     
GO  
  
```  
  
 Si se quita el atributo opcional `Age` de la instancia, la consulta anterior devuelve False.  
  
 En la prueba de atributos se puede especificar el nombre y tipo del atributo (`attribute(name,type)`).  
  
```  
SELECT @var.query('declare namespace x="myNS";   
FOR $i in /x:customer/@*  
RETURN  
    IF ($i instance of attribute (Age, xs:integer)) THEN  
        "true"  
        ELSE  
        ()')  
```  
  
 Como alternativa, puede especificar el `attribute(*, type)` sintaxis de tipo de secuencia. De esta manera se buscará una coincidencia para el nodo de atributo, si el tipo de atributo coincide con el tipo especificado, sea cual sea su nombre.  
  
### <a name="implementation-limitations"></a>Limitaciones de la implementación  
 Éstas son las limitaciones específicas:  
  
-   En la prueba de elemento, el nombre de tipo debe ir seguido por el indicador de repetición ( **?** ).  
  
-   **Element (ElementName, TypeName)** no se admite.  
  
-   **elemento (\*, TypeName)** no se admite.  
  
-   **Schema-Element()** no se admite.  
  
-   **Schema-Attribute(AttributeName)** no se admite.  
  
-   Consulta explícita para **xsi: Type** o **xsi: nil** no se admite.  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos &#40;XQuery&#41;](../xquery/type-system-xquery.md)  
  
  
