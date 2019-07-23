---
title: OLE DB driver for SQL Server Features | Microsoft Docs
description: Características del controlador OLE DB para SQL Server
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 46f7de1e57686a0f54368407580d90236152d147
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989047"
---
# <a name="ole-db-driver-for-sql-server-features"></a>Características del controlador OLE DB para SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Además de exponer las características de los Componentes de Windows (Microsoft en versiones anteriores) Data Access (WDAC), el controlador OLE DB para SQL Server implementa también muchas otras características para exponer la funcionalidad de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>En esta sección    
 [Usar la creación de reflejo de bases de datos](../../oledb/features/using-database-mirroring.md)  
 Explica cómo el controlador OLE DB para SQL Server admite el uso de bases de datos reflejadas, que es la capacidad de mantener una copia, o reflejo, de una base de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en un servidor en espera.  
  
 [Realizar operaciones asincrónicas](../../oledb/features/performing-asynchronous-operations.md)  
 Explica la compatibilidad del controlador OLE DB para SQL Server con operaciones asincrónicas, que es la capacidad de devolver resultados inmediatamente sin bloquear el subproceso de llamada.  

[Uso de Azure Active Directory](using-azure-active-directory.md)  
Describe los nuevos métodos de autenticación introducidos en OLE DB controlador 18.2.1 que tienen una configuración predeterminada más segura y permiten conectarse a una instancia de Azure SQL Database mediante una identidad federada.

 [Usar conjuntos de resultados activos múltiples &#40;MARS&#41;](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 Describe cómo OLE DB controlador para SQL Server admite conjuntos de resultados activos múltiples (MARS). MARS permite ejecutar y recibir varios conjuntos de resultados mediante una conexión a una base de datos única.  
  
 [Utilizar tipos de datos XML](../../oledb/features/using-xml-data-types.md)  
 Explica la compatibilidad del controlador OLE DB para SQL Server con el tipo de datos XML, que es un tipo de datos basado en XML que se puede usar como un tipo de columna, un tipo de variable, un tipo de parámetro o un tipo de valor devuelto por una función.  
  
 [Usar tipos definidos por el usuario](../../oledb/features/using-user-defined-types.md)  
 Explica la compatibilidad del controlador OLE DB para SQL Server con los tipos definidos por el usuario (UDT), lo que amplía el sistema de tipos SQL al permitir almacenar objetos y estructuras de datos personalizadas en una base de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Usar tipos de valor grande](../../oledb/features/using-large-value-types.md)  
 Describe cómo OLE DB controlador para SQL Server admite tipos de datos de valores grandes, que son tipos de datos de objetos grandes (LOB).  
  
 [Cambiar las contraseñas mediante programación](../../oledb/features/changing-passwords-programmatically.md)  
 Explica la compatibilidad del controlador OLE DB para SQL Server con el control de contraseñas que han expirado para que las contraseñas se puedan cambiar ahora en el cliente sin implicación del administrador.  
  
 [Trabajar con aislamiento de instantánea](../../oledb/features/working-with-snapshot-isolation.md)  
 Explica la compatibilidad del controlador OLE DB para SQL Server con la mejora de las versiones de fila que aumenta el rendimiento de la base de datos al evitar situaciones de bloqueo de lectura/escritura.  
  
 [Trabajar con notificaciones de consulta](../../oledb/features/working-with-query-notifications.md)  
 Describe cómo OLE DB controlador para SQL Server admite la notificación de consumidor en la modificación del conjunto de filas.  
  
 [Realizar operaciones de copia masiva](../../oledb/features/performing-bulk-copy-operations.md)  
 Explica cómo el controlador OLE DB para SQL Server admite las operaciones de copia masiva que permiten la transferencia de grandes cantidades de datos a o desde una tabla o vista de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Utilizar el cifrado sin validación](../../oledb/features/using-encryption-without-validation.md)  
 Describe cómo usar el controlador de OLE DB para SQL Server con el fin de cifrar los datos enviados al servidor sin validar el certificado.  
  
 [Parámetros con valores de tabla &#40;controlador OLE DB para SQL Server &#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 Describe OLE DB controlador para la compatibilidad de SQL Server con los parámetros con valores de tabla.  
  
 [Tipos definidos por el usuario de CLR grandes](../../oledb/features/large-clr-user-defined-types.md)  
 Explica la compatibilidad con los tipos definidos por el usuario (UDT) de Common Language Runtime (CLR) grandes.  
  
 [Compatibilidad con FILESTREAM](../../oledb/features/filestream-support.md)  
 Describe OLE DB controlador para la compatibilidad de SQL Server con la característica FILESTREAM mejorada.  
  
 [Compatibilidad con Nombre de entidad de seguridad de servicio &#40;SPN&#41; en conexiones cliente](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 Explica cómo se ha ampliado la compatibilidad con los nombres principales de servicio (SPN) para habilitar la autenticación mutua en todos los protocolos.  
  
 [Compatibilidad de columnas dispersas con el controlador OLE DB para SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 Describe OLE DB controlador para la compatibilidad de SQL Server con columnas dispersas.  
  
 [Mejoras en la fecha y la hora](../../oledb/features/date-and-time-improvements.md)  
 Describe la compatibilidad agregada al controlador de OLE DB para SQL Server de los tipos de datos de fecha y hora.  
  
 [Detección de metadatos](../../oledb/features/metadata-discovery.md)  
 Describe las mejoras en la detección de metadatos realizadas en [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Compatibilidad de UTF-16 con el controlador OLE DB para SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 Describe un cambio de comportamiento presentado en [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Si proporciona un búfer de longitud fija al enlazar un parámetro de salida o el resultado de una columna, y si el carácter **wchar** escrito en el búfer antes del carácter de finalización es un punto de código que actúa como suplente superior de un par de suplentes y el carácter **wchar** siguiente es un punto de código que actúa como suplente inferior, el controlador OLE DB para SQL Server no agregará el punto de código que actúa como suplente superior al búfer.  
 
 [Compatibilidad de UTF-8 con el controlador OLE DB para SQL Server](../../oledb/features/utf-8-support-in-oledb-driver-for-sql-server.md)  
 Describe la compatibilidad con la codificación de servidor UTF-8 y las precauciones de configuración que deben tomar los usuarios al trabajar con datos con codificación UTF-8.
  
 [Controlador OLE DB para la compatibilidad de SQL Server con la alta disponibilidad y la recuperación ante desastres](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 Describe cómo se puede configurar una aplicación para aprovechar las características de alta disponibilidad con recuperación ante desastres que se han agregado en [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Obtener acceso a información de diagnóstico en el registro de eventos extendidos](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 Describe las mejoras realizadas en el controlador OLE DB para SQL Server y en el seguimiento de datos que ofrecen acceso a la información de diagnóstico del búfer de anillo y del registro de XEvents.  
  
 [Controlador OLE DB para la compatibilidad de SQL Server con LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 Describe OLE DB controlador para la compatibilidad de SQL Server con la característica LocalDB.  
  
## <a name="see-also"></a>Consulte también  
 [Controlador OLE DB para SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [Temas de procedimientos de OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [Instalación del controlador OLE DB para SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
