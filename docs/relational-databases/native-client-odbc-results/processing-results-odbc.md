---
title: Procesar resultados (ODBC) | Documentos de Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f96430e6dee07e1c3bd385bb68b5057637974217
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="processing-results-odbc"></a>Procesar los resultados (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Después de que una aplicación envía una instrucción SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devuelve los datos resultantes como uno o varios conjuntos de resultados. Un conjunto de resultados es un conjunto de filas y columnas que coinciden con los criterios de la consulta. Las instrucciones SELECT, las funciones de catálogo y algunos procedimientos almacenados generan un conjunto de resultados que quedan disponibles para las aplicaciones en formato tabular. Si la instrucción SQL ejecutada es un procedimiento almacenado, un lote que contiene varios comandos o una instrucción SELECT que contiene palabras clave, habrá varios conjuntos de resultados que procesar.  
  
 Las funciones de catálogo de ODBC también pueden recuperar los datos. Por ejemplo, [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md) recupera datos acerca de las columnas del origen de datos. Estos conjuntos de resultados pueden contener ninguna o más filas.  
  
 Otras instrucciones SQL, como GRANT o REVOKE, no devuelven conjuntos de resultados. Para estas instrucciones, el código de retorno de **SQLExecute** o **SQLExecDirect** suele ser la única indicación de la instrucción fue correcta.  
  
 Cada instrucción INSERT, UPDATE y DELETE devuelve un conjunto de resultados que contiene solamente el número de filas afectado por la modificación. Este recuento estará disponible cuando la aplicación llama [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md). ODBC 3. *x* aplicaciones deben llamar a **SQLRowCount** para recuperar el resultado conjunto o [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) para cancelarla. Cuando una aplicación ejecuta un lote o procedimiento almacenado que contiene varias instrucciones INSERT, UPDATE o DELETE, el conjunto de resultados de cada instrucción de modificación debe procesarse utilizando **SQLRowCount** o cancelarse utilizando **SQLMoreResults**. Estos recuentos se pueden cancelar incluyendo una instrucción SET NOCOUNT ON en el lote o procedimiento almacenado.  
  
 Transact-SQL incluye la instrucción SET NOCOUNT. Cuando la opción NOCOUNT está activada, SQL Server no devuelve los recuentos de las filas afectadas por una instrucción y **SQLRowCount** devuelve 0. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versión del controlador ODBC de Native Client presenta un determinado controlador [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) opción, SQL_SOPT_SS_NOCOUNT_STATUS, para informar de si la opción NOCOUNT está activada o desactivada. En cualquier momento **SQLRowCount** devuelve 0, la aplicación debe probar SQL_SOPT_SS_NOCOUNT_STATUS. Si se devuelve SQL_NC_ON, el valor de 0 en **SQLRowCount** solamente indica que SQL Server no se ha devuelto un recuento de filas. Si devuelve sql_nc_off, significa que NOCOUNT está desactivado y el valor de 0 en **SQLRowCount** indica que la instrucción no afectó a ninguna fila. Las aplicaciones no deben mostrar el valor de **SQLRowCount** cuando SQL_SOPT_SS_NOCOUNT_STATUS es SQL_NC_OFF. Los procedimientos almacenados o lotes de gran tamaño pueden contener varias instrucciones SET NOCOUNT de modo que los programadores no puedan suponer que SQL_SOPT_SS_NOCOUNT_STATUS sigue siendo constante. La opción debe probarse cada vez que **SQLRowCount** devuelve 0.  
  
 Otras instrucciones Transact-SQL devuelven los datos en mensajes, en lugar de en conjuntos de resultados. Cuando el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client recibe estos mensajes, devuelve SQL_SUCCESS_WITH_INFO para permitir que la aplicación saber que los mensajes informativos están disponibles. A continuación, puede llamar la aplicación **SQLGetDiagRec** para recuperar estos mensajes. Las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] que funcionan de esta manera son:  
  
-   DBCC  
  
-   SET SHOWPLAN (disponible con versiones anteriores de SQL Server)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client devuelve SQL_ERROR en una instrucción RAISERROR con una gravedad de 11 o superior. Si la gravedad del RAISERROR es 19 o superior, se interrumpe además la conexión.  
  
 Para procesar los conjuntos de resultados de una instrucción SQL, la aplicación:  
  
-   Determina las características del conjunto de resultados.  
  
-   Enlaza las columnas a variables de programa.  
  
-   Recupera un valor único, una fila completa de valores o varias filas de valores.  
  
-   Comprueba si hay más conjuntos de resultados y, en caso afirmativo, recorre de nuevo el bucle para determinar las características del nuevo conjunto de resultados.  
  
 El proceso de recuperar filas del origen de datos y devolverlas a la aplicación se denomina captura.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Determinar las características de un conjunto de resultados &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [Asignar almacenamiento](../../relational-databases/native-client-odbc-results/assigning-storage.md)  
  
-   [Capturar datos de resultados](../../relational-databases/native-client-odbc-results/fetching-result-data.md)  
  
-   [Asignación de tipos de datos &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/mapping-data-types-odbc.md)  
  
-   [Uso de tipo de datos](../../relational-databases/native-client-odbc-results/data-type-usage.md)  
  
-   [Traducción automática de datos de caracteres](../../relational-databases/native-client-odbc-results/autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>Vea también  
 [Cliente nativo de SQL Server &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Temas "Cómo..." de resultados de procesamiento &#40; ODBC &#41;](http://msdn.microsoft.com/library/772d9064-c91d-4cac-8b60-fcc16bf76e10)  
  
  
