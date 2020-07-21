---
title: Protección de su propiedad intelectual de SQL Server | Microsoft Docs
description: Entienda las opciones para proteger la propiedad intelectual de una aplicación de datos de SQL Server que se distribuye a los clientes.
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- protecting intellectual property
- intellectual property
ms.assetid: 174a646a-d65c-4074-8249-d783e91be2dd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dc6b2c88fc2405aea99ac8ce7de9c38cf43c99aa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773879"
---
# <a name="protecting-your-sql-server-intellectual-property"></a>Proteger su propiedad intelectual de SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Los desarrolladores de software a menudo preguntan cómo pueden distribuir su aplicación de datos [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a los clientes y a la vez evitar que la analicen y deconstruyan. En esta situación, lo esencial es proteger su propiedad intelectual. Se trata de un problema legal y la protección correspondiente reside en su contrato de licencia. Si [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] está instalado en un equipo administrado por terceros, usted pierde algunos aspectos de control de forma inherente. 

## <a name="nature-of-the-problem"></a>Naturaleza del problema
El propietario o administrador de un equipo puede acceder en todo momento a la instancia de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instalada en dicho equipo. Si implementa la aplicación en el equipo de un cliente, como es un administrador, se lo podrá conectar a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] como miembro del rol fijo de servidor **sysadmin**. Incluye la capacidad de conceder permisos, administrar copias de seguridad (incluida la restauración de copias de seguridad a otros equipos), el descifrado y el movimiento de archivos de datos, etc. Para obtener más información, vea [Conectarse a SQL Server cuando los administradores del sistema no tienen acceso](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md). 

Los procedimientos y datos almacenados pueden estar cifrados, pero la estructura de datos no puede estar oculta y los usuarios que puedan adjuntar un depurador al proceso del servidor pueden recuperar procedimientos y datos descifrados de la memoria en tiempo de ejecución.

Si los clientes no son administradores de los equipos, puede impedirles el acceso. Puede usar un [cifrado de datos transparente](../../relational-databases/security/encryption/transparent-data-encryption.md) para cifrar los archivos de datos, puede cifrar las copias de seguridad y puede auditar las acciones de todos los usuarios. Sin embargo, los administradores de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] y los administradores del equipo de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] pueden revertir estas acciones.

## <a name="solution"></a>Solución
Hay varias maneras de configurar el acceso a los datos de los clientes sin necesidad de instalar [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en el equipo del cliente. Es probable que la más sencilla sea usar [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)] para que los clientes no sean administradores, tal vez conjuntamente con [Siempre cifrados](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Para obtener más información para empezar a trabajar con [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], vea [¿Qué es SQL Database? Introducción a SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview).  

También puede hospedar un sistema [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en su propia red y permitir a los clientes acceder a los datos a través de su red, ya sea directamente o a través de una aplicación web.

## <a name="see-also"></a>Consulte también

[Centro de seguridad para el Motor de base de datos de SQL Server y Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
[Proteger SQL Server](../../relational-databases/security/securing-sql-server.md)  

