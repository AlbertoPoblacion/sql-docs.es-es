---
title: Usar consultas FOR XML anidadas en ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], ASP.NET and
- nested FOR XML queries in ASP.NET
- ASP.NET [SQL Server]
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c726ca33df6b0cd9f79e336c7b056062a578236d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233667"
---
# <a name="use-nested-for-xml-queries-in-aspnet"></a>Usar consultas FOR XML anidadas en ASP.NET
  En este ejemplo, una aplicación ASP.NET devuelve XML a un explorador ejecutando un procedimiento almacenado en SQL Server. El procedimiento almacenado genera XML mediante consultas anidadas. Se muestra una instrucción SELECT similar en el tema [Generar elementos del mismo nivel con una consulta en modo AUTO anidada](generate-siblings-with-a-nested-auto-mode-query.md). Este ejemplo muestra una manera de usar consultas FOR XML anidadas para generar XML centrado en elementos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Ejemplo  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 Ésta es la aplicación .aspx. Ejecuta el procedimiento almacenado y devuelve el XML en el explorador:  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  Cree el procedimiento almacenado en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
2.  Guarde la aplicación .aspx en el directorio c:\inetpub\wwwroot (GetSalesOrderInfo.aspx).  
  
3.  Ejecute la aplicación (http://server/GetSalesOrderInfo.aspx).  
  
## <a name="see-also"></a>Vea también  
 [Usar consultas FOR XML anidadas](use-nested-for-xml-queries.md)  
  
  
