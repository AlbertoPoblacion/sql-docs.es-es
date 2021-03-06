---
title: Tipos definidos por el usuario | Documentos de Microsoft
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
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ccd5c353efd622fa406bfeb5c5b9c44c9546364b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="user-defined-types"></a>Tipos definidos por el usuario
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Tipos definidos por el usuario (UDT) se introdujeron en [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] para permitir que un desarrollador extender el sistema de tipo escalar del servidor mediante el almacenamiento de objetos de common language runtime (CLR) en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos. Los UDT pueden contener múltiples elementos y tener comportamientos, a diferencia de los tipos de datos de alias tradicionales que constan de una sola [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo de datos del sistema. Anteriormente, los UDT estaban restringidos a un tamaño máximo de 8 kilobytes. En [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], se agregó compatibilidad para UDT que superen los 64 kilobytes. A partir de la versión 3.0, el controlador JDBC también admite UDT de más de 64 kilobytes cuando se especifica el formato UserDefined.  
  
 No existe un cambio de comportamiento para los UDT con un tamaño menor o igual que 8.000 bytes, pero se admiten UDT de mayor tamaño y notifican su tamaño como "ilimitado".  
  
## <a name="see-also"></a>Vea también  
 [Describir los tipos de datos del controlador JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
