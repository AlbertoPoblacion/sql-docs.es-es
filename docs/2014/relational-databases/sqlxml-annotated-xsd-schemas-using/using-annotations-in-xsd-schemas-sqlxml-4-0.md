---
title: Utilizar anotaciones en esquemas XSD (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c62357496d0b143fcd8736bc61117d43c6a0fac
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2019
ms.locfileid: "66013596"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Utilizar anotaciones en esquemas XSD (SQLXML 4.0)
  En [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, el lenguaje de esquemas XSD admite las anotaciones de un modo similar a las introducidas en el lenguaje de esquemas reducidos de datos XML (XDR). Hay anotaciones adicionales introducidas en XSD que no se admiten en XDR.  
  
 Estas anotaciones se pueden utilizar dentro del esquema XSD para especificar la asignación de XML a relacional. Esto incluye la asignación entre los elementos y atributos del esquema XSD a las tablas (vistas) y columnas de las bases de datos.  
  
 Si no se especifican las anotaciones, se produce la asignación predeterminada. Un elemento XSD con un tipo complejo se asigna de forma predeterminada a un nombre de tabla (vista) de la base de datos especificada, mientras que un elemento o atributo con un tipo simple se asigna a la columna con el mismo nombre que el elemento o atributo.  
  
 Estas anotaciones también pueden utilizarse para especificar las relaciones jerárquicas en XML, lo que representan las relaciones de la base de datos, porque un esquema XSD es simplemente una vista XML de datos relacionales.  
  
 En esta sección se proporcionan descripciones de las anotaciones que puede usar con esquemas XSD y ejemplos de su uso.  
  
> [!NOTE]  
>  Todos los ejemplos de esta sección especifican consultas XPath simples en el esquema XSD agregado descrito en cada ejemplo. Se presupone el conocimiento del lenguaje XPath.  
  
## <a name="in-this-section"></a>En esta sección  
 [Las anotaciones XSD &#40;SQLXML 4.0&#41;](xsd-annotations-sqlxml-4-0.md)  
 Se enumeran las anotaciones que puede utilizar con esquemas XSD, sus descripciones y las anotaciones equivalentes para XDR.  
  
 [Asignación predeterminada de atributos y elementos XSD a tablas y columnas &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Explica la asignación predeterminada y proporciona ejemplos de tareas relacionados con la asignación predeterminada.  
  
 [Asignación explícita de elementos y atributos a las tablas y columnas XSD &#40;SQLXML 4.0&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Explica la asignación explícita con las anotaciones `sql:relation` y `sql:field` y proporciona ejemplos.  
  
 [Especificar relaciones mediante SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:relationship`.  
  
 [Especificar el atributo SQL: Inverse en SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Describe la anotación de `sql:inverse`.  
  
 [Crear elementos constantes mediante sql: constante es &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:is-constant`.  
  
 [Excluir elementos de esquema del documento XML resultante mediante sql: asigna &#40;SQLXML 4.0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Describe y proporciona ejemplos de la anotación `sql:mapped`.  
  
 [Filtrar valores mediante SQL: limit-campo y SQL: limit-valor &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Describe y proporciona ejemplos de las anotaciones `sql:limit-field` y `sql:limit-value`.  
  
 [Identificar columnas de clave mediante SQL: Key-campos &#40;SQLXML 4.0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:key-fields`.  
  
 [Especificar un destino Namespace mediante el atributo targetNamespace &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la **targetNamespace** atributo.  
  
 [Creación de un identificador válido, IDREF e IDREFS tipo atributos mediante SQL: prefix &#40;SQLXML 4.0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:prefix`.  
  
 [Conversiones de tipos de datos y la anotación SQL: DataType &#40;SQLXML 4.0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:datatype`.  
  
 [Asignar tipos de datos XSD a tipos de datos de XPath &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 Proporciona una tabla que compara XSD, XDR y tipos de datos XPath y enumera las conversiones [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pertinentes.  
  
 [Creación de secciones de CDATA mediante SQL: use-cdata &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:use-data`.  
  
 [Solicitar referencias URL a datos BLOB mediante sql: encode &#40;SQLXML 4.0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Describe y proporciona ejemplos de la anotación `sql:encode`.  
  
 [Recuperar datos no consumidos mediante Overflow-campo &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Describe y proporciona ejemplos de la anotación `sql:overflow-field`.  
  
 [Ocultar elementos y atributos mediante sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)  
 Describe y proporciona ejemplos de la anotación `sql:hide`.  
  
 [Utilizar las anotaciones sql:guid y sql:identity](using-the-sql-identity-and-sql-guid-annotations.md)  
 Describe y proporciona ejemplos de las anotaciones `sql:identity` y `sql:guid`.  
  
 [Especificar la profundidad en relaciones recursivas mediante sql:max-depth](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Describe y proporciona ejemplos de la anotación `sql:max-depth`.  
  
## <a name="see-also"></a>Vea también  
 [Anotar las consideraciones de seguridad de esquema &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
