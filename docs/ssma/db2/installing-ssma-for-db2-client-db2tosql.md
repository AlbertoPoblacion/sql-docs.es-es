---
title: Instalación de SSMA para DB2 de cliente (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1d479c8f7de1c9d7463e57f37f9e8588c9bc68b6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299048"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Instalación de SSMA para DB2 de cliente (DB2ToSQL)
El cliente SSMA consta de los archivos de programa que realizan las siguientes tareas:  
  
-   Conectarse a una base de datos DB2.  
  
-   Conectarse a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Convertir objetos de base de datos DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sintaxis.  
  
-   Cargar los objetos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Migrar datos a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Este tema proporciona los requisitos previos de instalación e instrucciones para la instalación de SSMA.  
  
## <a name="prerequisites"></a>Requisitos previos  
SSMA está diseñado para trabajar con DB2 en z/OS versión 9.0 y 10.0 o DB2 en las versiones LUW versión 9.8 y 10.1 o posterior y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
Antes de instalar SSMA, asegúrese de que el equipo cumple los requisitos siguientes:  
  
-   Windows 7 o versiones posteriores, o Windows Server 2008 o versiones posteriores.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 o una versión posterior.  
  
-   El [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] versión 4.0 o una versión posterior. El [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] está disponible en la versión 4.0 del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] medio del producto. También puede obtener desde el [Centro para desarrolladores de .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Proveedor OLEDB de Microsoft para DB2 versión 5 o una versión posterior y la conectividad a las bases de datos de DB2 que se van a migrar.  
  
-   Acceso a y los permisos necesarios en el equipo que hospeda la instancia de destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Azure SQL DB donde va a migrar datos y objetos de base de datos. Para obtener más información, consulte [conectarse a SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
-   4 GB de RAM recomendado.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Proveedor Microsoft OLE DB para DB2  
Para descargar el proveedor OLE DB para DB2 versión 5.0, vaya a [Microsoft® SQL Server® 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=42295).  
  
SSMA es una descarga Web. Para descargar la versión más reciente, consulte el [página de descarga de SQL Server Migration Assistant](https://aka.ms/ssmafordb2).  
  
Después de descargar la versión más reciente, debe extraer los archivos de instalación desde antes de poder instalar SSMA.  
  
**Para instalar al cliente SSMA**  
  
1.  Haga doble clic en SSMA para DB2 *n*. Install.exe, donde *n* es el número de compilación.  
  
2.  En la página de bienvenida, haga clic en **siguiente**.  
  
    Si no tiene instalados los requisitos previos, aparecerá un mensaje que indica que primero debe instalar los componentes necesarios. Asegúrese de que ha instalado todos los requisitos previos y, a continuación, ejecute el programa de instalación de nuevo.  
  
3.  Lea el contrato de licencia de usuario final. Si está de acuerdo, seleccione **acepto los términos del contrato de licencia**y, a continuación, haga clic en **siguiente**.  
  
4.  En la página Elegir tipo de instalación, haga clic en **típica**.  
  
5.  Haga clic en **Instalar**.  
  
> [!IMPORTANT]  
> 1.  Desinstale todas las versiones anteriores de SSMA para DB2 antes de instalar la nueva versión.  
  
La ubicación de instalación predeterminada es C:\Program Files\Microsoft SQL Server Migration Assistant para DB2.  
  
## <a name="see-also"></a>Vea también  
[Instalación de componentes de SSMA en SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Las bases de datos DB2 migrar a SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
