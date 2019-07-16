---
title: Guardar y abrir un ejemplo de los métodos (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6d42488f8f167cc7c98f663478c742963d24253c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931193"
---
# <a name="save-and-open-methods-example-vb"></a>Ejemplo de los métodos Save y Open (VB)
Estos tres ejemplos se muestra cómo el [guardar](../../../ado/reference/ado-api/save-method.md) y [abierto](../../../ado/reference/ado-api/open-method-ado-recordset.md) métodos pueden usarse conjuntamente.  
  
 Supongamos que se va de un viaje de negocios y desea tomar a lo largo de una tabla de una base de datos. Antes de ir, tener acceso a los datos como un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) y guárdelo en un formato transportable. Cuando llegue a su destino, tener acceso a la **Recordset** como un valor local desconectado **Recordset**. Realizar cambios en el **Recordset**y, a continuación, vuelva a guardar. Por último, al volver a casa, volver a conectar con la base de datos y actualizarla con los cambios realizados en la carretera.  
  
 En primer lugar, obtenga acceso y guarde el ***autores*** tabla.  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 En este momento, ha llegado a su destino. Tendrá acceso a la ***autores*** tabla como un valor local desconectado **Recordset**. Debe tener la **MSPersist** proveedor en el equipo que está usando para tener acceso al archivo guardado, a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Por último, volver a casa. Ahora puede actualizar la base de datos con los cambios.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>Vea también  
 [Método Open (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Más información acerca de la persistencia de conjunto de registros](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Save (método)](../../../ado/reference/ado-api/save-method.md)
