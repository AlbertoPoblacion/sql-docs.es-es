---
title: Asignar un identificador de entorno | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 35c58f136668893bb6dd865859f42b2bcaefe128
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134222"
---
# <a name="allocating-an-environment-handle"></a>Asignar un identificador de entorno
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Para que una aplicación pueda llamar a cualquier función ODBC, debe inicializar el entorno ODBC y asignar un identificador de entorno. Se trata del identificador de contexto global y marcador de posición del resto de los identificadores de ODBC. Para ello, una llamada a **SQLAllocHandle** con el *HandleType* parámetro establecido en SQL_HANDLE_ENV y *InputHandle* establecido en SQL_NULL_HANDLE.  
  
 Después de asignar el identificador de entorno, la aplicación debe establecer atributos de entorno para indicar qué versión de las llamadas a funciones de ODBC va a utilizar. Para usar el ODBC 3. *x* llamar funciones, [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) con el *atributo* parámetro establecido en SQL_ATTR_ODBC_VERSION y *ValuePtr* establecido en SQL_OV_ ODBC3.  
  
## <a name="see-also"></a>Vea también  
 [Comunicar con SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
