---
title: Instalar SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f57fc3ea1a677a2655f5358a1d5c4b27045ea6ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098024"
---
# <a name="installing-smo"></a>Instalar SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Esta página proporciona información sobre cómo instalar SMO para su uso por los requisitos del sistema para que usen SMO y aplicaciones.

## <a name="smo-nuget-package"></a>Paquete de NuGet SMO

A partir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO se distribuye como el [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) paquete NuGet para permitir que los usuarios a desarrollar aplicaciones con SMO.

Esto es un sustituto de SharedManagementObjects.msi, que anteriormente se publicó como parte del Feature Pack de SQL para cada versión de SQL Server. Las aplicaciones que usan SMO deben actualizarse para utilizar el paquete de NuGet en su lugar y serán responsables de garantizar que los archivos binarios se instalan con la aplicación que se desarrolla.

>>[!Important]
>>Como se mencionó en el [archivos y números de versión](files-and-version-numbers.md) página, no debe instalar los ensamblados SMO en la GAC. Si lo hace, podría causar problemas con otras aplicaciones que también usan esas versiones de SMO (por ejemplo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

## <a name="installing-the-package"></a>Instalación del paquete

Consulte [NuGet Quick Start - uso de un paquete](https://docs.microsoft.com/nuget/quickstart/use-a-package) para obtener instrucciones y ejemplos de instalación y uso de un paquete de NuGet. 
  
## <a name="system-requirements"></a>Requisitos del sistema
  
 SMO requiere [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 se ejecutan, por lo que las aplicaciones que usen, deben asegurarse de que los equipos cliente tengan la versión o superior instalado. Algunos archivos binarios nativos que se instala con las bibliotecas de NetFx SMO también requieren el tiempo de ejecución de VC 2013 instalado; ese tiempo de ejecución no se incluye en el paquete. Puede descargar el adecuado para la arquitectura de destino desde redist https://www.microsoft.com/download/details.aspx?id=40784
  
