---
title: Acerca de los controladores y orígenes de datos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69516a613cbd9071686067350ced2ce5ca166a27
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63294452"
---
# <a name="about-drivers-and-data-sources"></a>Acerca de controladores y orígenes de datos
*Controladores* son los componentes que procesan las solicitudes ODBC y devuelvan datos a la aplicación. Si es necesario, los controladores de modificar la solicitud de la aplicación en un formato que entienda el origen de datos. Debe usar el programa de instalación del controlador para agregar o eliminar un controlador desde su equipo.  
  
 *Orígenes de datos* son las bases de datos o tiene acceso a un controlador de archivos y se identifican mediante un nombre de origen de datos (DSN). Use el Administrador de orígenes de datos ODBC para agregar, configurar y eliminar orígenes de datos del sistema. Se describen los tipos de orígenes de datos que se pueden usar en la tabla siguiente.  
  
|Origen de datos|Descripción|  
|-----------------|-----------------|  
|Usuario|DSN de usuario locales en un equipo y pueden usarse únicamente por el usuario actual. Se registran en el subárbol del registro HKEY_CURRENT_USER.|  
|Sistema|Los DSN del sistema son locales en un equipo en lugar de dedicado a un usuario. El sistema o cualquier usuario con privilegios puede usar un origen de datos configurado con un DSN de sistema. Los DSN del sistema se registran en el subárbol del registro HKEY_LOCAL_MACHINE.|  
|Archivo|DSN de archivo son orígenes basados en archivos que se pueden compartir entre todos los usuarios que tienen instalados los mismos controladores y, por tanto, tienen acceso a la base de datos. Estos orígenes de datos no necesitan estar dedicados a un usuario ni ser local en un equipo. Nombres de origen de datos de archivo no identifica las entradas de registro dedicado; en su lugar, se identifican por un nombre de archivo con extensión .dsn.|  
  
 Orígenes de datos de usuario y del sistema se conocen colectivamente como *máquina* orígenes de datos porque son locales en un equipo.  
  
 Cada uno de estos orígenes de datos tiene una pestaña el **Administrador de orígenes de datos ODBC** cuadro de diálogo. Para obtener más información sobre los orígenes de datos, vea [Orígenes de datos](../../odbc/reference/data-sources.md).
