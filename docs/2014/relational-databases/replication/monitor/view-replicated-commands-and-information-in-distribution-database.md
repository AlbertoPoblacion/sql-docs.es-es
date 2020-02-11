---
title: Ver comandos replicados y otra información en la base de datos de distribución (programación de la replicación con Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86ced6fd281da2e47ddaa31cab7fa977767b98d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "74164952"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a>Ver comandos replicados y otra información en la base de datos de distribución (programación de la replicación con Transact-SQL)
  Al utilizar la replicación transaccional, los comandos de transacción están almacenados en la base de datos de distribución hasta que el Agente de distribución los propaga a todos los suscriptores o un Agente de distribución del suscriptor extrae los cambios. Estos comandos pendientes en la base de datos de distribución se pueden ver utilizando mediante programación los procedimientos almacenados de replicación. Para obtener más información, consulte [Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) (Procedimientos almacenados de replicación [Transact-SQL]).  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>Para ver los comandos replicados de todas las publicaciones transaccionales en la base de datos de distribución  
  
1.  En cualquier base de datos de distribución, ejecute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>Para ver los comandos replicados en la base de datos de distribución de un artículo concreto o de una base de datos concreta publicada utilizando replicación transaccional  
  
1.  (Opcional) En la base de datos de publicación del publicador, ejecute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql). Especifique ** \@la publicación** y ** \@el artículo**. Anote el valor de **article** del conjunto de resultados.  
  
2.  En cualquier base de datos de distribución, ejecute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql). Opta Especifique el ID. del artículo del paso 2 para ** \@article_id**. Opta Especifique el identificador de la base de datos de publicación para ** \@publisher_database_id**, que se puede obtener de la columna **database_id** de la vista de catálogo [Sys. Databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar la replicación mediante programación](../monitoring-replication.md)  
  
  
