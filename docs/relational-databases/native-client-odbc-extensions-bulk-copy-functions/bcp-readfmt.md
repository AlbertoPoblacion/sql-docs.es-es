---
title: bcp_readfmt | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_readfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6e0277959c1776dfbe9bd088c639f243ad6a2f7d
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73782519"
---
# <a name="bcp_readfmt"></a>bcp_readfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lee una definición de formato de archivo de datos del archivo de formato especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RETCODE bcp_readfmt (  
        HDBC hdbc,  
        LPCTSTR szFormatFile);  
```  
  
## <a name="arguments"></a>Argumentos  
 *hdbc*  
 Es el identificador de la conexión ODBC habilitada para la copia masiva.  
  
 *szFormatFile*  
 Es la ruta de acceso y nombre del archivo que contiene los valores de formato para el archivo de datos.  
  
## <a name="returns"></a>Devuelve  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Comentarios  
 Una vez que **bcp_readfmt** Lee los valores de formato, realiza las llamadas adecuadas a [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) y [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md). No es necesario que analice un archivo de formato y realice estas llamadas.  
  
 Para conservar un archivo de formato, llame a [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md). Las llamadas a **bcp_readfmt** pueden hacer referencia a los formatos guardados. Para obtener más información, vea [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md).  
  
 Como alternativa, la utilidad de copia masiva (**bcp**) puede guardar los formatos de datos definidos por el usuario en archivos a los que **bcp_readfmt**puede hacer referencia. Para obtener más información acerca de la utilidad **BCP** y la estructura de los archivos de formato de datos **BCP** , vea [importación &#40;y&#41;exportación masivas de datos SQL Server](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 El valor **BCPDELAYREADFMT** del parámetro *eOption* de [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) modifica el comportamiento de bcp_readfmt.  
  
> [!NOTE]  
>  La versión 4.2 o posterior de la utilidad **bcp** debe haber generado el archivo de formato.  
  
## <a name="example"></a>Ejemplo  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones de copia masiva](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
