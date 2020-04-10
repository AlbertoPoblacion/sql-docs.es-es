---
title: Cierre de objetos cuando no se usan | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f1f0c264a7752b296691f20f702ab345f18b1b37
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922583"
---
# <a name="closing-objects-when-not-in-use"></a>Cierre de objetos cuando no se usan
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cuando trabaje con objetos del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], especialmente [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) o uno de los objetos Statement como [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) o [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), debe cerrarlos explícitamente usando sus métodos close cuando ya no sean necesarios. Esto mejora el rendimiento al liberar lo antes posible los recursos del servidor y el controlador, en lugar de esperar a que el recolector de elementos no utilizados de la máquina virtual Java lo haga en su lugar.  
  
 Cerrar los objetos es especialmente importante para mantener una buena simultaneidad en el servidor cuando se usan bloqueos de desplazamiento. Los bloqueos de desplazamiento del búfer de captura al que se tuvo acceso por última vez se mantienen hasta que se cierra el conjunto de resultados. De igual forma, los identificadores que configuraron las instrucciones se conservan hasta que éstas se cierran. Si está reutilizando una conexión para varias instrucciones y las cierra antes de permitirles salir del ámbito, el servidor podrá limpiar los identificadores preparados con anterioridad.  
  
## <a name="see-also"></a>Consulte también  
 [Mejora del rendimiento y la confiabilidad con el controlador JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
