---
title: Ver una colección de esquemas XML almacenada | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e62fd82b302576dfbaf45cbb8073c2e94f7a67e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "68096972"
---
# <a name="view-a-stored-xml-schema-collection"></a>Ver una colección de esquemas XML almacenada
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Después de importar una colección de esquemas XML mediante [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md), los componentes del esquema se almacenan en los metadatos. Puede usar la función intrínseca [xml_schema_namespace](../../t-sql/xml/xml-schema-namespace.md)para reconstruir la colección de esquemas XML. La función devuelve una instancia de tipo de datos **xml** .  
  
 Por ejemplo, la siguiente consulta recupera una colección de esquemas XML (`ProductDescriptionSchemaCollection`) del esquema relacional de producción de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 Si solo quiere ver un esquema de la colección de esquemas XML, puede especificar XQuery en el resultado de tipo **xml** devuelto por `xml_schema_namespace`.  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 La siguiente consulta, por ejemplo, recupera información de garantía del producto y de mantenimiento del esquema XML a partir de la colección de esquemas XML `ProductDescriptionSchemaCollection` .  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 También puede pasar el espacio de nombres de destino opcional como tercer parámetro a la función `xml_schema_namespace` con el fin de recuperar un esquema específico de la colección, tal y como muestra la consulta siguiente:  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 Al crear una colección de esquemas XML mediante CREATE XML SCHEMA COLLECTION en la base de datos, la instrucción almacena los componentes de esquema en los metadatos. Observe que solo se almacenarán aquellos componentes de esquema que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pueda interpretar. No se almacenarán comentarios, anotaciones ni atributos que no sean XSD. Por tanto, el esquema reconstruido por **xml_schema_namespace** será funcionalmente equivalente al esquema original, pero no tendrá necesariamente la misma apariencia. Por ejemplo, no se observarán los mismos prefijos del esquema original. El esquema devuelto por **xml_schema_namespace** usa **t** como el prefijo para el espacio de nombres de destino y **ns1**, **ns2**, etc., para otros espacios de nombres.  
  
 Si desea conservar una copia idéntica de los esquemas XML, debería guardarlos en un archivo o en una tabla de base de datos en una columna de tipo **xml** .  
  
 La vista de catálogo [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) también devuelve información sobre las colecciones de esquemas XML. La información consiste en el nombre la colección, la fecha de creación y el nombre del propietario.  
  
## <a name="see-also"></a>Consulte también  
 [Colecciones de esquemas XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
