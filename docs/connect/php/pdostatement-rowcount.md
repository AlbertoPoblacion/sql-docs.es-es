---
title: PDOStatement::rowCount | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0569f26a-2376-4c20-8813-bd3c87d0ae9f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3536458fd56bba8406a9210537f20e31f8718c09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799113"
---
# <a name="pdostatementrowcount"></a>PDOStatement::rowCount
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Devuelve el número de filas agregadas, eliminadas o cambiadas en la última instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int PDOStatement::rowCount ();  
```  
  
## <a name="return-value"></a>Valor devuelto  
El número de filas agregadas, eliminadas o cambiadas.  
  
## <a name="remarks"></a>Notas  
Si la última instrucción SQL ejecutada mediante la clase PDOStatement asociado fue SELECT, el cursor PDO::CURSOR_FWDONLY devuelve -1. Un cursor PDO::CURSOR_SCROLLABLE devuelve el número de filas del conjunto de resultados.  
  
En la versión 2.0 de los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], se agregó compatibilidad con PDO.  
  
## <a name="example"></a>Ejemplo  
En este ejemplo se muestran dos usos de rowCount. En el primero, se devuelve el número de filas que se agregaron a la tabla. En el segundo, se muestra que rowCount puede devolver el número de filas en un conjunto de resultados al especificar un cursor desplazable.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table2(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
  
echo "\n\n";  
  
$con = null;  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
print $stmt->rowCount();  
?>  
```  
  
## <a name="see-also"></a>Consulte también  
[Clase PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
