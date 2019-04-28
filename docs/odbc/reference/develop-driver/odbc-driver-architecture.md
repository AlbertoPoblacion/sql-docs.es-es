---
title: Arquitectura de controladores ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 260767c88fdf980466a21d4cc9658b259b91c854
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690651"
---
# <a name="odbc-driver-architecture"></a>Arquitectura de controladores ODBC
Los escritores de controlador deben tener en cuenta que puede afectar la arquitectura de controladores si una aplicación puede usar SQL específicos para DBMS.  
  
 ![Muestra la arquitectura de controladores ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Controladores basados en archivos](../../../odbc/reference/file-based-drivers.md)  
  
 Cuando el controlador tiene acceso directo a los datos físicos, el controlador actúa como origen de datos y de controlador. El controlador debe procesar llamadas ODBC e instrucciones SQL. Los desarrolladores de controladores basados en archivos deben escribir sus propios motores de base de datos.  
  
 [Controladores basados en DBMS](../../../odbc/reference/dbms-based-drivers.md)  
  
 Cuando se usa un motor de base de datos independiente para tener acceso a datos físicos, el controlador procesa solo las llamadas ODBC. Instrucciones SQL pasa al motor de base de datos para procesar.  
  
 [Arquitectura de red](../../../odbc/reference/network-example.md)  
  
 Las configuraciones de archivo y DBMS ODBC pueden existir en una sola red.  
  
 [Otras arquitecturas de controlador](../../../odbc/reference/other-driver-architectures.md)  
  
 Cuando se requiere un controlador para que funcione con una variedad de orígenes de datos, se puede usar como middleware. Arquitectura del motor de combinación heterogéneo puede hacer que el controlador aparezca como un administrador de controladores. Los controladores también pueden instalarse en servidores, donde puede compartirse por una serie de clientes.  
  
 Para obtener más información acerca de la arquitectura de controladores, consulte [Administrador de controladores](../../../odbc/reference/the-driver-manager.md) y [arquitectura de controladores](../../../odbc/reference/driver-architecture.md) en la sección sobre [arquitectura ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Para obtener más información acerca de problemas de controladores se puede encontrar en las ubicaciones descritas en la tabla siguiente.  
  
|Problema|Tema|Location|  
|-----------|-----------|--------------|  
|Problemas de compatibilidad con aplicaciones y controladores|[Compatibilidad de aplicaciones y controladores](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Consideraciones sobre la programación](../../../odbc/reference/develop-app/programming-considerations.md), en la referencia del programador de ODBC|  
|Controladores ODBC de escritura|[Controladores ODBC 3.x de escritura](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Consideraciones sobre la programación](../../../odbc/reference/develop-app/programming-considerations.md), en la referencia del programador de ODBC|  
|Directrices de controlador para la compatibilidad con versiones anteriores|[Directrices de controlador para la compatibilidad con versiones anteriores](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Apéndice G: Directrices de controlador para la compatibilidad con versiones anteriores](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), en la referencia del programador de ODBC|  
|Conectarse a un controlador|[Elegir datos de un origen o el controlador](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Conectarse a datos de un origen o el controlador](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), en la referencia del programador de ODBC|  
|Identificación de controladores|[Visualización de controladores](../../../odbc/admin/viewing-drivers.md)|[Visualización de controladores](../../../odbc/admin/viewing-drivers.md), en la Ayuda en pantalla de administrador de orígenes de datos ODBC de Microsoft|  
|Habilitar la agrupación de conexiones|[Agrupación de conexiones ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Conectarse a datos de un origen o el controlador](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), en la referencia del programador de ODBC|  
|Problemas de conexión y controladores de Unicode/ANSI|[Controladores de Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)|[Consideraciones sobre la programación](../../../odbc/reference/develop-app/programming-considerations.md), en la referencia del programador de ODBC|  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un controlador ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
