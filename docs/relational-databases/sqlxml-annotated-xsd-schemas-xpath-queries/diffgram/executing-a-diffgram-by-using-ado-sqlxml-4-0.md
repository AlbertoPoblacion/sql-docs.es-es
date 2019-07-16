---
title: Ejecutar un DiffGram mediante ADO (SQLXML 4.0) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 764ba5c11e6ec4b41017e9839c46c0e8f4c8d70a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073474"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a>Ejecutar un DiffGram utilizando ADO (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Esta aplicación de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic utiliza ADO para establecer una conexión a una instancia de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y después ejecuta un DiffGram. En esta aplicación, el DiffGram y el esquema XSD están almacenados en un archivo. La aplicación carga el DiffGram del archivo especificado. Puede usar cualquiera de los DiffGrams (y el esquema XSD asociado) se describe en [ejemplos de DiffGram](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
 Éste es el proceso de la aplicación de ejemplo:  
  
-   El **conn** objeto (**ADODB. Conexión**) establece una conexión a una instancia de ejecución de SQL Server en un servidor específico.  
  
-   El **cmd** objeto (**ADODB.Command**) se ejecuta en la conexión establecida.  
  
-   El lenguaje de comandos está establecido en DBGUID_MSSQLXML.  
  
-   El DiffGram se copia en la secuencia de comandos (**strmIn**) desde un archivo.  
  
-   Flujo de salida del comando se establece en el **StrmOut** objeto (**ADODB. Stream**) a reciba cualquiera de los datos devueltos.  
  
-   Si está utilizando el proveedor SQLOLEDB, obtendrá de forma predeterminada la funcionalidad de Microsoft SQLXML que proporciona Sqlxmlx.dll. Para utilizar Sqlxml4.dll con el proveedor SQLOLEDB, el **SQLXML Version** propiedad debe establecerse en **SQLXML.4.0** en el proveedor SQLOLEDB **conexión** objeto.  
  
-   Se ejecuta el comando (DiffGram).  
  
 El siguiente código es la aplicación de ejemplo.  
  
> [!NOTE]  
>  En el código, debe suministrarse el nombre de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en la cadena de conexión.  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a>Para probar el DiffGram:  
  
1.  En una carpeta en el equipo, copie cualquiera de los DiffGrams y el esquema XSD correspondiente de uno de los ejemplos de [ejemplos de DiffGram](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
2.  Abra Visual Basic y cree un proyecto EXE estándar.  
  
3.  Agregue estas referencias al proyecto:  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  En el cuadro de herramientas, haga clic en **CommandButton**y, a continuación, dibuje un botón en el formulario.  
  
5.  Haga doble clic en el botón para modificar el código y agregue el código de aplicación que se proporciona en el tema.  
  
6.  Modifique el código para especificar el DiffGram y los nombres de archivos XSD. Modifique también la cadena de conexión según corresponda.  
  
7.  Ejecute la aplicación. El resultado de la ejecución depende del DiffGram que esté ejecutando.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

