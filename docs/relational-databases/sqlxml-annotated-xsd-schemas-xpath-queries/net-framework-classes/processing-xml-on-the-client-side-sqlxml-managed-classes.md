---
title: Procesar XML en el lado cliente (clases administradas de SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d6133cbedb01dce5cb4d868e79e52e236e773f4b
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909168"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>Procesar XML en el cliente (clases administradas de SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  En este ejemplo se muestra el uso de la propiedad Clientsidexml,. La aplicación ejecuta un procedimiento almacenado en el servidor. El resultado del procedimiento almacenado (un conjunto de filas de dos columnas) se procesa en el cliente para generar un documento XML.  
  
 El siguiente procedimiento almacenado GetContacts devuelve el **nombre** y el **Apellido** de los empleados de la tabla person. contact de la base de datos AdventureWorks.  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 Esta C# aplicación ejecuta el procedimiento almacenado y especifica la opción for XML auto en la especificación del valor CommandText. En la aplicación, la propiedad Clientsidexml, del objeto SqlXmlCommand se establece en true. Esto le permite ejecutar procedimientos almacenados preexistentes que devuelven un conjunto de filas y aplican a este último una transformación XML en el cliente.  
  
> [!NOTE]  
>  En el código, debe proporcionar el nombre de la instancia de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en la cadena de conexión.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
 Para probar este ejemplo, debe tener instalado [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework en el equipo.  
  
### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  Cree el procedimiento almacenado.  
  
2.  Guarde el código (DocSample.cs) de C# que se proporciona en este ejemplo en una carpeta. Modifique el código para especificar la información adecuada de inicio de sesión y contraseña.  
  
3.  Compile el código. Para compilar el código en el símbolo del sistema, use:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Esto crea una aplicación ejecutable (DocSample.exe).  
  
4.  En el símbolo del sistema, ejecute DocSample.exe.  

