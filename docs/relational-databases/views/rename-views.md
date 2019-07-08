---
title: Cambio de nombre de las vistas | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc4d31360e86fa0ec60c482034ce1678801cf5f3
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582328"
---
# <a name="rename-views"></a>Cambiar el nombre de las vistas
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]
  Puede cambiar el nombre de una vista en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  Si cambia el nombre de una vista, pueden producirse errores en el código y las aplicaciones que dependen de la misma. Los elementos afectados pueden ser otras vistas, consultas, procedimientos almacenados, funciones definidas por el usuario y aplicaciones cliente. Tenga en cuenta que estos errores se producirán en cascada.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Requisitos previos](#Prerequisites)  
  
     [Seguridad](#Security)  
  
-   **Para cambiar el nombre de una vista, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Seguimiento:**  [Después de cambiar el nombre de una vista](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Prerequisites"></a> Requisitos previos  
 Obtiene una lista de todas las dependencias de la vista. Cualquier objeto, script o aplicación que haga referencia a la vista debe modificarse para reflejar el nuevo nombre de la vista. Para más información, consulte [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md). Se recomienda quitar la vista y volver a crearla con un nuevo nombre en lugar de cambiarle el nombre. Al volver a crear la vista, se actualiza la información de dependencia para los objetos a los que se hace referencia en la vista.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en SCHEMA o el permiso CONTROL en OBJECT, y el permiso CREATE VIEW en la base de datos.  
  
##  <a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>Para cambiar el nombre de una vista  
  
1.  En el **Explorador de objetos**, expanda la base de datos que contiene la vista cuyo nombre desea cambiar y, a continuación, expanda la carpeta **Vista** .  
  
2.  Haga clic con el botón derecho en la vista cuyo nombre quiere cambiar y seleccione **Cambiar nombre**.  
  
3.  Escriba el nuevo nombre de la vista.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para cambiar el nombre de una vista**  
  
 Aunque puede usar **sp_rename** para cambiar el nombre de la vista, se recomienda eliminar la vista existente y volver a crearla con el nuevo nombre.  
  
 Para obtener más información, vea [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md) y [DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md).  
  
##  <a name="FollowUp"></a> Seguimiento: Después de cambiar el nombre de una vista  
 Asegúrese de que todos los objetos, scripts y aplicaciones que hacen referencia al nombre antiguo de la vista usan el nombre nuevo.  
  
  
