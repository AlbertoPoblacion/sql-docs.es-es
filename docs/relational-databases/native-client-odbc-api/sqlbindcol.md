---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4a92c95a67b6e9fd3d31917af4f5b7b19f4c613d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "73787793"
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Por regla general, considere las implicaciones del uso de **SQLBindCol** para realizar la conversión de datos. Las conversiones de enlaces son procesos de cliente, por lo que al recuperar, por ejemplo, un valor de punto flotante enlazado a una columna de carácter, el controlador realiza la conversión de punto flotante en carácter localmente cuando se captura una fila. La función [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT se puede utilizar para aplicar la carga de conversión de datos al servidor.  
  
 Una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede devolver varios conjuntos de filas de resultados al ejecutar una sola instrucción. Cada conjunto de resultados se debe enlazar por separado. Para obtener más información sobre cómo enlazar varios conjuntos de resultados, vea [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 El programador puede enlazar columnas a tipos de datos C específicos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mediante el valor *TargetType***SQL_C_BINARY**. Las columnas enlazadas a tipos específicos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]no son portables. Los tipos de datos C de ODBC específicos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]coinciden con las definiciones de tipos de DB-Library, y los programadores de DB-Library que trasladan aplicaciones tal vez desee aprovechar esta característica.  
  
 La notificación del truncamiento de datos es un proceso costoso para el controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Puede evitar el truncamiento asegurándose de que los búferes de datos enlazados son lo suficientemente grandes como para devolver datos. Para los datos de carácter, el ancho debe incluir el espacio de un terminador de cadena cuando se utiliza el comportamiento del controlador predeterminado para la finalización de las cadenas. Por ejemplo, el enlace de una columna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **** a una matriz de cinco caracteres produce el truncamiento de cada valor capturado. Si la misma columna se enlaza a una matriz de seis caracteres, se evita el truncamiento al proporcionar un elemento de cadena en el que se almacena el terminador nulo. [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) se puede utilizar para recuperar de forma eficaz datos binarios y de caracteres largos sin truncamiento.  
  
 En el caso de los tipos de datos de valores grandes, si el búfer proporcionado por el usuario no es lo suficientemente grande como para contener el valor completo de la columna, se devuelve **SQL_SUCCESS_WITH_INFO** y los datos de cadena. truncamiento derecho: se emite la advertencia. El argumento **StrLen_or_IndPtr** contendrá el número de caracteres/bytes almacenados en el búfer.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>SQLBindCol admite las características mejoradas de fecha y hora  
 Los valores de las columnas de resultados de los tipos de fecha y hora se convierten como se describe en [conversiones de SQL a C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Tenga en cuenta que para recuperar las columnas Time y DateTimeOffset como sus estructuras correspondientes (**SQL_SS_TIME2_STRUCT** y **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* debe especificarse como **SQL_C_DEFAULT** o **SQL_C_BINARY**.  
  
 Para obtener más información, vea [mejoras de fecha y hora &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Compatibilidad de SQLBindCol con tipos definidos por el usuario de CLR de gran tamaño  
 **SQLBindCol** admite tipos definidos por el usuario (UDT) CLR grandes. Para obtener más información, vea [tipos CLR grandes definidos por el usuario &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Consulte también  
 [SQLBindCol (función)](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
