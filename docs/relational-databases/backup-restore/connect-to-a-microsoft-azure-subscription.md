---
title: Conexión a una suscripción de Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 765763ae01183d0907e5371cf1420205cd5737b5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "68076132"
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Connect to a Microsoft Azure Subscription (Conectarse a una suscripción de Microsoft Azure)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Use **Connect to a Microsoft Azure Subscription (Conectarse a una suscripción de Microsoft)** para registrar un contenedor de blobs de Azure existente con la instancia de SQL Server.  El cuadro de diálogo creará una firma de acceso compartido y una directiva de acceso almacenada en un contenedor de blobs de Azure y, seguidamente, creará una credencial de SQL Server.  Este cuadro de diálogo aparece cuando se usa la tarea de copia de seguridad y restauración de SQL Server Management Studio y en dicha operación participa un dispositivo URL.

## <a name="limitation"></a>Limitación
La opción**Connect to a Microsoft Azure Subscription (Conectarse a una suscripción de Microsoft)** funciona únicamente con una cuenta de almacenamiento de Azure creada a través del modelo de implementación de administración de servicios (Clásico).  Para obtener más información sobre los modelos de implementación de Azure, vea [La implementación de Azure Resource Manager frente a la implementación clásica: los modelos de implementación y el estado de los recursos](https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model/).

## <a name="options"></a>Opciones
**Iniciar sesión**     
Permite iniciar sesión con la cuenta de Azure apropiada.

**Seleccionar una suscripción que usar**      
Permite elegir la suscripción que se prefiera de la lista desplegable.

**Seleccionar una cuenta de almacenamiento**  
Permite elegir la cuenta de almacenamiento que se prefiera de la lista desplegable.

**Seleccionar contenedor de blobs**   
Permite elegir el contenedor de blobs que se prefiera de la lista desplegable.

**Expiración de la directiva de acceso compartido**   
La directiva de acceso compartido expirará en la fecha que se indique.  La fecha de expiración predeterminada es de un año desde el momento de la creación.  Modifíquela como considere oportuno.

**Firma de acceso compartido generada**   
Este cuadro de texto enriquecido mostrará la firma de acceso compartido generada.

**Crear credencial**   
Este botón generará una directiva de acceso almacenada y una firma de acceso compartido y, luego, creará una credencial de SQL Server.
