---
title: Método ListIPAddresses (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1207c4c9688826b599548477a35ca123b9d39c28
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579936"
---
# <a name="configurationsetting-method---listipaddresses"></a>Método de ConfigurationSetting: ListIPAddresses
  Enumera las direcciones IP para el equipo del servidor de informes.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a>Parámetros  
 *IPAddress[]*  
 [fuera] Lista de dirección IP para el equipo.  
  
 *IPVersion[]*  
 [out] Versión para las direcciones IP.  
  
 *IsDhcpEnabled[]*  
 [out] Indica si las direcciones IP tienen DHCP habilitado.  
  
 *Longitud*  
 [out] Longitud de la matriz devuelta por el método.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente; un código de error indica que la llamada no se realizó correctamente.  
  
## <a name="remarks"></a>Observaciones  
 Las cadenas de*IPVersion* son V4 y V6.  
  
 Si *IsDhcpEnabled* es **True**, el valor de *IPAddress* es dinámico. No se debe usar para enlaces SSL.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Miembros MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
