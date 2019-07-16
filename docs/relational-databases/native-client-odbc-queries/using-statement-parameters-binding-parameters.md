---
title: Enlazar parámetros | Documentos de Microsoft
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
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 03903eedf9d1434ae7b1c20c2e6ddd57836b33cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942785"
---
# <a name="using-statement-parameters---binding-parameters"></a>Usar parámetros de instrucciones: enlazar parámetros
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Cada marcador de parámetros de una instrucción SQL debe estar asociado o enlazado a una variable de la aplicación antes de que se pueda ejecutar la instrucción. Esto se realiza mediante una llamada a la [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) función. **SQLBindParameter** describe la variable de programa (dirección, tipo de datos C etc.) para el controlador. También identifica el marcador de parámetros indicando su valor ordinal y, a continuación, describe las características del objeto SQL que representa (tipo de datos SQL, precisión, etc.).  
  
 Los marcadores de parámetros se pueden enlazar o reenlazar en cualquier momento antes de que se ejecute una instrucción. Un enlace de parámetro continúa activo hasta que se produce uno de los siguientes eventos:  
  
-   Una llamada a [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) con el *opción* parámetro establecido en SQL_RESET_PARAMS libera todos los parámetros enlazados al identificador de instrucción.  
  
-   Una llamada a **SQLBindParameter** con *ParameterNumber* establecido en el ordinal de un marcador de parámetros enlazado libera automáticamente el enlace anterior.  
  
 Una aplicación también puede enlazar parámetros a matrices de variables de programa para procesar una instrucción SQL por lotes. Existen dos tipos de enlaces de matriz:  
  
-   El enlace de modo de columna se hace cuando cada parámetro individual se enlaza a su propia matriz de variables.  
  
     El enlace se especifica mediante una llamada a [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) con *atributo* establecido en SQL_ATTR_PARAM_BIND_TYPE y *ValuePtr* establecido en SQL_PARAM_BIND_BY_COLUMN.  
  
-   El enlace de modo de fila se hace cuando todos los parámetros de la instrucción SQL se enlazan como una unidad a una matriz de estructuras que contienen variables individuales para los parámetros.  
  
     El enlace se especifica mediante una llamada a **SQLSetStmtAttr** con *atributo* establecido en SQL_ATTR_PARAM_BIND_TYPE y *ValuePtr* establecido en el tamaño de la explotación de estructura el variables del programa.  
  
 Cuando el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client envía parámetros de cadena binaria o carácter en el servidor, rellena los valores para la longitud especificada en **SQLBindParameter** *ColumnSize* parámetro. Si una aplicación de ODBC 2.x especifica 0 para *ColumnSize*, el controlador rellena el valor del parámetro a la precisión del tipo de datos. La precisión es 8000 cuando se conecta con los servidores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 255 cuando se conecta con versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *ColumnSize* en bytes para las columnas de tipo variant.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permite definir nombres para parámetros de procedimiento almacenado. ODBC 3.5 también introdujo la compatibilidad con el uso de parámetros con nombre para llamar a procedimientos almacenados de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta compatibilidad se puede utilizar para:  
  
-   Llamar a un procedimiento almacenado y proporcionar valores para un subconjunto de parámetros definido para el procedimiento almacenado.  
  
-   Especifique los parámetros en la aplicación en un orden diferente que el orden especificado cuando se creó el procedimiento almacenado.  
  
 Solo se admiten parámetros con nombre cuando se usa el [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXECUTE** instrucción o la secuencia de escape ODBC CALL para ejecutar un procedimiento almacenado.  
  
 Si **SQL_DESC_NAME** está establecido para un parámetro de procedimiento almacenado, también deben establecer todos los parámetros de procedimiento almacenado en la consulta **SQL_DESC_NAME**.  Si se usan literales en llamadas a procedimientos almacenados, que los parámetros tienen **SQL_DESC_NAME** establecido, los literales deben utilizar el formato *' nombre*=*valor*', donde *nombre* es el nombre de parámetro de procedimiento almacenado (por ejemplo, @p1). Para obtener más información, consulte [enlazar parámetros por nombre (parámetros con nombre)](https://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Vea también  
 [Usar parámetros de instrucciones](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
