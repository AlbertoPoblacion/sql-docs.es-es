---
title: Asignar tipos de datos (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcca4bc6161526d1bd78e55bc9452f2d7d9d69d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200003"
---
# <a name="mapping-data-types-odbc"></a>Asignar tipos de datos (ODBC)
  El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asignaciones de controlador ODBC de Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipos de datos SQL a tipos de datos SQL de ODBC. En las secciones siguientes se describen los tipos de datos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL y los tipos de datos ODBC SQL a los que se asignan. También se tratan los tipos de datos ODBC SQL y sus tipos de datos ODBC C correspondientes, así como las conversiones compatibles y predeterminadas.  
  
> [!NOTE]  
>  El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** tipo de datos asigna al tipo de datos SQL_BINARY o SQL_VARBINARY ODBC porque los valores de **marca de tiempo** columnas no son **datetime** valores, pero **binary (8)** o **varbinary (8)** valores que indican la secuencia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] actividad en la fila. Si el controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client encuentra un valor SQL_C_WCHAR (Unicode) con un número impar de bytes, se trunca el byte impar final.  
  
## <a name="dealing-with-sqlvariant-data-type-in-odbc"></a>Administrar tipos de datos sql_variant en ODBC  
 El **sql_variant** columna tipo de datos puede contener ninguno de los tipos de datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] excepto objetos grandes (LOB), como **texto**, **ntext**, y  **imagen**. Por ejemplo, podría contener la columna **smallint** valores para algunas filas, **float** valores en otras filas y **char/nchar** valores en el resto.  
  
 El **sql_variant** tipo de datos es similar a la **Variant** tipo de datos en Microsoft Visual Basic??.  
  
### <a name="retrieving-data-from-the-server"></a>Recuperar datos del servidor  
 ODBC no tiene un concepto de tipos variant, limitar el uso de la **sql_variant** tipo de datos con un controlador ODBC en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si se especifica el enlace, el **sql_variant** tipo de datos debe estar enlazado a uno de los tipos de datos ODBC documentados. **SQL_CA_SS_VARIANT_TYPE**, un nuevo atributo específico para el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client, devuelve el tipo de datos de una instancia en el **sql_variant** columna para el usuario.  
  
 Si se especifica ningún enlace, el [SQLGetData](../native-client-odbc-api/sqlgetdata.md) función puede utilizarse para determinar el tipo de datos de una instancia en el **sql_variant** columna.  
  
 Para recuperar **sql_variant** datos, siga estos pasos.  
  
1.  Llame a **SQLFetch** para colocar en la fila recuperada.  
  
2.  Llame a **SQLGetData**, especificando SQL_C_BINARY como el tipo y 0 para la longitud de datos. Esto obliga al controlador para leer el **sql_variant** encabezado. El encabezado proporciona el tipo de datos de la instancia en el **sql_variant** columna. **SQLGetData** devuelve el tamaño (en bytes) del valor.  
  
3.  Llame a [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) especificando **SQL_CA_SS_VARIANT_TYPE** como su valor de atributo. Esta función devolverá el tipo de datos C de la instancia en el **sql_variant** columna al cliente.  
  
 A continuación se incluye un segmento de código que muestra los pasos anteriores.  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 Si el usuario crea el enlace mediante [SQLBindCol](../native-client-odbc-api/sqlbindcol.md), el controlador lee los metadatos y los datos. A continuación, el controlador convierte los datos al tipo ODBC adecuado especificado en el enlace.  
  
### <a name="sending-data-to-the-server"></a>Enviar datos al servidor  
 **SQL_SS_VARIANT**, un nuevo tipo de datos específicos de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client, se usa para los datos enviados a un **sql_variant** columna. Al enviar datos al servidor mediante parámetros (por ejemplo, INSERT INTO NombreDeTabla VALUES (?,?)), [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) se usa para especificar la información de parámetros, incluido el tipo de C y la correspondiente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC de Native Client convertirá el tipo de datos C en uno de los adecuados **sql_variant** subtipos.  
  
## <a name="see-also"></a>Vea también  
 [Procesar resultados &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
