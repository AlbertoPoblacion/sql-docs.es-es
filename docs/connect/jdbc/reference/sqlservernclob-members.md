---
title: Los miembros de SQLServerNClob | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ffd65361d92986838fcd623bc52c54f2c986c61
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="sqlservernclob-members"></a>Miembros SQLServerNClob
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Las tablas siguientes enumeran los miembros expuestos por el [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md) clase.  
  
## <a name="constructors"></a>Constructores  
 Ninguno.  
  
## <a name="fields"></a>Campos  
 Ninguno.  
  
## <a name="inherited-fields"></a>Campos heredados  
 Ninguno.  
  
## <a name="methods"></a>Métodos  
  
|Nombre|Description|  
|----------|-----------------|  
|[liberar](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|Este método libera el **NCLOB** objeto y libera los recursos que contiene.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|Recupera el **NCLOB** valor designado por el **java.sql.NClob** objeto como un flujo ASCII.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|Recupera el **NCLOB** valor designado por el **java.sql.NClob** objeto.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|Recupera una copia de la subcadena especificada en el **NCLOB** valor designado por el **java.sql.NClob** objeto.|  
|[longitud](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|Recupera el número de caracteres de la **NCLOB** valor designado por el **java.sql.NClob** objeto.|  
|[posición](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|Recupera la posición del carácter del elemento especificado **java.sql.NClob** un objeto o una subcadena en la **java.sql.NClob** en función de la posición inicial especificada.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|Recupera un flujo que se va a utilizar para escribir ASCII caracteres para la **NCLOB** que este valor **java.sql.NClob** representa, comenzando en la posición especificada del objeto.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|Recupera un flujo que se va a utilizar para escribir una secuencia de caracteres Unicode para la **NCLOB** que este valor **java.sql.NClob** representa, comenzando en la posición especificada del objeto.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|Escribe el determinado **cadena** a la **NCLOB** a partir de la posición especificada.|  
|[truncar](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|Trunca la **NCLOB** valor para la longitud especificada.|  
  
## <a name="inherited-methods"></a>Métodos heredados  
  
|Clase heredada de|Métodos|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>Vea también  
 [Clase SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
