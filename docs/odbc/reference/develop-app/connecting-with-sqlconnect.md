---
title: "Conexión con SQLConnect | Documentos de Microsoft"
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
- data sources [ODBC], connection functions
- connecting to driver [ODBC], SQLConnect
- functions [ODBC], data source or driver connections
- SQLConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: b16319d2-2c2c-4341-abb5-caa9e17362b4
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd3644acb609a041c53232a757fa27fc5b5a4bf1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-with-sqlconnect"></a>Conexión con SQLConnect
**SQLConnect** es la función de conexión más sencilla. Se requiere un nombre de origen de datos y acepta un Id. de usuario opcionales y una contraseña. Funciona bien para las aplicaciones que codifica un origen de datos nombre y no requieren un Id. de usuario o una contraseña. También funciona bien para las aplicaciones que desean controlan su propias "apariencia" o que no tienen ninguna interfaz de usuario. Estas aplicaciones pueden generar una lista de orígenes de datos mediante **SQLDataSources**, pedir al usuario para el origen de datos, el Id. de usuario y la contraseña y, a continuación, llame a **SQLConnect**.  
  
 El siguiente ejemplo se conecta a la base de datos Northwind, con un DSN denominado Northwind y recupera todos los campos de nombre y apellidos de todos los registros en la tabla Employees.  
  
```  
// Connecting_with_SQLConnect.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <mbstring.h>  
#include <stdio.h>  
  
#define MAX_DATA 100  
#define MYSQLSUCCESS(rc) ((rc == SQL_SUCCESS) || (rc == SQL_SUCCESS_WITH_INFO) )  
  
class direxec {  
   RETCODE rc; // ODBC return code  
   HENV henv; // Environment     
   HDBC hdbc; // Connection handle  
   HSTMT hstmt; // Statement handle  
  
   unsigned char szData[MAX_DATA]; // Returned data storage  
   SDWORD cbData; // Output length of data  
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH]; // Data source name  
  
public:  
   direxec(); // Constructor  
   void sqlconn(); // Allocate env, stat, and conn  
   void sqlexec(unsigned char *); // Execute SQL statement  
   void sqldisconn(); // Free pointers to env, stat, conn, and disconnect  
   void error_out(); // Displays errors  
};  
  
// Constructor initializes the string chr_ds_name with the data source name.  
// "Northwind" is an ODBC data source (odbcad32.exe) name whose default is the Northwind database  
direxec::direxec() {  
   _mbscpy_s(chr_ds_name, SQL_MAX_DSN_LENGTH, (const unsigned char *)"Northwind");  
}  
  
// Allocate environment handle and connection handle, connect to data source, and allocate statement handle.  
void direxec::sqlconn() {  
   SQLAllocEnv(&henv);  
   SQLAllocConnect(henv, &hdbc);  
   rc = SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);  
  
   // Deallocate handles, display error message, and exit.  
   if (!MYSQLSUCCESS(rc)) {  
      SQLFreeConnect(henv);  
      SQLFreeEnv(henv);  
      SQLFreeConnect(hdbc);  
      if (hstmt)  
         error_out();  
      exit(-1);  
   }  
  
   rc = SQLAllocStmt(hdbc, &hstmt);  
}  
  
// Execute SQL command with SQLExecDirect() ODBC API.  
void direxec::sqlexec(unsigned char * cmdstr) {  
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);  
   if (!MYSQLSUCCESS(rc)) {  //Error  
      error_out();  
      // Deallocate handles and disconnect.  
      SQLFreeStmt(hstmt,SQL_DROP);  
      SQLDisconnect(hdbc);  
      SQLFreeConnect(hdbc);  
      SQLFreeEnv(henv);  
      exit(-1);  
   }  
   else {  
      for ( rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS ; rc=SQLFetch(hstmt) ) {  
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &cbData);  
         // In this example, the data is sent to the console; SQLBindCol() could be called to bind   
         // individual rows of data and assign for a rowset.  
         printf("%s\n", (const char *)szData);  
      }  
   }  
}  
  
// Free the statement handle, disconnect, free the connection handle, and free the environment handle.  
void direxec::sqldisconn() {  
   SQLFreeStmt(hstmt,SQL_DROP);  
   SQLDisconnect(hdbc);  
   SQLFreeConnect(hdbc);  
   SQLFreeEnv(henv);  
}  
  
// Display error message in a message box that has an OK button.  
void direxec::error_out() {  
   unsigned char szSQLSTATE[10];  
   SDWORD nErr;  
   unsigned char msg[SQL_MAX_MESSAGE_LENGTH + 1];  
   SWORD cbmsg;  
  
   while (SQLError(0, 0, hstmt, szSQLSTATE, &nErr, msg, sizeof(msg), &cbmsg) == SQL_SUCCESS) {  
      sprintf_s((char *)szData, sizeof(szData), "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'", szSQLSTATE, nErr, msg);  
      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);  
   }  
}  
  
int main () {  
   direxec x;   // Declare an instance of the direxec object.  
   x.sqlconn();   // Allocate handles, and connect.  
   x.sqlexec((UCHAR FAR *)"SELECT FirstName, LastName FROM employees");   // Execute SQL command  
   x.sqldisconn();   // Free handles and disconnect  
}  
```
