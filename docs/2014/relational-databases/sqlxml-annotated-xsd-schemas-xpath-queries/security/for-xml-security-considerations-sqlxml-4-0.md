---
title: Consideraciones de seguridad de FOR XML (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6ee2ac48e03d7436f2671faa8f4883b10210a380
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717618"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a>Consideraciones de seguridad de FOR XML (SQLXML 4.0)
  El modo AUTO de FOR XML genera una jerarquía XML en la que los nombres de elemento se asignan a nombres de tabla y los nombres de atributos se asignan a nombres de columna. Esto expone la información de las tablas y columnas de la base de datos. Puede ocultar la información de la base de datos con el modo AUTO (formato aplicado en el servidor) especificando alias de tabla y columna en la consulta. Estos alias se devuelven en el documento XML resultante como nombres de elemento y atributo.  
  
 Por ejemplo, la consulta siguiente especifica el modo AUTO; por tanto, la aplicación de formato XML se realiza en el servidor:  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 En el documento XML resultante, los alias se utilizan para los nombres de elemento y atributo:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 Al utilizar el modo NESTED (formato aplicado del lado cliente), los alias solo se devuelven para los atributos en el documento XML resultante. Los nombres de las tablas base siempre se devuelven como nombres de elemento. Por ejemplo, la consulta siguiente especifica el modo NESTED.  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 En el documento XML resultante, los nombres de las tablas base se devuelven como nombres de elemento y no se utilizan alias de tabla:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
