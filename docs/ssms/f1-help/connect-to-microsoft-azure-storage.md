---
title: Conectar con Almacenamiento de Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 68e20963c8d68c68c48752e4237b8cba3747fa0c
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67680302"
---
# <a name="connect-to-microsoft-azure-storage"></a>Conectar con Almacenamiento de Microsoft Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Utilice el cuadro de diálogo de **Conexión de almacenamiento de Windows Azure** para especificar una cuenta de almacenamiento y validar la conexión a Windows Azure.  
  
## <a name="options"></a>Opciones  
Especifique la siguiente información sobre su cuenta de Windows Azure y, a continuación, haga clic en **Siguiente** para continuar.  
  
1.  **Cuenta de almacenamiento** : especifique el nombre de la cuenta de almacenamiento.

   >[!NOTE]
   > Solo se puede conectar a [Cuentas de almacenamiento de uso general](https://docs.microsoft.com/azure/storage/storage-introduction#azure-storage-services). La conexión a otros tipos de cuentas de almacenamiento puede dar lugar a un error similar al siguiente:
   >
   >  El valor para uno de los encabezados HTTP no tiene el formato correcto. (Microsoft.SqlServer.StorageClient).
   >
   >  El servidor remoto devolvió un error: (400) Solicitud incorrecta. (Sistema)

2.  **Clave de cuenta** : especifique la clave de cuenta para la cuenta de almacenamiento especificada.  
  
3.  **Usar puntos de conexión seguros (HTTPS)** : esta opción usa la comunicación cifrada y el identificador seguro de un servidor web de la red.  
  
4.  **Guardar clave de cuenta** : esta opción guarda su contraseña en un archivo cifrado.  
  
