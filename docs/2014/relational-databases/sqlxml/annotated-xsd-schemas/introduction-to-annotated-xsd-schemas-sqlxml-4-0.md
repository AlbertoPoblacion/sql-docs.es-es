---
title: Introducción a los esquemas XSD anotados (SQLXML 4.0) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8813d34f2c669e9646b899230388fca649e4488
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2019
ms.locfileid: "66014456"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Introducción a los esquemas XSD anotados (SQLXML 4.0)
  Puede crear vistas XML de datos relacionales utilizando el lenguaje de definición de esquemas XML (XSD). Estas vistas pueden consultarse después utilizando consultas XPath (Lenguaje de rutas XML). Es parecido a crear vistas utilizando instrucciones CREATE VIEW y, a continuación, especificar consultas SQL en la vista.  
  
 Un esquema XML describe la estructura de un documento XML y también describe las diversas restricciones en los datos en el documento. Cuando se especifican consultas XPath en el esquema, la estructura del documento XML devuelto viene determinada por el esquema en el que se ejecuta la consulta XPath.  
  
 En un esquema XSD, el  **\<xsd: schema >** elemento abarca todo el esquema; todas las declaraciones de elemento deben estar dentro del  **\<xsd: schema >** elemento. Puede describir los atributos que definen el espacio de nombres en el que reside el esquema y los espacios de nombres que se usan en el esquema como propiedades de la  **\<xsd: schema >** elemento.  
  
 Un esquema XSD válido debe contener el  **\<xsd: schema >** elemento que se define como sigue:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 El  **\<xsd: schema >** elemento se deriva de la especificación de espacio de nombres del esquema XML en http://www.w3.org/2001/XMLSchema.  
  
## <a name="annotations-to-the-xsd-schema"></a>Anotaciones en el esquema XSD  
 Puede usar un esquema XSD con anotaciones que describan la asignación a una base de datos, consultar la base de datos y devolver los resultados en forma de documento XML. Las anotaciones se proporcionan para asignar un esquema XSD a las tablas y columnas de base de datos. Pueden especificarse consultas XPath en la vista XML creada por el esquema XSD para consultar la base de datos y obtener los resultados en un documento XML.  
  
> [!NOTE]  
>  En [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, el lenguaje de esquemas XSD admite las anotaciones introducidas por el lenguaje de esquemas reducidos de datos XML (XDR) anotados de [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]. Los esquemas XDR anotados han quedado desusados en SQLXML 4.0.  
  
 En el contexto de la base de datos relacional, resulta de gran utilidad para asignar el esquema XSD arbitrario a un almacén relacional. Una forma de conseguirlo es anotar el esquema XSD. Un esquema XSD con anotaciones se conoce como un *esquema de asignación*, que proporciona información relativa al modo datos XML que debe asignarse al almacén relacional. Un esquema de asignación es realmente una vista XML de los datos relacionales. Estas asignaciones pueden usarse para recuperar los datos relacionales como un documento XML.  
  
## <a name="namespace-for-annotations"></a>Espacio de nombres para las anotaciones  
 En un esquema XSD, las anotaciones se especifican mediante el espacio de nombres **urn: schemas-microsoft-mapping-schema**. Como se muestra en el ejemplo siguiente, la manera más fácil para especificar el espacio de nombres es especificarlo en el  **\<xsd: schema >** etiqueta.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Se utiliza un prefijo de espacio de nombres arbitrario. En esta documentación, el **sql** prefijo se utiliza para denotar el espacio de nombres de anotación y para distinguir las anotaciones de este espacio de nombres de las de otros espacios de nombres.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Ejemplo de un esquema XSD anotado  
 En el ejemplo siguiente, el esquema XSD consta de un  **\<Person.Contact >** elemento. El  **\<empleado >** elemento tiene un **ContactID** atributo y  **\<FirstName >** y  **\< LastName >** elementos secundarios:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Se han agregado anotaciones a este esquema XSD para asignar sus elementos y atributos a las tablas y columnas de base de datos:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 En el esquema de asignación, el  **\<contacto >** elemento se asigna a la tabla Person.Contact de la base de datos de ejemplo AdventureWorks mediante el uso de la `sql:relation` anotación. Los atributos ConID, FName y LName se asignan a las columnas ContactID, FirstName y LastName de la tabla Person.Contact mediante las anotaciones `sql:field`.  
  
 Este esquema XSD anotado proporciona la vista XML de los datos relacionales. Esta vista XML puede consultarse utilizando el lenguaje XPath. Una consulta XPath devuelve como resultado un documento XML en lugar del conjunto de filas que devuelven las consultas SQL.  
  
> [!NOTE]  
>  En el esquema de asignación, la distinción de mayúsculas y minúsculas para los valores relacionales especificados (como el nombre de tabla y el nombre de columna) depende de que SQL Server utilice la configuración de intercalación con distinción de mayúsculas y minúsculas. Para más información, consulte [Compatibilidad con la intercalación y Unicode](../../collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Otros recursos  
 Puede buscar más información sobre el lenguaje de definición de esquemas XML (XSD), el lenguaje de rutas XML (XPath) y el lenguaje de transformación basado en hojas de estilo (XSLT) en los siguientes sitios web:  
  
-   XML Schema Part 0: Manual, W3C recomendación (http://www.w3.org/TR/xmlschema-0/)  
  
-   Esquema XML parte 1: Estructuras, W3C recomendación (http://www.w3.org/TR/xmlschema-1/)  
  
-   Esquema XML parte 2:Datatypes, W3C recomendación (http://www.w3.org/TR/xmlschema-2/)  
  
-   XML Path Language (XPath) (http://www.w3.org/TR/xpath)  
  
-   (XSL Transformations (XSLT) (http://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>Vea también  
 [Anotar las consideraciones de seguridad de esquema &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Esquemas XDR anotados &#40;en desuso en SQLXML 4.0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
