---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ede93e1552451f7db8e286ac28284fed79ddef0c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63067861"
---
# <a name="sqlbindcol"></a>SQLBindCol
  Por regla general, considere las implicaciones del uso de **SQLBindCol** para realizar la conversión de datos. Las conversiones de enlaces son procesos de cliente, por lo que al recuperar, por ejemplo, un valor de punto flotante enlazado a una columna de carácter, el controlador realiza la conversión de punto flotante en carácter localmente cuando se captura una fila. La función [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT se puede utilizar para aplicar la carga de conversión de datos al servidor.  
  
 Una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede devolver varios conjuntos de filas de resultados al ejecutar una sola instrucción. Cada conjunto de resultados se debe enlazar por separado. Para obtener más información sobre cómo enlazar varios conjuntos de resultados, vea [SQLMoreResults](sqlmoreresults.md).  
  
 El programador puede enlazar columnas a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-tipos de datos C específicos mediante el *TargetType* valor `SQL_C_BINARY`. Las columnas enlazadas a tipos específicos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]no son portables. Los tipos de datos C de ODBC específicos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]coinciden con las definiciones de tipos de DB-Library, y los programadores de DB-Library que trasladan aplicaciones tal vez desee aprovechar esta característica.  
  
 La notificación del truncamiento de datos es un proceso costoso para el controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Puede evitar el truncamiento asegurándose de que los búferes de datos enlazados son lo suficientemente grandes como para devolver datos. Para los datos de carácter, el ancho debe incluir el espacio de un terminador de cadena cuando se utiliza el comportamiento del controlador predeterminado para la finalización de las cadenas. Por ejemplo, el enlace de una columna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** a una matriz de cinco caracteres produce el truncamiento de cada valor capturado. Si la misma columna se enlaza a una matriz de seis caracteres, se evita el truncamiento al proporcionar un elemento de cadena en el que se almacena el terminador nulo. [SQLGetData](sqlgetdata.md) se puede utilizar para recuperar de forma eficaz datos binarios y de carácter grandes sin truncamiento.  
  
 Para tipos de datos de gran valor, si el búfer proporcionado por el usuario no es suficientemente grande como para contener el valor completo de la columna, `SQL_SUCCESS_WITH_INFO` se devuelve y los datos de cadena"; se emite la advertencia de truncamiento por la derecha". El argumento `StrLen_or_IndPtr` contendrá el número de caracteres/bytes almacenados en el búfer.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>SQLBindCol admite las características mejoradas de fecha y hora  
 Los valores de columna de resultados de tipos de fecha y hora se convierten como se describe en [conversiones de SQL a C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Tenga en cuenta que para recuperar columnas time y datetimeoffset como sus estructuras correspondientes (`SQL_SS_TIME2_STRUCT` y **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* debe especificarse como `SQL_C_DEFAULT` o `SQL_C_BINARY`.  
  
 Para obtener más información, consulte [mejoras de fecha y hora &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Compatibilidad de SQLBindCol con tipos definidos por el usuario de CLR de gran tamaño  
 **SQLBindCol** admite tipos definidos por el usuario (UDT) de CLR de gran tamaño. Para obtener más información, consulte [Large CLR User-Defined tipos &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [SQLBindCol (función)](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [Detalles de implementación de la API de ODBC](odbc-api-implementation-details.md)  
  
  
