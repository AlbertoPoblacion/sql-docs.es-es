---
title: Controlar metadatos con el controlador JDBC | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d9eb1d31f0dcba8b17849a8f2b897420e1627cd4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Controlar metadatos con el controlador JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  El [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] puede utilizarse para trabajar con metadatos en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos en una variedad de formas. El controlador JDBC se puede usar para obtener metadatos sobre la base de datos, un conjunto de resultados o los parámetros.  
  
 El controlador JDBC proporciona tres clases para recuperar los metadatos de un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), que se usa para devolver información acerca de la base de datos que está conectado actualmente.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), que se usa para devolver información sobre el conjunto de resultados.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), que se usa para devolver información acerca de los parámetros de instrucciones preparadas e invocables.  
  
 Los temas de esta sección describen cómo se puede usar cada una de estas tres clases de metadatos para trabajar con metadatos en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos.  
  
> [!NOTE]  
>  Dado que el uso de los métodos de metadatos analizados en esta sección suele ser costoso por lo que respecta al rendimiento de la aplicación, se deben usar con precaución.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[Usar metadatos de una base de datos](../../connect/jdbc/using-database-metadata.md)|Describe cómo recuperar información de metadatos sobre la base de datos conectada.|  
|[Usar metadatos del conjunto de resultados](../../connect/jdbc/using-result-set-metadata.md)|Describe cómo recuperar información de metadatos sobre el conjunto de resultados actual.|  
|[Usar metadatos de parámetros](../../connect/jdbc/using-parameter-metadata.md)|Describe cómo recuperar información de metadatos sobre los parámetros de las instrucciones preparadas e invocables.|  
  
## <a name="see-also"></a>Vea también  
 [Introducción al controlador JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
