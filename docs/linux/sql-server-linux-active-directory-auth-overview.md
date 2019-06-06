---
title: Autenticación de Active Directory para SQL Server en Linux
titleSuffix: SQL Server
description: En este artículo se proporciona información general de la autenticación de Active Directory para SQL Server en Linux.
author: rothja
ms.date: 04/01/2019
ms.author: jroth
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 906dd961bcfbb7ea6d8868fdf6eb51cc7bc814aa
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713598"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Autenticación de Active Directory para SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

En este artículo proporciona información general sobre la autenticación de Active Directory (AD) para [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en Linux. Autenticación de Active Directory es también conocida como la autenticación integrada en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Información general sobre la autenticación de AD

Autenticación de Active Directory permite a los clientes Unidos a un dominio en Windows o Linux para autenticarse en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con sus credenciales de dominio y el protocolo Kerberos.

Autenticación de Active Directory tiene las siguientes ventajas sobre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] autenticación:

- Los usuarios se autentican mediante el inicio de sesión único, sin que se le pida una contraseña.   
- Mediante la creación de inicios de sesión para los grupos de AD, puede administrar el acceso y permisos en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mediante la pertenencia a grupo de AD.  
- Cada usuario tiene una identidad única a través de su organización, por lo que no debe mantener un seguimiento de qué [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] inicios de sesión corresponden a las personas.   
- AD le permite aplicar una directiva de contraseña centralizada a través de su organización.   

## <a name="configuration-steps"></a>Pasos de configuración

Para utilizar la autenticación de Active Directory, debe tener un controlador de dominio de Active Directory (Windows) en la red.

Se proporcionan los detalles acerca de cómo configurar la autenticación de AD en el tutorial, [Tutorial: Utilizar autenticación de Active Directory con SQL Server en Linux](sql-server-linux-active-directory-authentication.md). En la lista siguiente proporciona un resumen con un vínculo a cada sección del tutorial:

1. [Unirse a un host de SQL Server a un dominio de Active Directory](sql-server-linux-active-directory-join-domain.md).
1. [Cree un usuario de AD para SQL Server y establezca el ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Configurar la tabla de claves del servicio de SQL Server](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Proteger el archivo keytab](sql-server-linux-active-directory-authentication.md#securekeytab).
1. [Configurar SQL Server para usar el archivo keytab para la autenticación Kerberos](sql-server-linux-active-directory-authentication.md#keytabkerberos).
1. [Crear inicios de sesión de SQL Server basada en AD en Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Conectarse a SQL Server mediante autenticación de AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Problemas conocidos

- En este momento, el único método de autenticación admitido para el extremo de reflejo de la base de datos es el certificado. Método de autenticación de WINDOWS se habilitará en una versión futura.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo implementar la autenticación de Active Directory para SQL Server en Linux, consulte [Tutorial: Utilizar autenticación de Active Directory con SQL Server en Linux](sql-server-linux-active-directory-authentication.md).
