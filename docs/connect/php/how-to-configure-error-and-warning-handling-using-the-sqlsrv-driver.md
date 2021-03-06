---
title: Configurar el control de errores y advertencia con el controlador SQLSRV | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: errors and warnings
ms.assetid: 257c6f53-9137-4619-a613-eee33d2077e8
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a01d21006913ad2ae04491eb99d342b58f97a0a9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver"></a>Cómo configurar el control de errores y advertencias con el controlador SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

En este tema se describe cómo configurar el controlador SQLSRV para controlar errores y advertencias.  
  
De forma predeterminada, el controlador SQLSRV trata las advertencias como errores; una llamada a una función de **sqlsrv** que genera un error o una advertencia devolverá el valor **False**. Para deshabilitar este comportamiento, use la [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) función. Cuando la línea de código siguiente se incluye al principio de una secuencia de comandos, un **sqlsrv** función que únicamente genera advertencias (no errores) no devolverá **false**:  
  
`sqlsrv_configure("WarningsReturnAsErrors", 0);`  
  
La siguiente línea de código restablecerá el comportamiento predeterminado (las advertencias se tratan como errores):  
  
`sqlsrv_configure("WarningsReturnAsErrors", 1);`  
  
> [!NOTE]  
> Sin embargo, las advertencias que corresponden a los valores 01000, 01001, 01003 y 01S02 de SQLSTATE nunca se tratan como errores. Con independencia de la configuración, una función de **sqlsrv** que únicamente genera advertencias que corresponden a uno de estos estados no devolverá el valor **False**.  
  
El valor de **WarningsReturnAsErrors** también puede establecerse en el archivo php.ini. Por ejemplo, esta entrada de la sección de `[sqlsrv]` del archivo php.ini desactivará el comportamiento predeterminado.  
  
`sqlsrv.WarningsReturnAsErrors = 0`  
  
Para obtener información sobre cómo recuperar información de advertencias y errores, consulte [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) y [Cómo controlar errores y advertencias](../../connect/php/how-to-handle-errors-and-warnings-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Ejemplo  
En el siguiente ejemplo de código se muestra cómo deshabilitar el comportamiento de control de errores predeterminado. En el ejemplo se utiliza el comando PRINT de Transact-SQL para generar una advertencia. Para obtener más información sobre el comando PRINT, vea [PRINT (Transact-SQL)](http://go.microsoft.com/fwlink/?linkid=119518).  
  
En primer lugar, el ejemplo ilustra el comportamiento de control de errores predeterminado mediante la ejecución de una consulta que genera una advertencia. Esta advertencia se trata como un error. Después de cambiar la configuración de control de errores, se ejecuta la misma consulta. La advertencia no se trata como un error.  
  
En el ejemplo se da por hecho que SQL Server está instalado en el equipo local. Los resultados se agregan a la consola cuando se ejecuta el ejemplo en la línea de comandos.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName );  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* The Transact-SQL PRINT statement can be used to return   
informational or warning messages*/  
$tsql = "PRINT 'The PRINT statement can be used ";  
$tsql .= "to return user-defined warnings.'";  
  
/* Execute the query and print any errors. */  
$stmt1 = sqlsrv_query( $conn, $tsql);  
if($stmt1 === false)  
{  
     echo "By default, warnings are treated as errors:\n";  
     /* Dump errors in the error collection. */  
     print_r(sqlsrv_errors(SQLSRV_ERR_ERRORS));  
}  
  
/* Disable warnings as errors behavior. */  
sqlsrv_configure("WarningsReturnAsErrors", 0);  
  
/* Execute the same query and print any errors. */  
$stmt2 = sqlsrv_query( $conn, $tsql);  
if($stmt2 === false)  
{  
     /* Dump errors in the error collection. */  
     /* Since the warning generated by the query will not be treated as   
        an error, this block of code will not be executed. */  
     print_r(sqlsrv_errors(SQLSRV_ERR_ERRORS));  
}  
else  
{  
     echo "After calling ";  
     echo "sqlsrv_configure('WarningsReturnAsErrors', 0), ";  
     echo "warnings are not treated as errors.";  
}  
  
/*Close the connection. */  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="see-also"></a>Vea también  
[Actividad de registro](../../connect/php/logging-activity.md)  
[Guía de programación para el controlador SQL para PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Referencia de API del controlador SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
