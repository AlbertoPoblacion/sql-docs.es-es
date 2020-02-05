---
title: Abrir y guardar archivos con paquetes SSIS implementados en Azure | Microsoft Docs
description: Obtenga información sobre cómo abrir y guardar archivos de forma local y en Azure al aplicar lift-and-shift a los paquetes SSIS que usan los sistemas de archivos locales en SSIS en Azure.
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: 696b7bbd19ed41aeedaf0cbba683870c04de1b13
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "67896202"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>Abrir y guardar archivos de forma local y en Azure con paquetes SSIS implementados en Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



En este artículo se describe cómo abrir y guardar archivos de forma local y en Azure al aplicar lift-and-shift a los paquetes SSIS que usan los sistemas de archivos locales en SSIS en Azure.

## <a name="save-temporary-files"></a>Guardar los archivos temporales
Si necesita almacenar y procesar archivos temporales durante la ejecución de un paquete único, los paquetes pueden usar la carpeta de trabajo actual (`.`) o la carpeta temporal (`%TEMP%`) de los nodos de Integration Runtime de SSIS de Azure.

## <a name="use-on-premises-file-shares"></a>Usar recursos compartidos de archivos locales
Para seguir usando **recursos compartidos de archivos locales** al elevar y desplazar paquetes que usan sistemas de archivos locales a SSIS de Azure, haga lo siguiente:
1.  Transfiera los archivos de los sistemas de archivos locales a recursos compartidos de archivos locales.
2.  Una los recursos compartidos de archivos locales a una red virtual de Azure.
3.  Una la instancia de Azure SSIS IR a la misma red virtual. Para más información, vea [Unión de un entorno de ejecución para la integración de SSIS en Azure a una red virtual](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Conecte la instancia de Azure SSIS IR al recurso compartido de archivos locales dentro de la misma red virtual mediante la configuración de credenciales de acceso que usan la autenticación de Windows. Para obtener más información, vea [Conexión a datos y a recursos compartidos de archivos con la autenticación de Windows](ssis-azure-connect-with-windows-auth.md).
5.  Actualice las rutas de acceso de archivos locales en los paquetes a rutas de acceso UNC que apuntan a los recursos compartidos de archivos locales. Por ejemplo, actualice `C:\abc.txt` a `\\<on-prem-server-name>\<share-name>\abc.txt`.

## <a name="use-azure-file-shares"></a>Usar recursos compartidos de archivos de Azure
Para usar **Azure Files** al elevar y desplazar paquetes que usan sistemas de archivos locales a SSIS de Azure, haga lo siguiente:
1.  Transfiera archivos de los sistemas de archivos locales a Azure Files. Para obtener más información, consulte [Azure Files](https://azure.microsoft.com/services/storage/files/).
2.  Conecte la instancia de IR de SSIS de Azure a Azure Files mediante la configuración de las credenciales de acceso que usan la autenticación de Windows. Para obtener más información, vea [Conexión a datos y a recursos compartidos de archivos con la autenticación de Windows](ssis-azure-connect-with-windows-auth.md).
3.  Actualice las rutas de acceso de archivos locales en los paquetes a rutas de acceso UNC que apuntan a Azure Files. Por ejemplo, actualice `C:\abc.txt` a `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
