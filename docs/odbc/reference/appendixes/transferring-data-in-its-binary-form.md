---
title: Transferencia de datos en su forma binaria | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7241124d7297dd661c3aef08701af0cc15d77d1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="transferring-data-in-its-binary-form"></a>Transferencia de datos en su forma binaria
Una aplicación puede transferir con seguridad datos (en el formulario interno utilizado por un DBMS especificado) entre dos orígenes de datos que utilizan la misma DBMS y la plataforma de hardware. Para una parte determinada de datos, los tipos de datos SQL deben ser el mismo en los orígenes de datos de origen y de destino. El tipo de datos de C es SQL_C_BINARY.  
  
 Cuando la aplicación llama **SQLFetch**, **SQLFetchScroll**, o **SQLGetData** para recuperar los datos desde el origen de datos de origen, el controlador recupera los datos de los datos código fuente y los transfiere, sin convertirlos a una ubicación de almacenamiento de tipo SQL_C_BINARY. Cuando la aplicación llama **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData o SQLSetPos** para enviar los datos a el origen de datos de destino, el controlador recupera los datos de la ubicación de almacenamiento y la transfiere, sin convertirlos, en el origen de datos de destino.  
  
> [!NOTE]  
>  Las aplicaciones que transferir los datos (excepto los datos binarios) de esta manera no son interoperables entre DBMS.  
  
 **SQLCopyDesc** puede utilizarse para copiar enlaces de fila en el DBMS de origen a los enlaces de parámetro en el DBMS de destino.
