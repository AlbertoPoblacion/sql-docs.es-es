---
title: ¿Cómo se implementan los cursores | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3d96a1879867f17b10baa3fd93f8225f3da7b184
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014335"
---
# <a name="how-cursors-are-implemented"></a>Cómo se implementan los cursores
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Las aplicaciones ODBC controlan el comportamiento de un cursor estableciendo uno o más atributos de instrucción antes de ejecutar una instrucción SQL. ODBC tiene dos maneras diferentes de especificar las características de un cursor:  
  
-   Tipo de cursor  
  
     Tipos de cursor se establecen mediante el atributo SQL_ATTR_CURSOR_TYPE de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Los tipos de cursor de ODBC son de solo avance, estático, controlado por conjunto de claves, mixto y dinámico. Establecer el tipo de cursor fue el método original para especificar los cursores en ODBC.  
  
-   Comportamiento de los cursores  
  
     Comportamiento del cursor se establece mediante los atributos SQL_ATTR_CURSOR_SCROLLABLE y SQL_ATTR_CURSOR_SENSITIVITY de **SQLSetStmtAttr**. Estos atributos se modelan en las palabras clave SCROLL y SENSITIVE definidas para la instrucción DECLARE CURSOR en los estándares ISO. Estas dos opciones ISO se introdujeron en la versión 3.0 de ODBC.  
  
 Las características de un cursor ODBC se deberían especificar con cualquiera de estos dos métodos, siendo preferente el uso de los tipos de cursor de ODBC.  
  
 Además de establecer el tipo de un cursor, las aplicaciones ODBC también establecen otras opciones, como el número de filas devueltas en cada captura, opciones de simultaneidad y niveles de aislamiento de transacción. Estas opciones se pueden establecer tanto para cursores de estilo ODBC (de solo avance, estático, controlado por conjunto de claves, mixto y dinámico) como para cursores de estilo ISO (desplazamiento y sensibilidad).  
  
 El [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client admite varias maneras de implementar físicamente los distintos tipos de cursores. El controlador implementa algunos tipos de cursores mediante un conjunto de resultados predeterminado de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; implementa otros como cursores de servidor o mediante la Biblioteca de cursores ODBC.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Usar conjuntos de resultados predeterminados de SQL Server](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
-   [Utilizar cursores de servidor](../../../relational-databases/native-client-odbc-cursors/implementation/using-server-cursors.md)  
  
-   [Biblioteca de cursores ODBC](../../../relational-databases/native-client-odbc-cursors/implementation/odbc-cursor-library.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de cursores &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
