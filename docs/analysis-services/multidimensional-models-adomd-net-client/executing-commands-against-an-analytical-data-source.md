---
title: "Ejecutar comandos en un origen de datos analíticos | Documentos de Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 23c14b71b321ee8358d542bd10f8b6cb73ee9a9f
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Ejecutar comandos en un origen de datos analíticos
  Después de establecer una conexión a un origen de datos analíticos, puede usar un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> para ejecutar con comandos y resultados devueltos de ese origen de datos. Estos comandos pueden recuperar datos mediante expresiones multidimensionales (MDX), extensiones de minería de datos (DMX), o incluso una sintaxis limitada de SQL. Además, puede usar los comandos ASSL (Analysis Services Scripting Language) para modificar la base de datos subyacente.  
  
## <a name="creating-a-command"></a>Crear un comando  
 Antes de ejecutar un comando, debe crearlo. Puede crear un comando mediante uno de los dos métodos siguientes:  
  
-   El primer método usa el constructor <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, que puede tomar un comando para ejecutarlo en el origen de datos y un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> para ejecutar el comando.  
  
-   El segundo método usa el método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 El texto del comando para ejecutar se puede consultar y modificar mediante la propiedad <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. Los comandos que crea no tienen que devolver los datos después de ejecutarse.  
  
## <a name="running-a-command"></a>Ejecutar un comando  
 Después de crear un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, hay varios métodos <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> que el comando puede usar para realizar varias acciones. En la tabla siguiente se enumeran algunas de estas acciones.  
  
|A|Use este método|  
|--------|---------------------|  
|Devolver resultados como un flujo de datos|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> para devolver un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Devolver un objeto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Ejecutar comandos que no devuelven filas|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Devolver un **XMLReader** objeto que contiene los datos de XML for formato compatible con Analysis (XMLA)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Ejemplo de cómo ejecutar un comando  
 Este ejemplo se utiliza la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> para ejecutar un comando XMLA que procesará el **Adventure Works DW** cubo en el servidor local, sin devolver los datos.  
  
 [!code-cs[Adomd.NetClient#ExecuteXMLAProcessCommand](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/executing-commands-again_1.cs)]  
  
  
