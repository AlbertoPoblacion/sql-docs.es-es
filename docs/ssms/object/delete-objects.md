---
title: Eliminar objetos | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-objects
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.deleteobjects.f1
helpviewer_keywords: Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9b56c909bf8038ed70460bbea6ee98ba539bd3cb
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="delete-objects"></a>Eliminar objetos
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Use este cuadro de diálogo para eliminar una base de datos o un objeto de base de datos.  
  
## <a name="uielement-list"></a>Lista de UIElement  
**Objeto que se va a eliminar**  
Muestra los nombres, tipos, propietarios y estado de los objetos que van a eliminarse, así como los mensajes de error generados durante la ejecución.  
  
> [!NOTE]  
> La ejecución de **Eliminar** en una base de datos equivale a enviar DROP DATABASE en [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Mostrar dependencias**  
Haga clic para mostrar los objetos que dependen del objeto actualmente seleccionado y de los cuales éste depende (dependencia ascendente y descendente). La información que aparece en el cuadro de diálogo **Mostrar dependencias** es de solo lectura.  
  
> [!NOTE]  
> El botón **Mostrar dependencias** no aparece para todos los tipos de objetos de base de datos. Para ver las dependencias cuando el botón **Mostrar dependencias** no está disponible, haga clic con el botón derecho en el objeto en el Explorador de objetos y luego haga clic en **Ver dependencias**.  
  
**Eliminar la información del historial de copia de seguridad y restauración para las bases de datos**  
Solo aparece cuando se elimina una base de datos; esta casilla hace que el historial de copias de seguridad y restauración de la base de datos se elimine de la base de datos **msdb** .  
  
**Cerrar conexiones existentes**  
Solo aparece cuando se elimina una base de datos; esta casilla termina las conexiones a la base de datos.  
  
