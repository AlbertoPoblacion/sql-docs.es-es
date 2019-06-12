---
title: Usar una instrucción SQL con parámetros | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2c2647b4737268a1550bd9e45deb9557ecc0f81d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790133"
---
# <a name="using-an-sql-statement-with-parameters"></a>Usar una instrucción SQL con parámetros

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Para trabajar con los datos de una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una instrucción SQL que contiene parámetros IN, puede usar el método [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) de la clase [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) para devolver [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), que contiene los datos solicitados. Para ello, primero debe crear un objeto SQLServerPreparedStatement mediante el método [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) de la clase [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Al generar la instrucción SQL, los parámetros IN se especifican mediante el carácter ? (signo de interrogación), que actúa como un marcador de posición para los valores de parámetros que se van a pasar a la instrucción SQL. Para especificar un valor para un parámetro, puede usar uno de los métodos de establecedor de la clase SQLServerPreparedStatement. El método de establecedor usado se determina mediante el tipo de datos del valor que desea pasar a la instrucción SQL.

Al pasar un valor al método de establecedor, debe especificar no sólo el valor real que se va a usar en la instrucción SQL, sino también la posición ordinal del parámetro en la instrucción SQL. Por ejemplo, si la instrucción SQL contiene un único parámetro, su valor ordinal será 1. Si la instrucción contiene dos parámetros, el primer valor ordinal es 1 y el segundo 2.

En el siguiente ejemplo, se pasa una conexión abierta a la base de datos de ejemplo de [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] a la función, se genera una instrucción SQL preparada y se ejecuta con un solo valor de parámetro String y, luego, se leen los resultados del conjunto de resultados.

[!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]

## <a name="see-also"></a>Consulte también

[Usar instrucciones con SQL](../../connect/jdbc/using-statements-with-sql.md)
