---
title: "Lección 2: Preparación de la carpeta de instantáneas | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 522114a937e18b825b8c9349aa434e1fd892d620
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>Lección 2: Preparar la carpeta de instantáneas
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
En esta lección aprenderá a configurar la carpeta de instantáneas que se utiliza para crear y almacenar la instantánea de publicación.  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>Para crear un recurso compartido para la carpeta de instantáneas y asignar permisos  
  
1.  En el Explorador de Windows, navegue a la carpeta de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La ubicación predeterminada es C:\Archivos de programa\Microsoft SQL Server\MSSQL.X\MSSQL\Data.  
  
2.  Cree una carpeta con el nombre **repldata**.  
  
3.  Haga clic con el botón derecho en esta carpeta y haga clic en **Propiedades**.  
  
4.  En la pestaña **Compartir** del cuadro de diálogo **Propiedades de repldata** , haga clic en **Compartir**.  
  
5.  En el cuadro de diálogo **Uso compartido de archivos** , haga clic en **Compartir**y luego en **Listo**.  
  
6.  En la pestaña **Seguridad** , haga clic en **Editar**.  
  
7.  En el cuadro de diálogo **Permisos** , haga clic en **Agregar**. En el cuadro de texto **Select User, Computers, Service Account, or Groups** (Seleccionar usuario, equipos, cuenta de servicio o grupos), escriba el nombre de la cuenta del agente de instantáneas creado en la lección 1, como \<*Nombre_De_Equipo>***\repl_snapshot**, donde \<*nombre_de_equipo>* es el nombre del publicador. Haga clic en **Comprobar nombres**y luego en **Aceptar**.  
  
8.  Repita el paso anterior para agregar permisos para el Agente de distribución, por ejemplo \<*Nombre_De_Equipo>***\repl_distribution**, y para el Agente de mezcla, por ejemplo \<*Nombre_De_Equipo>***\repl_merge**.  
  
9. Compruebe que se admiten los siguientes permisos:  
  
    -   repl_snapshot - Control total  
  
    -   repl_distribution - Lectura  
  
    -   repl_merge - Lectura  
  
10. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Propiedades de repldata** y crear el recurso compartido repldata.  
  
## <a name="next-steps"></a>Next Steps  
Ha configurado correctamente el recurso compartido para la carpeta de instantáneas. A continuación configurará la distribución. Consulte [Lección 3: Configurar la distribución](../../relational-databases/replication/lesson-3-configuring-distribution.md).  
  
## <a name="see-also"></a>Ver también  
[Proteger la carpeta de instantáneas](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
  
