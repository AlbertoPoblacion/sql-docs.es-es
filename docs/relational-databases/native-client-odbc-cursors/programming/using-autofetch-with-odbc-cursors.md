---
title: Usar la captura automática con cursores ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7959068d5e24aa38157525ec133ab071611b5e85
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013643"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Usar la captura automática con cursores ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Cuando se conecta a una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client admite una opción de captura automática cuando se utiliza cualquier tipo de cursor de servidor. Con captura automática, el **SQLExecute** o **SQLExecDirect** función que se abre el cursor tiene también un implícita [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)función (SQL_FIRST). Las filas que componen el primer conjunto de filas se devuelven a las variables de aplicación enlazadas como parte de la ejecución de la instrucción y se ahorra un viaje de ida y vuelta (round trip) de la red al servidor. [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) no se admite cuando está habilitada la opción de captura automática; se deben enlazar las columnas del conjunto de resultados a variables de programa.  
  
 Las aplicaciones solicitan la captura automática estableciendo el atributo de la instrucción SQL_SOPT_SS_CURSOR_OPTIONS específica del controlador en SQL_CO_AF.  
  
## <a name="see-also"></a>Vea también  
 [Detalles de programación de cursores &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
