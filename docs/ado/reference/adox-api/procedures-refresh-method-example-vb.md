---
title: Procedimientos de actualización de ejemplo del método (VB) | Microsoft Docs
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
- Refresh method [ADOX], Visual Basic example
ms.assetid: 499679bd-287b-487d-bdfb-3803abffec1c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f46bc9aceeec0e03329572814653a94ea64aa50
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62708802"
---
# <a name="procedures-refresh-method-example-vb"></a>Ejemplo de método Refresh de procedimientos (VB)
El código siguiente muestra cómo actualizar el [procedimientos](../../../ado/reference/adox-api/procedures-collection-adox.md) colección de un [catálogo](../../../ado/reference/adox-api/catalog-object-adox.md). Esto es necesario antes de [procedimiento](../../../ado/reference/adox-api/procedure-object-adox.md) objetos desde el **catálogo** se puede tener acceso.  
  
```  
' BeginProceduresRefreshVB  
Sub Main()  
    On Error GoTo ProcedureRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection  
    cat.Procedures.Refresh  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureRefreshError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndProceduresRefreshVB  
```  
  
## <a name="see-also"></a>Vea también  
 [Objeto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Colección de procedimientos (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Actualizar (método, ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
