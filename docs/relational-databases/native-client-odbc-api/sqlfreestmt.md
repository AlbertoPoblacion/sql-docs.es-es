---
title: SQLFreeStmt | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 32b1f1185dad9b173c12f3acb232c2426d5db411
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014475"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Por lo general   
      **SQLFreeStmt** no se recomienda en ODBC 3.0 y posterior. Sin embargo si la aplicación debe volver a usar la instrucción debería usar aún **SQLFreeStmt** con el **SQL_RESET_PARAMS** y **SQL_UNBIND** opciones). También puede utilizar [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), y [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) para reemplazar o duplicar la función de **SQLFreeStmt** y se debe utilizar en su lugar.  
  
 En general, resulta más eficaz reutilizar instrucciones que to, colocarlos y asignar nuevos. Sin embargo en algunas situaciones, como la reutilización de instrucciones, SQLFreeStmt todavía debe utilizarse.  
  
## <a name="see-also"></a>Vea también  
 [Función SQLFreeStmt](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [Detalles de implementación de la API de ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
