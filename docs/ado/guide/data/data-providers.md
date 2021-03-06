---
title: Proveedores de datos | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 98eb787fc3dbaab7b55795a0a1b3a99d9a43e2a4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="data-providers"></a>Proveedores de datos
Proveedores de datos representan diversos orígenes de datos, como bases de datos SQL, archivos secuenciales indizados, hojas de cálculo, almacenes de documentos y archivos de correo electrónico. Los proveedores exponen datos uniformemente mediante una abstracción común que se denomina conjunto de filas.  
  
 ADO es eficaz y flexible porque puede conectarse a cualquiera de varios proveedores de datos y seguir exponiendo el mismo modelo de programación, sin tener en cuenta las características específicas de un proveedor determinado. Sin embargo, dado que cada proveedor de datos es único, cómo interactúa la aplicación con ADO variará por el proveedor de datos.  
  
 Por ejemplo, las capacidades y características del proveedor OLE DB para SQL Server, que se utiliza para tener acceso a las bases de datos de Microsoft SQL Server, son considerablemente diferentes de los del proveedor Microsoft OLE DB para la publicación en Internet, que se utiliza para tener acceso a archivos almacena en un servidor Web.
