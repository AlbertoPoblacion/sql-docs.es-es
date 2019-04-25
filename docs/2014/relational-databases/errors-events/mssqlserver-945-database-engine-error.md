---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8c2cf1abfb41f4a49fccfe1befad11e429037da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761746"
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|945|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DB_IS_SHUTDOWN|  
|Texto del mensaje|No se puede abrir la base de datos '%.*ls', porque no es posible tener acceso a archivos, o la memoria o el espacio en disco son insuficientes.  Compruebe el registro de errores de SQL Server para obtener más información.|  
  
## <a name="explanation"></a>Explicación  
No se pudo obtener acceso a la base de datos porque faltan archivos u otros recursos.  
  
## <a name="user-action"></a>Acción del usuario  
Compruebe el registro de errores para obtener información adicional acerca del error de memoria, espacio en disco o permiso. Confirme la ubicación de los archivos .mdf y .ndf de la base de datos afectada y confirme que la cuenta usada por [!INCLUDE[ssDE](../../includes/ssde-md.md)] tiene permiso de acceso a esos archivos. Después de corregir el problema, reinicie la base de datos usando ALTER DATABASE para establecerla en ONLINE.  
  
