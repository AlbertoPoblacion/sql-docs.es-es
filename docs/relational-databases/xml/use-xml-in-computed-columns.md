---
title: Usar XML en columnas calculadas | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb0cca121576000f3f7c5ba42eb4161c7d38f207
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2018
---
# <a name="use-xml-in-computed-columns"></a>Usar XML en columnas calculadas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Pueden aparecer instancias XML como origen de una columna calculada o como un tipo de columna calculada. Los ejemplos de este tema muestran cómo usar XML con columnas calculadas.  
  
## <a name="creating-computed-columns-from-xml-columns"></a>Crear columnas calculadas a partir de columnas XML  
 En la siguiente instrucción `CREATE TABLE` , una columna de tipo `xml` (`col2`) se calcula a partir de `col1`:  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 El tipo de datos `xml` también puede aparecer como origen en la creación de una columna calculada, tal como se muestra en la siguiente instrucción `CREATE TABLE` :  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 Puede crear una columna calculada extrayendo un valor de una columna de tipo `xml` , como se muestra en el ejemplo siguiente. Puesto que los métodos de tipo de datos **xml** no se pueden usar directamente en la creación de columnas calculadas, en el ejemplo se define en primer lugar una función (`my_udf`) que devuelve un valor de una instancia XML. La función ajusta el método `value()` del tipo `xml` . A continuación se especifica el nombre de la función en la instrucción `CREATE TABLE` para la columna calculada.  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 Al igual que en el ejemplo anterior, en el siguiente se define una función para devolver una instancia de tipo **xml** para una columna calculada. En la función, el método `query()` del tipo de datos `xml` recupera un valor de un parámetro de tipo `xml` .  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 En la siguiente instrucción `CREATE TABLE` , `Col2` es una columna calculada que usa los datos XML (elemento`<Features>` ) devueltos por la función:  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[Promover los valores XML usados con frecuencia con columnas calculadas](../../relational-databases/xml/promote-frequently-used-xml-values-with-computed-columns.md)|Describe cómo usar la promoción de propiedades con columnas calculadas y tablas de propiedades.|  
  
  
