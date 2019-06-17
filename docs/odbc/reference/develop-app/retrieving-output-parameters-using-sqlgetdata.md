---
title: Recuperar parámetros de salida mediante SQLGetData | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebb09b3118c2d16041d4ca60bf738d0fda561346
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199084"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Recuperar parámetros de salida mediante SQLGetData
Antes de ODBC 3.8, una aplicación podría recuperar solo los parámetros de salida de una consulta con un búfer de salida enlazada. Sin embargo, es difícil asignar un búfer muy grande cuando el tamaño del valor del parámetro es muy grande (por ejemplo, una imagen grande). ODBC 3.8 presenta una nueva forma de recuperar parámetros de salida en partes. Ahora puede llamar una aplicación **SQLGetData** con un búfer pequeño varias veces para recuperar un valor de parámetro grande. Esto es similar a la recuperación de datos de columna grande.  
  
 Para enlazar un parámetro de salida o el parámetro de entrada/salida va a recuperar en partes, llame a **SQLBindParameter** con el *InputOutputType* establecido en SQL_PARAM_OUTPUT_STREAM o SQL_PARAM_INPUT_OUTPUT _STREAM. Con SQL_PARAM_INPUT_OUTPUT_STREAM, puede usar una aplicación **SQLPutData** para introducir datos en el parámetro y, a continuación, usar **SQLGetData** para recuperar el parámetro de salida. Los datos de entrada deben estar en la datos en la ejecución (DAE) forman, mediante **SQLPutData** en lugar de enlazarla a un búfer asignado previamente.  
  
 Esta característica puede usarse en aplicaciones de ODBC 3.8 o vuelve a compilar ODBC 3.x y las aplicaciones de ODBC 2.x y estas aplicaciones deben tener un controlador de ODBC 3.8 que admita al recuperar parámetros de salida con **SQLGetData** y el controlador de ODBC 3.8 Administrador. Para obtener información sobre cómo habilitar una aplicación anterior usar nuevas características ODBC, vea [matriz de compatibilidad](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Ejemplo de uso  
 Por ejemplo, considere la posibilidad de ejecutar un procedimiento almacenado, **{llamada sp_f(?,?)}** , donde ambos parámetros se enlazan como SQL_PARAM_OUTPUT_STREAM y el procedimiento almacenado no devuelve ningún conjunto de resultados (más adelante en este tema encontrará un escenario más complejo):  
  
1.  Para cada parámetro, llame a **SQLBindParameter** con *InputOutputType* establecido en SQL_PARAM_OUTPUT_STREAM y *ParameterValuePtr* establecido en un token, como un número de parámetro , un puntero a datos o un puntero a una estructura que la aplicación se usa para enlazar parámetros de entrada. En este ejemplo usará el ordinal del parámetro como el token.  
  
2.  Ejecutar la consulta con **SQLExecDirect** o **SQLExecute**. Se devolverá SQL_PARAM_DATA_AVAILABLE, que indica que hay parámetros de salida transmitidos disponibles para su recuperación.  
  
3.  Llame a **SQLParamData** para obtener el parámetro que está disponible para su recuperación. **SQLParamData** devolverá SQL_PARAM_DATA_AVAILABLE con el token del primer parámetro disponible, que se establece en **SQLBindParameter** (paso 1). El token se devuelve en el búfer que el *ValuePtrPtr* apunta a.  
  
4.  Llame a **SQLGetData** con el argumento *Col*_or\_*Param_Num* establecido en el parámetro ordinal para recuperar los datos del primer parámetro disponible. Si **SQLGetData** devuelve SQL_SUCCESS_WITH_INFO y SQLState 01004 (datos truncados) y el tipo es de longitud variable en el servidor y cliente, no hay más datos para recuperar desde el primer parámetro disponible. Puede continuar llamar a **SQLGetData** hasta que devuelve SQL_SUCCESS o SQL_SUCCESS_WITH_INFO con otro **SQLState**.  
  
5.  Repita los pasos 3 y 4 para recuperar el parámetro actual.  
  
6.  Llame a **SQLParamData** nuevo. Si devuelve nada excepto SQL_PARAM_DATA_AVAILABLE, hay por secuencias no hay más datos de parámetro para recuperar y el código de retorno será el código de retorno de la siguiente instrucción que se ejecuta.  
  
7.  Llame a **SQLMoreResults** para procesar el conjunto de parámetros siguiente hasta que devuelva SQL_NO_DATA. **SQLMoreResults** devuelve SQL_NO_DATA en este ejemplo si el atributo de instrucción SQL_ATTR_PARAMSET_SIZE se estableció en 1. En caso contrario, **SQLMoreResults** devolverá SQL_PARAM_DATA_AVAILABLE para indicar que hay disponibles para el siguiente conjunto de parámetros para recuperar los parámetros de salida transmitidos.  
  
 El token de forma similar a un parámetro de entrada DAE, usada en el argumento *ParameterValuePtr* en **SQLBindParameter** (paso 1) puede ser un puntero que señala a una estructura de datos de aplicación, que contiene el ordinal del parámetro y obtener más información específica de la aplicación, si es necesario.  
  
 El orden de la salida transmitidos devuelto o parámetros de entrada/salida es específico del controlador y podría no ser siempre el mismo que el orden especificado en la consulta.  
  
 Si la aplicación no llama a **SQLGetData** en el paso 4, se descarta el valor del parámetro. De forma similar, si la aplicación llama a **SQLParamData** antes de que todos de un parámetro de valor se ha leído por **SQLGetData**, se descarta el resto del valor y la aplicación puede procesar el siguiente parámetro.  
  
 Si la aplicación llama a **SQLMoreResults** antes de toda la salida transmitida se procesan los parámetros (**SQLParamData** devuelve SQL_PARAM_DATA_AVAILABLE), se descartan todos los parámetros restantes. De forma similar, si la aplicación llama a **SQLMoreResults** antes de que todos de un parámetro de valor se ha leído por **SQLGetData**, se descarta el resto del valor y todos los parámetros restantes y el aplicación pueda continuar procesando el siguiente conjunto de parámetros.  
  
 Tenga en cuenta que una aplicación puede especificar el tipo de datos C en ambos **SQLBindParameter** y **SQLGetData**. El tipo de datos C especificado con **SQLGetData** invalida especificado en el tipo de datos de C **SQLBindParameter**, a menos que especifica el tipo de datos C en **SQLGetData** es SQL_APD_TYPE.  
  
 Aunque un parámetro de salida transmitidos es más útil cuando el tipo de datos del parámetro de salida es de tipo BLOB, esta funcionalidad también se puede usar con cualquier tipo de datos. Los tipos de datos admitidos por los parámetros de salida transmitidos se especifican en el controlador.  
  
 Si no hay parámetros SQL_PARAM_INPUT_OUTPUT_STREAM procesarse, **SQLExecute** o **SQLExecDirect** devolverá SQL_NEED_DATA en primer lugar. Una aplicación puede llamar a **SQLParamData** y **SQLPutData** para enviar datos del parámetro DAE. Cuando se procesan todos los parámetros de entrada DAE, **SQLParamData** devuelve SQL_PARAM_DATA_AVAILABLE para indicar los parámetros de salida transmitidos están disponibles.  
  
 Cuando existe se transmiten los parámetros de salida y parámetros de salida enlazada a procesarse, el controlador determina el orden de procesamiento de los parámetros de salida. Por lo tanto, si un parámetro de salida está enlazado a un búfer (el **SQLBindParameter** parámetro *InputOutputType* está establecido en SQL_PARAM_INPUT_OUTPUT o SQL_PARAM_OUTPUT), no se puede llenar el búfer hasta  **SQLParamData** devuelve SQL_SUCCESS o SQL_SUCCESS_WITH_INFO. Una aplicación debe leer un límite de búfer solo después **SQLParamData** devuelve SQL_SUCCESS o SQL_SUCCESS_WITH_INFO que después de todo se transmiten los parámetros de salida se procesan.  
  
 El origen de datos puede devolver que una advertencia y el resultado establecen, además en el parámetro de salida transmitidos. En general, las advertencias y los conjuntos de resultados se procesan por separado de un parámetro de salida transmitidos mediante una llamada a **SQLMoreResults**. Advertencias de proceso y el conjunto antes de procesar el parámetro de salida transmitidos de resultados.  
  
 En la tabla siguiente se describe varios escenarios de un único comando enviado al servidor y el funcionamiento de la aplicación.  
  
|Escenario|Valor devuelto de SQLExecute o SQLExecDirect|Qué hacer a continuación|  
|--------------|---------------------------------------------------|---------------------|  
|Datos solo incluyen parámetros de salida transmitidos|SQL_PARAM_DATA_AVAILABLE|Use **SQLParamData** y **SQLGetData** para recuperar los parámetros de salida transmitidos.|  
|Los datos incluyen un conjunto de resultados y parámetros de salida transmitidos|SQL_SUCCESS|Recuperar el conjunto de resultados con **SQLBindCol** y **SQLGetData**.<br /><br /> Llame a **SQLMoreResults** para iniciar el procesamiento de los parámetros de salida transmitidos. Debe devolver SQL_PARAM_DATA_AVAILABLE.<br /><br /> Use **SQLParamData** y **SQLGetData** para recuperar los parámetros de salida transmitidos.|  
|Los datos incluyen un mensaje de advertencia y parámetros de salida transmitidos|SQL_SUCCESS_WITH_INFO|Use **SQLGetDiagRec** y **SQLGetDiagField** para procesar los mensajes de advertencia.<br /><br /> Llame a **SQLMoreResults** para iniciar el procesamiento de los parámetros de salida transmitidos. Debe devolver SQL_PARAM_DATA_AVAILABLE.<br /><br /> Use **SQLParamData** y **SQLGetData** para recuperar los parámetros de salida transmitidos.|  
|Datos incluyen un mensaje de advertencia, conjunto de resultados y parámetros de salida transmitidos|SQL_SUCCESS_WITH_INFO|Use **SQLGetDiagRec** y **SQLGetDiagField** para procesar los mensajes de advertencia. A continuación, llame a **SQLMoreResults** que empiece a procesar el resultado de conjunto.<br /><br /> Recuperar un conjunto de resultados con **SQLBindCol** y **SQLGetData**.<br /><br /> Llame a **SQLMoreResults** para iniciar el procesamiento de los parámetros de salida transmitidos. **SQLMoreResults** debe devolver SQL_PARAM_DATA_AVAILABLE.<br /><br /> Use **SQLParamData** y **SQLGetData** para recuperar los parámetros de salida transmitidos.|  
|Consulta con parámetros de entrada DAE, por ejemplo, un parámetro (DAE) de entrada/salida por secuencias|SQL NEED_DATA|Llame a **SQLParamData** y **SQLPutData** DAE de enviar datos de parámetro de entrada.<br /><br /> Una vez procesados todos los parámetros de entrada DAE, **SQLParamData** puede devolver cualquier código de retorno que **SQLExecute** y **SQLExecDirect** puede devolver. A continuación, se pueden aplicar los casos en esta tabla.<br /><br /> Si el código de retorno es SQL_PARAM_DATA_AVAILABLE, parámetros de salida transmitidos están disponibles. Una aplicación debe llamar a **SQLParamData** nuevo para recuperar el token para el parámetro de salida transmitidos, como se describe en la primera fila de esta tabla.<br /><br /> Si el código de retorno es SQL_SUCCESS, hay un conjunto de resultados para procesar o el procesamiento está completo.<br /><br /> Si el código de retorno es SQL_SUCCESS_WITH_INFO, hay mensajes de advertencia para procesar.|  
  
 Después de **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** devuelve SQL_PARAM_DATA_AVAILABLE, un error de secuencia de función se producirá si una aplicación llama a un función que no está en la lista siguiente:  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions**  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr** / **SQLGetDescField** / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (con el identificador de instrucción)  
  
-   **SQLFreeStmt** (con la opción = SQL_CLOSE, SQL_DROP o SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (con HandleType = SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Las aplicaciones pueden usar aún **SQLSetDescField** o **SQLSetDescRec** para establecer la información de enlace. No se cambiará la asignación de campos. Sin embargo, los campos dentro del descriptor podrían devolver valores nuevos. Por ejemplo, podría devolver SQL_DESC_PARAMETER_TYPE SQL_PARAM_INPUT_OUTPUT_STREAM o SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Escenario de uso: Recuperar una imagen en partes de un conjunto de resultados  
 **SQLGetData** puede usarse para obtener datos de partes cuando un procedimiento almacenado devuelve un conjunto de resultados que contiene una fila de metadatos sobre una imagen y se devuelve la imagen en un parámetro de salida de gran tamaño.  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Escenario de uso: Enviar y recibir un objeto grande como un parámetro de entrada/salida por secuencias  
 **SQLGetData** puede usarse para conectarse y enviar datos en partes cuando un procedimiento almacenado pasa un objeto grande como un parámetro de entrada/salida, el valor hacia y desde la base de datos de transmisión por secuencias. No es necesario que almacenar todos los datos en memoria.  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Parámetros de la instrucción](../../../odbc/reference/develop-app/statement-parameters.md)
