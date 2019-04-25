---
title: Programación de SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, about SQL Server Native Client
- SQL Server Native Client, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
- data access [SQL Server Native Client]
- SQL Server Native Client
- SQLNCLI
- native data access [SQL Server Native Client]
ms.assetid: 14ba2cb1-a424-4e4d-b224-0bf1015ab801
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ef03fd5a9332e1c14a8c0eadf0730ccd5609c87
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62638202"
---
# <a name="sql-server-native-client-programming"></a>Programación de SQL Server Native Client
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client es una interfaz de programación de aplicaciones (API) de acceso a datos independiente que se introdujo en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y que se utiliza tanto para OLE DB como para ODBC. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client combina el proveedor OLE DB de SQL y el controlador ODBC de SQL en una biblioteca de vínculos dinámicos (DLL) nativa. También ofrece muchas más funciones nuevas de las que se proporcionaban en Data Access Components para Windows (DAC para Windows, anteriormente Microsoft Data Access Components o MDAC). Puede utilizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client para crear nuevas aplicaciones o mejorar las existentes incorporando las características introducidas en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], como la compatibilidad con conjuntos de resultados activos múltiples (MARS), los tipos de datos definidos por el usuario (UDT), las notificaciones de consulta, el aislamiento de instantánea y el tipo de datos XML.  
  
> [!NOTE]  
>  Para obtener una lista de las diferencias entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client y Windows DAC, además de información sobre los problemas a tener en cuenta antes de actualizar una aplicación de Windows DAC a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, vea [actualizar una aplicación a SQL Server Native Client desde MDAC](applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 El controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client siempre se utiliza junto con el administrador de controladores ODBC que se proporciona con DAC para Windows. El proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client puede utilizarse junto con los servicios principales de OLE DB que se proporcionan con DAC para Windows, pero no se trata de un requisito; la opción de usar o no los servicios principales depende de los requisitos de la aplicación individual (por ejemplo, si se requiere la agrupación de conexiones).  
  
 Las aplicaciones ADO (Objetos de datos ActiveX) pueden usar el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, pero es recomendable usar ADO junto con la palabra clave de cadena de conexión `DataTypeCompatibility` (o su propiedad `DataSource` correspondiente). Al utilizar el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, las aplicaciones ADO pueden aprovecharse de esas nuevas características introducidas en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] que se encuentran disponibles a través de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mediante las palabras clave de cadena de conexión o mediante las propiedades de OLE DB o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Para obtener más información sobre el uso de estas características con ADO, vea [utilizar ADO con SQL Server Native Client](applications/using-ado-with-sql-server-native-client.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client se diseñó para proporcionar un método simplificado de acceso a datos nativos de SQL Server mediante OLE DB u ODBC. Es un método simplificado en el sentido de que combina las tecnologías de OLE DB y ODBC en una sola biblioteca, y permite innovar y desarrollar nuevas características de acceso a datos sin modificar los componentes actuales de DAC para Windows, que ya forman parte de la plataforma Microsoft Windows.  
  
 Aunque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client usa los componentes de DAC para Windows, no depende explícitamente de ninguna versión en concreto de DAC para Windows. Puede usar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client con la versión de DAC para Windows que esté instalada en cualquier sistema operativo compatible con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="in-this-section"></a>En esta sección  
 [Novedades de SQL Server Native Client](sql-server-native-client.md)  
 Enumera las características nuevas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client más significativas.  
  
 [Cuándo debe utilizarse SQL Server Native Client](when-to-use-sql-server-native-client.md)  
 Describe la forma en que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client se ajusta a las tecnologías de acceso a datos de Microsoft, sus semejanzas y diferencias con DAC para Windows y ADO.NET y, además, proporciona punteros para decidir qué tecnología de acceso a datos se va a usar.  
  
 [Características de SQL Server Native Client](features/sql-server-native-client-features.md)  
 Describe las características compatibles con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Generar aplicaciones con SQL Server Native Client](applications/building-applications-with-sql-server-native-client.md)  
 Proporciona información general sobre el desarrollo de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, como las diferencias que existen con Windows DAC, los componentes que utiliza y la forma en que puede utilizarse con ADO.  
  
 En esta sección también se explica la instalación e implementación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, incluida la forma de redistribuir la biblioteca de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Requisitos del sistema para SQL Server Native Client](system-requirements-for-sql-server-native-client.md)  
 Describe el sistema de recursos necesario para usar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [SQL Server Native Client &#40;OLE DB&#41;](ole-db/sql-server-native-client-ole-db.md)  
 Proporciona información sobre la forma de usar el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [SQL Server Native Client &#40;ODBC&#41;](odbc/sql-server-native-client-odbc.md)  
 Proporciona información sobre la forma de usar el controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 [Más información sobre SQL Server Native Client](finding-more-sql-server-native-client-information.md)  
 Proporciona recursos adicionales sobre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, incluidos vínculos a recursos externos y obtención de más ayuda.  
  
 [Errores de SQL Server Native Client](../native-client-ole-db-errors/errors.md)  
 Contiene temas sobre errores en tiempo de ejecución asociados a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Vea también  
 [Actualizar una aplicación desde SQL Server 2005 Native Client](applications/updating-an-application-from-sql-server-2005-native-client.md)   
 [Temas de procedimientos de ODBC](../native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Temas de procedimientos de OLE DB](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
