---
title: Secuencias y persistencia | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisted streams [ADO]
- streams [ADO], persistence
ms.assetid: ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 246d894ff38cc0dd74e96bb0fcbdb7b170b51d53
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700492"
---
# <a name="streams-and-persistence"></a>Secuencias y persistencia
El [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto [guardar](../../../ado/reference/ado-api/save-method.md) método almacenes, o *continúa*, un **Recordset** en un archivo y el [abrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)método restaura el **Recordset** desde ese archivo.  
  
 Con ADO 2.7 o posterior, el **guardar** y **abierto** métodos pueden conservar un **Recordset** a un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objeto también. Esta característica es especialmente útil al trabajar con el servicio de datos remoto (RDS) y páginas Active Server (ASP).  
  
 Para obtener más información sobre cómo se puede usar persistencia por sí mismo en las páginas ASP, consulte la documentación de ASP.  
  
 Los siguientes son algunos escenarios que muestran cómo **Stream** objetos y persistencia se pueden usar.  
  
## <a name="scenario-1"></a>Escenario 1  
 Este escenario simplemente se guarda un **Recordset** a un archivo y, a continuación, en un **Stream**. A continuación, abre el flujo almacenado en otro **Recordset**.  
  
```  
Dim rs1 As ADODB.Recordset  
Dim rs2 As ADODB.Recordset  
Dim stm As ADODB.Stream  
  
Set rs1 = New ADODB.Recordset  
Set rs2 = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
rs1.Open   "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;""", adopenStatic, adLockReadOnly, adCmdText  
rs1.Save "c:\myfolder\mysubfolder\myrs.xml", adPersistXML  
rs1.Save stm, adPersistXML  
rs2.Open stm  
```  
  
## <a name="scenario-2"></a>Escenario 2  
 Este escenario se persiste un **Recordset** en un **Stream** en formato XML. A continuación, lee el **Stream** en una cadena que puede examinar, manipular o mostrar.  
  
```  
Dim rs As ADODB.Recordset  
Dim stm As ADODB.Stream  
Dim strRst As String  
  
Set rs = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
' Open, save, and close the recordset.   
rs.Open "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
rs.Save stm, adPersistXML  
rs.Close  
Set rs = nothing  
  
' Put saved Recordset into a string variable.  
strRst = stm.ReadText(adReadAll)  
  
' Examine, manipulate, or display the XML data.  
...  
```  
  
## <a name="scenario-3"></a>Escenario 3  
 Este código de ejemplo muestra código ASP conservar un **Recordset** como XML directamente a la **respuesta** objeto:  
  
```  
...  
<%  
response.ContentType = "text/xml"  
  
' Create and open a Recordset.  
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select * from Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
  
' Save Recordset directly into output stream.  
rs.Save Response, adPersistXML   
  
' Close Recordset.  
rs.Close  
Set rs = nothing  
%>  
...  
```  
  
## <a name="scenario-4"></a>Escenario 4  
 En este escenario, el código ASP escribe el contenido de la **Recordset** en formato ADTG al cliente. El [servicio de cursores de Microsoft para OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) puede usar estos datos para crear un desconectado **Recordset**.  
  
 Una nueva propiedad en el RDS [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md), [URL](../../../ado/reference/rds-api/url-property-rds.md), apunta a la página .asp que genera el **Recordset**. Esto significa un **Recordset** objeto puede obtenerse sin RDS con el servidor [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objeto o el usuario escribe un objeto comercial. Esto simplifica significativamente el modelo de programación de RDS.  
  
 Lado servidor, nombre de código https://server/directory/recordset.asp:  
  
```  
<%  
Dim rs   
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select au_fname, au_lname, phone from Authors", ""& _  
        "Provider=sqloledb;Data Source=MyServer;" & _  
        "Initial Catalog=Pubs;Integrated Security=SSPI;"  
response.ContentType = "multipart/mixed"  
rs.Save response, adPersistADTG  
%>  
```  
  
 Código de cliente:  
  
```  
<HTML>  
<HEAD>  
<TITLE>RDS Query Page</TITLE>  
</HEAD>  
<body>  
<CENTER>  
<H1>Remote Data Service 2.5</H1>  
<TABLE DATASRC="#DC1">  
   <TR>   
      <TD><SPAN DATAFLD="au_fname"></SPAN></TD>  
      <TD><SPAN DATAFLD="au_lname"></SPAN></TD>  
      <TD><SPAN DATAFLD="phone"></SPAN></TD>  
   </TR>  
</TABLE>  
<BR>  
  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
    ID=DC1 HEIGHT=1 WIDTH = 1>  
    <PARAM NAME="URL" VALUE="https://server/directory/recordset.asp">  
</OBJECT>  
  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 Los desarrolladores también tienen la opción de usar un **Recordset** objeto en el cliente:  
  
```  
...  
function GetRs()   
    {  
    rs = CreateObject("ADODB.Recordset");  
    rs.Open "https://server/directory/recordset.asp"  
    DC1.SourceRecordset = rs;  
    }  
...  
```  
  
## <a name="see-also"></a>Vea también  
 [Método Open (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Objeto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Save (método)](../../../ado/reference/ado-api/save-method.md)
