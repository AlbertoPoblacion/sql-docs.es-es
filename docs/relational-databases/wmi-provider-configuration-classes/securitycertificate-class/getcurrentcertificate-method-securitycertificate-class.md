---
title: Método GetCurrentCertificate (clase SecurityCertificate) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c7f5c207f786936a6bb9aebec03fb6e14fe7c1cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912041"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a>Método GetCurrentCertificate (clase SecurityCertificate)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtiene el certificado de seguridad actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.GetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>Partes  
 *object*  
 Objeto de la [clase SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) que representa un certificado de seguridad.  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*SHA*|Valor de objeto de cadena (parámetro de salida) que especifica la huella digital de SHA del certificado de seguridad actual una vez que el método finaliza.|  
|*SQLInstance*|Valor de cadena que especifica la instancia para la que se requiere el certificado.|  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Valor **uint32** que es 0 si se modificó el servicio correctamente, 1 si no se admite la solicitud y cualquier otro número para indicar un error.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Configurar protocolos de red de servidor y las bibliotecas de red](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
