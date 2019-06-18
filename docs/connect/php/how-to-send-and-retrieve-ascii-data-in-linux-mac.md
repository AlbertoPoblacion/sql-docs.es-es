---
title: 'Cómo: enviar y recuperar datos ASCII en Linux y macOS (SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 2fe78cc80cd7ca77f09465fb7d3e92482da7d008
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181150"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>Envío y recuperación de datos ASCII en Linux y Mac OS 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

En este artículo se da por supuesto que se han generado las configuraciones regionales de ASCII (no UTF-8) o instalado en los sistemas Linux o macOS. 

Para enviar o recuperar conjuntos de caracteres ASCII en el servidor:  

1.  Si la configuración regional deseada no es el valor predeterminado en el entorno del sistema, asegúrese de que invoque `setlocale(LC_ALL, $locale)` antes de realizar la primera conexión. La función PHP setlocale() cambia la configuración regional solo para el script actual y, si se invoca después de realizar la primera conexión, puede omitirse.
 
2.  Cuando se usa el controlador SQLSRV, puede especificar `'CharacterSet' => SQLSRV_ENC_CHAR` como una conexión de opción, pero este paso es opcional porque es el valor predeterminado de codificación.

3.  Cuando se usa el controlador PDO_SQLSRV, hay dos maneras. En primer lugar, al realizar la conexión, establezca `PDO::SQLSRV_ATTR_ENCODING` a `PDO::SQLSRV_ENCODING_SYSTEM` (para obtener un ejemplo de configuración de una opción de conexión, consulte [PDO:: __construct](../../connect/php/pdo-construct.md)). Como alternativa, una vez conectado correctamente, agregue esta línea `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
Cuando se especifica la codificación de un recurso de conexión (en SQLSRV) o un objeto de conexión (PDO_SQLSRV), el controlador se da por supuesto que las otras cadenas de conexión opción usan esa misma codificación. También se da por hecho que las cadenas de nombre del servidor y consulta utilizan el mismo juego de caracteres.  
  
La codificación predeterminada para el controlador PDO_SQLSRV es UTF-8 (PDO:: sqlsrv_encoding_utf8), al contrario que el controlador SQLSRV. Para obtener más información sobre estas constantes de PHP, vea [Constantes &#40;Controladores de Microsoft para PHP para SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). 
  
## <a name="example"></a>Ejemplo  
Los ejemplos siguientes muestran cómo enviar y recuperar datos de ASCII mediante los controladores de PHP para SQL Server especificando una configuración regional determinada antes de realizar la conexión. Las configuraciones regionales en distintas plataformas Linux pueden llamarse de forma diferente de las configuraciones regionales mismas en macOS. Por ejemplo, la configuración regional de nosotros ISO-8859-1 (Latín 1) es `en_US.ISO-8859-1` en Linux, mientras que en macOS es el nombre `en_US.ISO8859-1`.
  
Los ejemplos supone que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está instalado en un servidor. Los resultados se agregan al explorador cuando se ejecuta el ejemplo en el explorador.  
  
```  
<?php  
  
// SQLSRV Example
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';
$connectionInfo = array('Database'=>'Test', 'UID'=>$uid, 'PWD'=>$pwd);
$conn = sqlsrv_connect($serverName, $connectionInfo);
  
if ($conn === false) {
    echo "Could not connect.<br>";  
    die(print_r(sqlsrv_errors(), true));
}  
  
// Set up the Transact-SQL query to create a test table
//   
$stmt = sqlsrv_query($conn, "CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");

// Insert data using a parameter array 
//
$tsql = "INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (?, ?)";
  
// Execute the query, $value being some ASCII string
//   
$stmt = sqlsrv_query($conn, $tsql, array(1, array($value, SQLSRV_PARAM_IN, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR))));
  
if ($stmt === false) {
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
else {  
    echo "The insertion was successfully executed.<br>";  
}  
  
// Retrieve the newly inserted data
//   
$stmt = sqlsrv_query($conn, "SELECT * FROM Table1");
$outValue = null;  
if ($stmt === false) {  
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data
//   
if (sqlsrv_fetch($stmt)) {  
    $outValue = sqlsrv_get_field($stmt, 1, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    echo "Value: " . $outValue . "<br>";
    if ($value !== $outValue) {
        echo "Data retrieved, \'$outValue\', is unexpected!<br>";
    }
}  
else {  
    echo "Error in fetching data.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Free statement and connection resources
//   
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
```
<?php  
  
// PDO_SQLSRV Example:
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';

try {
    $conn = new PDO("sqlsrv:Server=$serverName;Database=$database;", $uid, $pwd);
    $conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);
    
    // Set up the Transact-SQL query to create a test table
    //   
    $stmt = $conn->query("CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");
    
    // Insert data using parameters, $value being some ASCII string
    //
    $stmt = $conn->prepare("INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (:var1, :var2)");
    $stmt->bindValue(1, 1);
    $stmt->bindParam(2, $value);
    $stmt->execute();
    
    // Retrieve and display the data
    //
    $stmt = $conn->query("SELECT * FROM [Table1]");
    $outValue = null;
    if ($row = $stmt->fetch()) {
        $outValue = $row[1];
        echo "Value: " . $outValue . "<br>";
        if ($value !== $outValue) {
            echo "Data retrieved, \'$outValue\', is unexpected!<br>";
        }
    }
} catch (PDOException $e) {
    echo $e->getMessage() . "<br>";
} finally {
    // Free statement and connection resources
    //
    unset($stmt);
    unset($conn);
}

?>  
```  

## <a name="see-also"></a>Consulte también  
[Recuperación de datos](../../connect/php/retrieving-data.md)  
[Trabajar con datos UTF-8](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
[actualizar datos &#40;controladores de Microsoft para PHP para SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[Referencia de API del controlador SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Constantes &#40;controladores de Microsoft para PHP para SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Aplicación de ejemplo &#40;controlador SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  
