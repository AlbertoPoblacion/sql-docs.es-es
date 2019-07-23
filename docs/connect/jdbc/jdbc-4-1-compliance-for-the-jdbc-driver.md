---
title: Compatibilidad de JDBC 4,1 con el controlador JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f087fd40-8451-478e-b465-43112c711515
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6bf37b74c06ac03ef135eab7a09d275bde78b867
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956378"
---
# <a name="jdbc-41-compliance-for-the-jdbc-driver"></a>Cumplimiento de JDBC 4.1 con el controlador JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Las versiones anteriores de Microsoft JDBC Driver 4.2 para SQL Server son compatibles con las especificaciones de la API de Java Database Connectivity 4.0. Esta sección no es aplicable a las versiones anteriores a la versión 4.2.  
  
 La especificación de la API de Java Database Connectivity 4.1 es compatible con Microsoft JDBC Driver 4.2 para SQL Server, con los siguientes métodos de API.  
  
 **Clase SQLServerConnection**  
  
|Nuevo método|Descripción|Implementación del controlador JDBC|  
|----------------|-----------------|--------------------------------|  
|void abort(Executor executor)|Finaliza una conexión abierta a SQL Server.|Se implementa como se describe en la interfaz java.sql.Connection. Para más información, vea [java.sql.Connection](https://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
|void setSchema(String schema)|Establece el esquema de la conexión actual.|SQL Server no admite con la configuración del esquema para la sesión actual. El controlador registra automáticamente un mensaje de advertencia si se llama a este método. Para más información, vea [java.sql.Connection](https://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
|String getSchema()|Devuelve el nombre de esquema para la conexión actual.|Puesto que SQL Server no admite la configuración de la conexión actual, el controlador devuelve, en su lugar, el esquema predeterminado del usuario. Para más información, vea [java.sql.Connection](https://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
  
 **Clase SQLServerDatabaseMetaData**  
  
|Nuevo método|Descripción|Implementación del controlador JDBC|  
|----------------|-----------------|--------------------------------|  
|boolean generatedKeyAlwaysReturned()|Devuelve true, ya que el controlador admite la recuperación de claves generadas|Se implementa como se describe en java.sql. Interfaz DatabaseMetaData. Para más información, vea [java.sql.DatabaseMetaData](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html).|  
|ResultSet getPseudoColumns(String catalog, String schemaPattern,String tableNamePattern,String columnNamePattern)|Recupera una descripción de las pseudocolumnas/columnas ocultas|Devuelve un conjunto de resultados vacío, ya que SQL Server no tiene una noción de pseudocolumnas formal. Para más información, vea [java.sql.DatabaseMetaData](https://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html).|  
  
 **Clase SQLServerStatement**  
  
|Nuevo método|Descripción|Implementación del controlador JDBC|  
|----------------|-----------------|--------------------------------|  
|void closeOnCompletion()|Especifica que esta instrucción se cerrará cuando se cierren todos sus conjuntos de resultados dependientes.|Se implementa como se describe en la interfaz java.sql.Statement. Para más información, vea [java.sql.Statement](https://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html).|  
|isCloseOnCompletion() Boolean|Devuelve un valor que indica si esta instrucción se cerrará cuando se cierren todos sus conjuntos de resultados dependientes.|Se implementa como se describe en la interfaz java.sql.Statement. Para más información, vea [java.sql.Statement](https://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html).|  
  
 La especificación de la API de Java Database Connectivity 4.1 es compatible con Microsoft JDBC Driver 4.2 para SQL Server, con las siguientes características.  
  
|Nueva característica|Descripción|  
|-----------------|-----------------|  
|Nueva función Escape<br /><br /> Secuencia de escape de devolución de filas limitada|Compatibilidad parcial<br /><br /> Sintaxis de escape: \<Limit Rows > [offset < row_offset >](using-sql-escape-sequences.md).|  
  
 La especificación de la API de Java Database Connectivity 4.1 es compatible con Microsoft JDBC Driver 4.2 para SQL Server, con las siguientes asignaciones de tipo de datos.  
  
|Asignaciones de tipo de datos|Descripción|  
|------------------------|-----------------|  
|Ahora los métodos PreparedStatement.setObject() y PreparedStatement.setNull() admiten nuevas asignaciones de tipos de datos.|1. Nueva asignación de tipo de Java a JDBC<br /><br /> (a) java.math.BigInteger a JDBC BIGINT<br /><br /> (b) java.util.Date y java.util.Calendar a JDBC TIMESTAMP<br /><br /> 2. Nuevas conversiones de tipos de datos:<br /><br /> (a) java.math.BigInteger a CHAR, VARCHAR y LONGVARCHAR a BIGINT<br /><br /> (b) java.util.Date y java.util.Calendar a CHAR, VARCHAR, LONGVARCHAR, DATE, TIME y TIMESTAMP<br /><br /> Para obtener más información, vea la especificación de JDBC 4.1.|  
  
  
