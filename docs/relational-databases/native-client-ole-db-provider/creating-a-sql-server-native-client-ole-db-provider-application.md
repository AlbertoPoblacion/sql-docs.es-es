---
title: "Crear una aplicación de proveedor SQL Server Native Client OLE DB | Documentos de Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-provider
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 68fb2398633deb91e596e46170e87606345ca236
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Crear una aplicación de proveedor OLE DB de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Crear un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aplicación del proveedor OLE DB de Native Client incluye los siguientes pasos:  
  
1.  Establecer una conexión con un origen de datos.  
  
2.  Ejecutar un comando.  
  
3.  Procesar los resultados.  
  
> [!NOTE]  
>  Siempre que sea posible, utilice la autenticación de Windows. Si la autenticación de Windows no está disponible, solicite a los usuarios que escriban sus credenciales en tiempo de ejecución. No guarde las credenciales en un archivo. Si debe conservar las credenciales, debería cifrarlas con [cryptoAPI de Win32](http://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Establecer una conexión con un origen de datos](../../relational-databases/native-client-ole-db-provider/establishing-a-connection-to-a-data-source.md)  
  
-   [Ejecutar un comando](../../relational-databases/native-client-ole-db-provider/executing-a-command.md)  
  
-   [Procesar resultados](../../relational-databases/native-client-ole-db-provider/processing-results.md)  
  
-   [Acerca de las propiedades OLE DB](../../relational-databases/native-client-ole-db-provider/about-ole-db-properties.md)  
  
-   [Usar la cláusula OUTPUT con OLE DB de SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Vea también  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
