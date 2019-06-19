---
title: Configurar propiedades de instantáneas (programación de la replicación con Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b454197982685882610fc808d9319835053e21bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62661095"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>Configurar propiedades de instantáneas (programación de la replicación con Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Las propiedades de las instantáneas se pueden definir y modificar mediante programación usando procedimientos almacenados de replicación, los cuales dependerán del tipo de publicación.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>Para configurar propiedades de instantáneas al crear una instantánea o una publicación transaccional  
  
1.  En el publicador, ejecute [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Especifique un nombre de publicación para **@publication** , el valor **snapshot** o **continuous** para **@repl_freq** y uno o más de los siguientes parámetros relacionados con instantáneas:  
  
    -   **@alt_snapshot_folder** - especifique una ruta si a la instantánea de esta publicación se tiene acceso desde esa ubicación en lugar o además de desde la carpeta predeterminada para instantáneas.    
    -   **@compress_snapshot** - especifique el valor **true** si los archivos de instantáneas de la carpeta de instantáneas están comprimidos en el formato de archivo CAB de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .    
    -   **@pre_snapshot_script** - especifique el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **@post_snapshot_script** - especifique el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **@snapshot_in_defaultfolder** - especifique el valor **false** si la instantánea únicamente está disponible en una ubicación que no es la predeterminada.  
  
     Para obtener más información acerca de la creación de publicaciones, vea [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>Para configurar propiedades de instantáneas al crear una publicación de combinación  
  
1.  En el publicador, ejecute [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Especifique un nombre de publicación para **@publication** , el valor **snapshot** o **continuous** para **@repl_freq** y uno o más de los siguientes parámetros relacionados con instantáneas:  
  
    -   **@alt_snapshot_folder** - especifique una ruta si a la instantánea de esta publicación se tiene acceso desde esa ubicación en lugar o además de desde la carpeta predeterminada para instantáneas.    
    -   **@compress_snapshot** - especifique el valor **true** si los archivos de instantáneas de la carpeta de instantáneas están comprimidos en el formato de archivo CAB.   
    -   **@pre_snapshot_script** - especifique el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **@post_snapshot_script** - especifique el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **@snapshot_in_defaultfolder** - especifique el valor **false** si la instantánea únicamente está disponible en una ubicación que no es la predeterminada.  
  
2.  Para obtener más información acerca de la creación de publicaciones, vea [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>Para modificar las propiedades de instantánea de una instantánea o de una publicación transaccional existente  
  
1.  En la base de datos de publicación del publicador, ejecute [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Especifique el valor **1** para **@force_invalidate_snapshot** y uno de los valores siguientes para **@property** :  
  
    -   **alt_snapshot_folder** - especifique también una nueva ruta a la carpeta de instantáneas alternativa para **@value** .    
    -   **compress_snapshot** - especifique también el valor **true** o **false** para **@value** para indicar si los archivos de instantáneas de la carpeta de instantáneas alternativa están comprimidos en el formato de archivo CAB.    
    -   **pre_snapshot_script** - especifique también para **@value** el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **post_snapshot_script** - especifique también para **@value** el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **snapshot_in_defaultfolder** - especifique también el valor **true** o **false** para indicar si la instantánea está disponible únicamente en una ubicación que no es la predeterminada.  
  
2.  (Opcional) En la base de datos de publicación del publicador, ejecute [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md). Especifique **@publication** y uno o más de los parámetros de credenciales de seguridad o de programación que se están cambiando.  
  
    > [!IMPORTANT]  
    >  Cuando sea posible, pida a los usuarios que proporcionen credenciales de seguridad en tiempo de ejecución. Si debe almacenar las credenciales en un archivo de script, proteja el archivo para evitar el acceso no autorizado.  
  
3.  Ejecute el [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) desde el símbolo del sistema o inicie el trabajo del Agente de instantáneas para generar una nueva instantánea. Para más información, consulte [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>Para modificar las propiedades de instantánea de una publicación de combinación existente  
  
1.  En la base de datos de publicación del publicador, ejecute [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Especifique el valor **1** para **@force_invalidate_snapshot** y uno de los valores siguientes para **@property** :  
  
    -   **alt_snapshot_folder** - especifique también una nueva ruta a la carpeta de instantáneas alternativa para **@value** .    
    -   **compress_snapshot** - especifique también el valor **true** o **false** para **@value** para indicar si los archivos de instantáneas de la carpeta de instantáneas alternativa están comprimidos en el formato de archivo CAB.    
    -   **pre_snapshot_script** - especifique también para **@value** el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **post_snapshot_script** - especifique también para **@value** el nombre de archivo y la ruta completa de un archivo **.sql** que se ejecutará en el suscriptor durante la inicialización antes de que se aplique la instantánea inicial.    
    -   **snapshot_in_defaultfolder** - especifique también el valor **true** o **false** para indicar si la instantánea está disponible únicamente en una ubicación que no es la predeterminada.  
  
2.  Ejecute el [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) desde el símbolo del sistema o inicie el trabajo del Agente de instantáneas para generar una nueva instantánea. Para más información, consulte [Crear y aplicar la instantánea inicial](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se crea una publicación que usa una carpeta de instantáneas alternativa y una instantánea comprimida.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## <a name="see-also"></a>Consulte también  
 [Modificación de las opciones de instantánea](../../../relational-databases/replication/snapshot-options.md)   
 [Ejecutar scripts antes y después de aplicar la instantánea](../../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Transferir instantáneas mediante FTP](../../../relational-databases/replication//publish/deliver-a-snapshot-through-ftp.md)   
 [Cambiar las propiedades de la publicación y de los artículos](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  
