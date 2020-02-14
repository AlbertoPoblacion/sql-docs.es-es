---
title: Replicación de cambios de esquema | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 956ce42f5fc4d9d367e496b4ff3f22f0c6ee24da
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287593"
---
# <a name="replicate-schema-changes"></a>Replicar cambios de esquema
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  En este tema se describe cómo replicar cambios de esquema en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Si realiza los siguientes cambios de esquema en un artículo publicado, se propagan de forma predeterminada a los suscriptores de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
-   **Para replicar cambios de esquema con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   La instrucción ALTER TABLE … DROP COLUMN siempre se replica en todos los suscriptores cuya suscripción contenga las columnas que se van a quitar, aunque deshabilite la replicación de cambios de esquema.  
  
##  <a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
 Si no quiere replicar los cambios de esquema para una publicación, deshabilite la replicación de cambios de esquema en el cuadro de diálogo **Propiedades de la publicación: \<publicación>** . Para obtener más información sobre el acceso a este cuadro de diálogo, vea [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-disable-replication-of-schema-changes"></a>Para deshabilitar la replicación de los cambios de esquema  
  
1.  En la página **Opciones de suscripción** del cuadro de diálogo **Propiedades de la publicación: \<publicación>** , establezca el valor de la propiedad **Replicar cambios de esquema** en **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

     Para propagar únicamente los cambios de esquema específicos, establezca la propiedad en **True** antes de un cambio de esquema y vuelva a establecerla en **False** después de realizar el cambio. A la inversa, para propagar la mayoría de los cambios de esquema, excepto un cambio determinado, establezca la propiedad en **False** antes de un cambio de esquema y vuelva a establecerla en **True** después de realizar el cambio.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 Puede utilizar los procedimientos almacenados de replicación para especificar si se replican estos cambios de esquema. El procedimiento almacenado que utiliza depende del tipo de publicación.  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>Para crear una instantánea o una publicación transaccional que no replique cambios de esquema  
  
1.  En el publicador de la base de datos de publicación, ejecute [sp_addpublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) y especifique un valor de `0` para `@replicate_ddl`. Para obtener más información, vea [Crear una suscripción](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>Para crear una publicación de combinación que no replique cambios de esquema  
  
1.  En el publicador de la base de datos de publicación, ejecute [sp_addmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) y especifique un valor de `0` para `@replicate_ddl`. Para obtener más información, vea [Crear una suscripción](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>Para deshabilitar temporalmente la replicación de cambios de esquema para una instantánea o una publicación transaccional  
  
1.  Para una publicación con replicación de cambios de esquema, ejecute [sp_changepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) y especifique un valor de `replicate_ddl` para `@property` y un valor de `0` para `@value`.  
  
2.  Ejecute el comando DDL en el objeto publicado.  
  
3.  (Opcional) Vuelva a habilitar la replicación de cambios de esquema mediante la ejecución de [sp_changepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) y especifique un valor de `replicate_ddl` para `@property` y un valor de `1` para `@value`.  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>Para deshabilitar temporalmente la replicación de cambios de esquema para una publicación de combinación  
  
1.  Para una publicación con replicación de cambios de esquema, ejecute [sp_changemergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) y especifique un valor de `replicate_ddl` para `@property` y un valor de `0` para `@value`.  
  
2.  Ejecute el comando DDL en el objeto publicado.  
  
3.  (Opcional) Vuelva a habilitar la replicación de cambios de esquema mediante la ejecución de [sp_changemergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) y especifique un valor de `replicate_ddl` para `@property` y un valor de `1` para `@value`.  
  
## <a name="see-also"></a>Consulte también  
 [Realizar cambios de esquema en bases de datos de publicaciones](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Realizar cambios de esquema en bases de datos de publicaciones](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
