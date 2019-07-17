---
title: Suplantación y credenciales para conexiones | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: d83ee1d69e7083931a2f6e6befb89912abec43f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138678"
---
# <a name="impersonation-and-credentials-for-connections"></a>Suplantación y credenciales para conexiones
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  En la integración con Common Language Runtime (CLR) de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], el uso de la autenticación de Windows es complejo, pero es más seguro que usar la autenticación de SOL Server. Al usar la autenticación de Windows, tenga presente las consideraciones siguientes.  
  
 De forma predeterminada, un proceso de SQL Server que se conecta a Windows adquiere el contexto de seguridad de la cuenta de servicio de Windows para SQL Server. Pero es posible asignar una función CLR a una identidad del proxy, para que sus conexiones salientes tengan un contexto de seguridad diferente que el de la cuenta del servicio de Windows.  
  
 En algunos casos, es posible que desee suplantar al llamador mediante el uso de la **SqlContext.WindowsIdentity** propiedad en lugar de ejecutarse como cuenta de servicio. El **WindowsIdentity** instancia representa la identidad del cliente que invoca el código de llamada y solo está disponible cuando el cliente usa la autenticación de Windows. Después de haber obtenido el **WindowsIdentity** instancia, puede llamar a **Impersonate** para cambiar el token de seguridad del subproceso y, a continuación, abra Conexiones de ADO.NET en nombre del cliente.  
  
 Después de llamar a SQLContext.WindowsIdentity.Impersonate, no se puede obtener acceso a datos locales y no se puede obtener acceso a los datos del sistema. Para obtener acceso a datos de nuevo, se debe llamar a WindowsImpersonationContext.Undo.  
  
 El ejemplo siguiente muestra cómo suplantar al llamador utilizando el **SqlContext.WindowsIdentity** propiedad.  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Para obtener información acerca de los cambios de comportamiento en la suplantación, vea [cambios recientes en las características del motor de base de datos en SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Además, si obtuvo la instancia de identidad en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, no puede propagar esa instancia a otro equipo de forma predeterminada; la infraestructura de seguridad de Windows restringe esa acción de forma predeterminada. Sin embargo, hay un mecanismo denominado "delegación" que habilita la propagación de identidades de Windows a través de varios equipos de confianza. Puede aprender más acerca de la delegación en el artículo de TechNet "[Kerberos Protocol Transition and Constrained Delegation](https://go.microsoft.com/fwlink/?LinkId=50419)".  
  
## <a name="see-also"></a>Vea también  
 [Objeto SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
