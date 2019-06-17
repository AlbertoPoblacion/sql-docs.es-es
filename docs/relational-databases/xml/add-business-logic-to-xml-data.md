---
title: Agregar lógica comercial a los datos XML | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bd30df2ef65fcbdfa2118321b5e7c723b56316e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63034832"
---
# <a name="add-business-logic-to-xml-data"></a>Agregar lógica comercial a los datos XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La lógica de negocios se puede agregar a los datos XML de varias formas:  
  
-   Se pueden escribir restricciones de filas o columnas para forzar restricciones específicas de un dominio durante la inserción y modificación de datos XML.  
  
-   Es posible escribir un desencadenador en la columna XML que se active al insertar o actualizar valores en la columna. El desencadenador puede contener reglas de validación específicas de un dominio o rellenar tablas de propiedades.  
  
-   El motor de base de datos incluye la capacidad de ejecutar código administrado. Puede usar esta integración de Common Language Runtime (CLR) para escribir funciones en código administrado a las que pasar valores XML y usar capacidades de procesamiento XML proporcionadas por el espacio de nombres System.Xml. Un ejemplo es aplicar la transformación XSL a datos XML. Otra posibilidad es deserializar el XML en una o más clases administradas y operar con ellas mediante código administrado.  
  
-   Se pueden escribir procedimientos almacenados de Transact-SQL y funciones que inicien el procesamiento en la columna XML de acuerdo con las necesidades de la empresa.  
  
## <a name="example-applying-xsl-transformation"></a>Ejemplo: Aplicación de una transformación XSL  
 Considere una función CLR **TransformXml()** que acepta una instancia de tipo de datos **xml** y una transformación XSL almacenada en un archivo, aplica la transformación a los datos XML y, después, devuelve el XML transformado en el resultado. A continuación, se muestra una función esquemática escrita en C#:  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 Después de registrar el ensamblado y crear una función [!INCLUDE[tsql](../../includes/tsql-md.md)] definida por el usuario, **SqlXslTransform()** correspondiente a **TransformXml()** , se puede invocar la función desde Transact-SQL como se indica en la consulta siguiente:  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 El resultado de la consulta contiene un conjunto de filas del XML transformado.  
  
 La integración de CLR en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] amplía las posibilidades de descomponer datos XML en tablas o promoción de propiedades, y de consulta de datos XML usando clases administradas en el espacio de nombres System.Xml. Para obtener más información, vea [Datos XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md).  
  
  
