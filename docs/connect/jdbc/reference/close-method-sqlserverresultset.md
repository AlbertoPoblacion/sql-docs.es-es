---
title: "Close (método) (SQLServerResultSet) | Documentos de Microsoft"
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
apiname: SQLServerResultSet.close
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cabdcad9f2a358e767af49f0ec3772f5ed552a74
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="close-method-sqlserverresultset"></a>Método close (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esto libera [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) del objeto base de datos y recursos de JDBC inmediatamente en lugar de esperar para que esto suceda cuando se cierra automáticamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método de cierre especificado por el método de cierre en la interfaz java.sql.ResultSet.  
  
 Un objeto SQLServerResultSet lo cierra automáticamente el [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto que lo generó cuando ese objeto SQLServerStatement está cerrado, vuelve a ejecutar ni debe usarse para recuperar el resultado siguiente de una secuencia de varios resultados . Un objeto SQLServerResultSet se cierra automáticamente cuando es recolectado.  
  
 Cuando se ejecuta una instrucción que genera un conjunto de resultados grande de solo avance y solo lectura, es posible que únicamente esté interesado en algún conjunto inicial de filas en el conjunto de resultados que se ha devuelto. En este caso, la aplicación puede llamar a la [cancelar](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) establece método de objeto de instrucción asociado antes de cerrar el resultado con el fin de minimizar el tiempo de procesamiento necesario para descartar las filas innecesarias restantes. Recomendamos comparar los inconvenientes entre el tiempo de procesamiento que se ahorraría y el tiempo y el viaje de ida y vuelta al servidor que se necesita para cancelar la ejecución a la hora de decidir si utilizar o no esta técnica.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
