---
title: Propiedad PropertyValType (clase ClientNetworkProtocolProperty) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- PropertyValType Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyValType property
ms.assetid: 624b9bdd-ed93-4140-bd4e-00d714a2558c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c1b503ea721aa83f9e9954a2181b1b252b211474
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016137"
---
# <a name="propertyvaltype-property-clientnetworkprotocolproperty-class"></a>Propiedad PropertyValType (clase ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtiene el tipo de datos del valor almacenado en la propiedad al que hace referencia el [Propertyidx (clase ClientNetworkProtocolProperty)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Partes  
 *object*  
 Un [clase ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) objeto que representa un atributo del protocolo de red utilizado por el [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cliente.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un **uint32** valor que especifica el tipo de datos del valor de propiedad.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Configurar protocolos de cliente](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
