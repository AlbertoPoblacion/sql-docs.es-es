---
title: Estado, propiedad (clase SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 06193b774484afd6e6f7f47f286498c0698ab7c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094731"
---
# <a name="state-property-sqlservice-class"></a>Propiedad State (clase SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtiene o establece el estado actual del servicio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>Partes  
 *object*  
 Objeto de la [clase SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) que representa el servicio.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Valor uint32 que especifica el estado del servicio.  
  
 Los valores pueden ser alguno de los siguientes:  
  
 1  
 Detenido. El servicio está detenido.  
  
 2  
 Inicio pendiente. El servicio está a la espera de que se inicie.  
  
 3  
 Detención pendiente. El servicio está a la espera de que se detenga.  
  
 4  
 En ejecución. El servicio se está ejecutando.  
  
 5  
 Continuación pendiente. El servicio está a la espera de continuar.  
  
 6  
 Pausa pendiente. El servicio está a la espera de que se ponga en pausa.  
  
 7  
 En pausa. El servicio está en pausa.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Iniciar y detener servicios](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
