---
title: Restricciones en conexiones de contexto y normales | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: d8cbdd195f698090602b98cdb6e5bab0a86556ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216411"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Conexiones de contexto y conexiones normales: restricciones
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  En este tema se describe las restricciones asociadas con la ejecución de código en el [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] procesos a través de conexiones normales y de contexto.  
  
## <a name="restrictions-on-context-connections"></a>Restricciones en conexiones de contexto  
 Al desarrollar su aplicación, tenga en cuenta las siguientes restricciones que se aplican a las conexiones de contexto:  
  
-   Solo puede tener una conexión de contexto abierta a una hora determinada para una conexión determinada. Si tiene varias instrucciones ejecutándose simultáneamente en conexiones independientes, cada una de ellas puede obtener su propia conexión de contexto. La restricción no afecta a solicitudes simultáneas de conexiones distintas; solo afecta a una solicitud determinada en una conexión determinada.  
  
-   No se admiten conjuntos de resultados activos múltiples (MARS) en una conexión de contexto.  
  
-   El **SqlBulkCopy** clase no funciona en una conexión de contexto.  
  
-   No se admite el procesamiento por lotes de actualizaciones en una conexión de contexto  
  
-   **SqlNotificationRequest** no se puede usar con los comandos que se ejecutan en una conexión de contexto.  
  
-   No se admite la cancelación de comandos que están ejecutándose en la conexión de contexto. El **SqlCommand.Cancel** método omite automáticamente la solicitud.  
  
-   No puede usarse ninguna otra palabra clave de cadena de conexión cuando se utiliza "context connection=true".  
  
-   El **SqlConnection.DataSource** propiedad devuelve null si la cadena de conexión para el **SqlConnection** es "conexión de contexto = true", en lugar del nombre de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Establecer el **SqlCommand.CommandTimeout** propiedad no tiene ningún efecto cuando el comando se ejecuta en una conexión de contexto.  
  
## <a name="restrictions-on-regular-connections"></a>Restricciones en conexiones normales  
 Al desarrollar su aplicación, tenga en cuenta las siguientes restricciones que se aplican a las conexiones normales:  
  
-   No se admite la ejecución de comandos asincrónica en servidores internos. Incluido "async = true" en la cadena de conexión de un comando y, a continuación, ejecutar el comando, da como resultado **System.NotSupportedException** producida. Aparece este mensaje: "No se admite el procesamiento asincrónico cuando se ejecuta en el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proceso."  
  
-   **SqlDependency** objeto no es compatible.  
  
## <a name="see-also"></a>Vea también  
 [Conexión de contexto](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
