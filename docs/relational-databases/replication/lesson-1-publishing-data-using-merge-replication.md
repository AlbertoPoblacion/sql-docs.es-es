---
title: "Lección 1: Publicación de datos con la replicación de mezcla | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: c3c6e0b6-54cd-4b7d-8efb-2cefe14fcd7f
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8d2ca2d6dc4c638b38ca353612cef1bda70e457
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-1-publishing-data-using-merge-replication"></a>Lección 1: Publicar datos con la replicación de mezcla
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
En esta lección, creará una publicación de combinación con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para publicar un subconjunto de las tablas **Employee**, **SalesOrderHeader**y **SalesOrderDetail** en la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Estas tablas están filtradas con filtros de fila con parámetros para que cada suscripción contenga una partición única de los datos. También agregará el inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que usa el Agente de mezcla a la lista de acceso a la publicación (PAL). Para realizar este tutorial, es preciso que haya finalizado el anterior, [Preparar el servidor para replicación](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
### <a name="to-create-a-publication-and-define-articles"></a>Para crear publicaciones y definir artículos  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]y luego expanda el nodo del servidor.  
  
2.  Expanda la carpeta **Replicación** , haga clic con el botón derecho en la carpeta **Publicaciones locales**y, después, haga clic en **Nueva publicación**.  
  
    Se iniciará el Asistente para nueva publicación.  
  
3.  En la página Base de datos de publicaciones, seleccione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]y, a continuación, haga clic en **Siguiente**.  
  
4.  En la página Tipo de publicación, seleccione **Publicación de combinación**y, a continuación, haga clic en **Siguiente**.  
  
5.  En la página Tipos de suscriptor, asegúrese de que solo esté seleccionado [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o posterior y, a continuación, haga clic en **Siguiente**.  
  
6.  En la página Artículos, expanda el nodo **Tablas** , seleccione **SalesOrderHeader** y **SalesOrderDetail**, luego expanda **Employee**, seleccione **EmployeeID** o **LoginID**y, a continuación, haga clic en **Siguiente**.  
  
    > [!TIP]  
    > Las columnas necesarias adicionales se seleccionan automáticamente. Seleccione cualquiera de las columnas seleccionadas automáticamente y vea la nota que hay bajo la lista **Objetos que se van a publicar** para obtener una explicación de por qué se necesita la columna.  
  
7.  En la página Filtrar filas de tabla, haga clic en **Agregar** y luego en **Agregar filtro**.  
  
8.  En el cuadro de diálogo **Agregar filtro** , seleccione **Employee (HumanResources)** en **Seleccione la tabla que quiere filtrar**, haga clic en la columna **LoginID** , haga clic en la flecha derecha para agregar la columna a la cláusula WHERE de la consulta del filtro y modifique la cláusula WHERE de la manera siguiente:  
  
    ```  
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
9. Haga clic en **Una fila de esta tabla irá a una sola suscripción**y luego en **Aceptar**  
  
10. En la página **Filtrar filas de tabla** , haga clic en **Employee (Human Resources)**, haga clic en **Agregar** y, después, en **Agregar combinación para ampliar el filtro seleccionado**.  
  
11. En el cuadro de diálogo **Agregar combinación** , seleccione **Sales.SalesOrderHeader** en **Tabla combinada**, haga clic en **Escribir instrucción de combinación manualmente**y complete la instrucción de combinación de la manera siguiente:  
  
    ```  
    ON Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
    ```  
  
12. En **Especifique las opciones de combinación**, seleccione **Clave única**y, a continuación, haga clic en **Aceptar**.  
  
13. En la página Filtrar filas de tabla, haga clic en **SalesOrderHeader**, haga clic en **Agregar**y luego en **Agregar combinación para ampliar el filtro seleccionado**.  
  
14. En el cuadro de diálogo **Agregar combinación** , seleccione **Sales.SalesOrderDetail** en **Tabla combinada**.  
  
15. Haga clic en **Escribir instrucción de combinación manualmente**.  
  
16. En **Columnas de la tabla filtrada**, seleccione **BusinessEntityID**y haga clic en el botón de flecha para copiar el nombre de columna a la instrucción de combinación.  
  
17. En el cuadro **Instrucción de combinación** , complete la instrucción de combinación de la manera siguiente:  
  
    ```  
    ON Employee.BusinessEntityID = SalesOrderHeader.SalesPersonID  
    ```  
  
18. En **Especifique las opciones de combinación**, seleccione **Clave única**y, a continuación, haga clic en **Aceptar**.  
  
19. En la página **Filtrar filas de tabla** , haga clic en **SalesOrderHeader (Sales)**, haga clic en **Agregar**y, después, en **Agregar combinación para ampliar el filtro seleccionado**.  
  
20. En el cuadro de diálogo **Agregar combinación** , seleccione **Sales.SalesOrderDetail** en **Tabla combinada**, haga clic en **Aceptar**y luego en **Siguiente**.  
  
21. Seleccione **Crear una instantánea inmediatamente**, desactive **Programar el Agente de instantáneas para ejecutarse**y, a continuación, haga clic en **Siguiente**.  
  
22. En la página Seguridad del agente, haga clic en **Configuración de seguridad**, escriba \<*Nombre_De_Equipo>***\repl_snapshot** en el cuadro **Cuenta de proceso**, escriba la contraseña de la cuenta y haga clic en **Aceptar**. Haga clic en **Finalizar**.  
  
23. En la página Finalización del asistente, escriba **AdvWorksSalesOrdersMerge** en el cuadro **Nombre de publicación** y, a continuación, haga clic en **Finalizar**.  
  
24. Una vez creada la publicación, haga clic en **Cerrar**.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Para ver el estado de la generación de instantáneas  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda el nodo del servidor y luego la carpeta **Replicación** .  
  
2.  En la carpeta Publicaciones locales, haga clic con el botón derecho en **AdvWorksSalesOrdersMerge**y luego haga clic en **Ver estado del Agente de instantáneas**.  
  
3.  Se muestra el estado actual del trabajo del Agente de instantáneas para la publicación. Compruebe que el trabajo de instantáneas sea correcto antes de continuar con la siguiente lección.  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>Para agregar el inicio de sesión del Agente de mezcla para la lista de acceso de la publicación (PAL)  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda el nodo del servidor y luego la carpeta **Replicación** .  
  
2.  En la carpeta Publicaciones locales, haga clic con el botón derecho en **AdvWorksSalesOrdersMerge**y luego haga clic en **Propiedades**.  
  
    Se mostrará el cuadro de diálogo **Propiedades de la publicación** .  
  
3.  Seleccione la página **Lista de acceso a la publicación** y haga clic en **Agregar**.  
  
4.  En el cuadro de diálogo Agregar acceso de publicación, seleccione *<Nombre_De_Equipo>***\repl_merge** y haga clic en **Aceptar**. Haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Next Steps  
Ha creado correctamente la publicación de combinación. A continuación se suscribirá a esta publicación. Consulte la [Lección 2: Crear una suscripción a la publicación de combinación](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Ver también  
[Filtrar datos publicados](../../relational-databases/replication/publish/filter-published-data.md)  
[Filtros de fila con parámetros](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
[Definir un artículo](../../relational-databases/replication/publish/define-an-article.md)  
  
  
  
