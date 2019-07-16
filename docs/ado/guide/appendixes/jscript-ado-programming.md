---
title: Programación ADO con JScript | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d07759405dc337667cc8971ce7795af428a0cfa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926803"
---
# <a name="jscript-ado-programming"></a>Programación ADO con JScript
## <a name="creating-an-ado-project"></a>Crear un proyecto de ADO  
 Microsoft JScript no admite las bibliotecas de tipos, por lo que no es necesario hacer referencia a ADO en el proyecto. Por lo tanto, se admite ninguna característica asociada como la finalización de la línea de comandos. Además, de forma predeterminada, no se definen las constantes enumeradas de ADO en JScript.  
  
 Sin embargo, ADO ofrece que dos incluyen los archivos que contienen las siguientes definiciones para usarse con JScript:  
  
-   Uso de scripting del lado servidor Adojavas.inc, que se instala en las carpetas de la biblioteca ADO.  
  
-   Uso de scripting del lado cliente Adcjavas.inc, que se instala en las carpetas de la biblioteca ADO.  
  
 Puede copiar y pegar las definiciones de constantes de estos archivos en las páginas ASP o, si va a realizar el scripting del lado servidor, copie el archivo Adojavas.inc en una carpeta en el sitio Web y hace referencia a él desde la página ASP similar al siguiente:  
  
```javascript
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Creación de objetos ADO en JScript  
 En su lugar, debe usar el **CreateObject** llamada de función:  
  
```javascript
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>Ejemplo de JScript  
 El código siguiente es un ejemplo genérico de programación de JScript en el servidor en un archivo de páginas Active Server (ASP) que se abre un **Recordset** objeto:  
  
```javascript
<%  @LANGUAGE="JScript" %>  
<!--#include File="adojavas.inc"-->  
<HTML>  
<BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
<%  
var Source = "SELECT * FROM Authors";  
var Connect =  "Provider=sqloledb;Data Source=srv;" +  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );  
Rs1.Open(Source,Connect,adOpenForwardOnly);  
Response.Write("Success!");  
%>  
</BODY>  
</HTML>  
```
