---
title: Usar parámetros de instrucciones | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1168c81d8eeb6a25b84f473858bc924f529a572
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058674"
---
# <a name="using-statement-parameters"></a>Usar parámetros de instrucciones
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un parámetro es una variable en una instrucción SQL que puede habilitar una aplicación ODBC:  
  
-   Proporcionando de forma eficaz valores para las columnas de una tabla.  
  
-   Mejorando la interacción del usuario para construir criterios de consulta.  
  
-   Administrar **texto**, **ntext**, y **imagen** datos y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-tipos de datos C específicos.  
  
 Por ejemplo, un **partes** tabla tiene columnas denominadas **PartID**, **descripción**, y **precio**. Para agregar una parte sin parámetros se requiere la construcción de una instrucción SQL como:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Aunque esta instrucción es aceptable para insertar una fila con un conjunto conocido de valores, resulta complicado cuando se requiere que una aplicación inserte varias filas. ODBC soluciona esto permitiendo que una aplicación reemplace cualquier valor de datos en una instrucción SQL mediante un creador de parámetro. Esto se indica mediante un signo de interrogación (?). En el ejemplo siguiente, tres valores de datos se reemplazan con marcadores de parámetros:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Los marcadores de parámetros se enlazan a variables de aplicación. Para insertar una nueva fila, la aplicación únicamente tiene que establecer los valores de las variables y ejecutar la instrucción. Después, el controlador recupera los valores actuales de las variables y los envía al origen de datos. Si se ejecuta la instrucción varias veces, la aplicación puede hacer que el proceso mejore al preparar la instrucción.  
  
 Cada número ordinal asignado a los parámetros de izquierda a derecha hace referencia a su marcador de parámetro. El marcador de parámetros del extremo izquierdo de una instrucción SQL tiene un valor ordinal de 1; el siguiente es el ordinal 2, etc.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Enlazar parámetros](../../relational-databases/native-client-odbc-queries/using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de consultas &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
