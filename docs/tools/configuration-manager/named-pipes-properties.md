---
title: Propiedades de canalizaciones con nombre | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: a811080b5b0f4deaca5f2bd4ef1eacde2009a44a
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67732196"
---
# <a name="named-pipes-properties"></a>Propiedades de Canalizaciones con nombre
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Utilice la página **Protocolo**del cuadro de diálogo **Named Pipes Properties** (Propiedades de canalizaciones con nombre) para ver o cambiar la canalización con nombre que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escucha, cuando se utiliza el protocolo Canalizaciones con nombre.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para habilitar o deshabilitar el protocolo, o cambiar la canalización con nombre.  
  
## <a name="options"></a>Opciones  
 **Enabled**  
 Los valores posibles **Yes** y **No**.  
  
 **Nombre de canalización**  
 Especifica la canalización con nombre en la que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escucha. De manera predeterminada, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escucha en: `\\.\pipe\sql\query` para la instancia predeterminada y `\\.\pipe\MSSQL$<instancename>\sql\query` para una instancia con nombre. Este campo tiene un límite de 2.047 caracteres.  
  
## <a name="creating-an-alternate-named-pipe"></a>Crear una canalización con nombre alternativa  
 Para cambiar la canalización con nombre, escriba el nuevo nombre de canalización en el cuadro **Nombre de canalización** y, a continuación, detenga y reinicie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Como **sql\query** se conoce ampliamente como la canalización con nombre usada por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el cambio de la canalización puede ayudar a reducir el riesgo de ataques por programas malintencionados.  
  
### <a name="example"></a>Ejemplo  
 Escriba **\\\\.\pipe\unit\app** para escuchar en la canalización **unit\app** .  
  
 Escriba **\\\\.\pipe\acct** para escuchar en la canalización **acct** .  
  
## <a name="see-also"></a>Consulte también  
 [Habilitar o deshabilitar un protocolo de red de servidor](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Elegir un protocolo de red](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Crear una cadena de conexión válida con canalizaciones con nombre](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
