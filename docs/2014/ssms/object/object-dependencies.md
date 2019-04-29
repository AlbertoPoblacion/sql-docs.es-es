---
title: Dependencias del objeto | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bba5156d159c87ad6ad0e011268bc655b45a5c37
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63032419"
---
# <a name="object-dependencies"></a>Dependencias del objeto
  Algunos objetos de base de datos dependen de otros objetos de base de datos. Por ejemplo, las vistas y los procedimientos almacenados dependen de la existencia de tablas que contengan los datos devueltos por la vista o procedimiento. En la página general de **Dependencias del objeto (página General)** del objeto actual se indican los objetos de la base de datos que deben estar presentes para que el objeto funcione correctamente, así como los objetos que dependen del objeto seleccionado. Un objeto que hace referencia a otro objeto en su definición y esa definición se almacena en el catálogo del sistema se denomina una *entidad de referencia*. Un objeto al que se hace referencia por otro objeto se denomina una *entidad a la que se hace referencia*.  
  
 **Dependencias del objeto (página Opciones avanzadas)** para el objeto actual contiene una lista de los objetos de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y los objetos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que dependen del objeto. Los objetos pueden estar almacenados en servidores diferentes.  
  
 Use este cuadro de diálogo para saber qué dependencias existen antes de cambiar o eliminar el objeto seleccionado.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Objetos que dependen de**_\<objeto seleccionado >_  
 Haga clic en este botón para mostrar una lista de los objetos de cuyas dependencias se realiza un seguimiento y que dependen del objeto seleccionado.  
  
 **Objetos de los cuales**_\<objeto seleccionado >_**depende**  
 Haga clic en este botón para mostrar una lista de los objetos de cuyas dependencias se realiza un seguimiento y de los que depende el objeto seleccionado.  
  
 **Dependencias**  
 Si **objetos que dependen de**  _\<objeto seleccionado >_ es hacer clic en, se muestra una vista jerárquica de los objetos que dependen del objeto seleccionado. Si **objetos de los cuales**  _\<objeto seleccionado >_ **depende** es hacer clic en, se muestra una vista jerárquica de objetos de los que depende el objeto seleccionado .  
  
 **Name**  
 Muestra el nombre del objeto seleccionado en la vista de árbol **Dependencias** anterior.  
  
 **Tipo**  
 Muestra el tipo del objeto seleccionado en la vista de árbol **Dependencias** anterior.  
  
 **Fecha de la última sincronización**  
 > [!NOTE]  
>  Esta opción solo está disponible en la página **Opciones avanzadas** .  
  
 Especifica la fecha y hora en que se actualizó por última vez la información de dependencias.  
  
 **Tipo de dependencia**  
 > [!NOTE]  
>  Esta opción solo está disponible en la página **General** .  
  
 Muestra el tipo de dependencia entre dos objetos. Puede ser uno de los valores siguientes:  
  
-   Dependencia enlazada a esquema  
  
     Es una relación entre dos objetos que evita que el objeto referenciado se elimine o modifique mientras el objeto que realiza la referencia exista. Se crea una Dependencia enlazada a esquema cuando una vista o función definida por el usuario se crea utilizando la cláusula WITH SCHEMABINDING o cuando una tabla hace referencia a otro objeto a través de una restricción CHECK o DEFAULT, o bien en la definición de una columna calculada.  
  
-   Dependencia no enlazada a esquema  
  
     Es una relación entre dos objetos que no evita que el objeto referenciado se elimine o modifique.  
  
-   Entidad no disponible o sin resolver  
  
     Indica que no se puede determinar el tipo de dependencia. Esta situación solo puede producirse cuando el objeto seleccionado está en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que es anterior a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
  
