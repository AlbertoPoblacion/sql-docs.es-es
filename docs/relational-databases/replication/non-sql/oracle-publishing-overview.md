---
title: Información general de la publicación de Oracle | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7814090b688f362737e7cd045bca9edd32c34bcb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883630"
---
# <a name="oracle-publishing-overview"></a>Oracle Publishing Overview  
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

A partir de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], puede incluir Publicadores de Oracle en su topología de replicación, empezando por Oracle versión 9i. Los servidores de publicación se pueden implementar en cualquier hardware y sistema operativo admitido por Oracle. La característica se ha creado sobre la sólida base de la replicación transaccional y la replicación de instantáneas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , lo que proporciona un rendimiento y una capacidad de uso similares.  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] admite los siguientes escenarios heterogéneos para la replicación de instantáneas y transaccional:  
  
-   Publicar datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en suscriptores que no son de[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   La publicación de datos en y desde Oracle tiene las siguientes restricciones:  

  |       | 2016 o anterior |2017 o posterior |
  |-------|-------|--------|
  |Replicación de Oracle |Compatibilidad solo con Oracle 10g o versiones anteriores |Compatibilidad solo con Oracle 10g o versiones anteriores |
  |Replicación en Oracle |Hasta Oracle 12c |No compatible |


 La replicación heterogénea en suscriptores que no son SQL Server está desusada. La publicación de Oracle está desusada. Para mover datos, cree soluciones mediante captura de datos modificados y [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  

  
## <a name="snapshot-replication-for-oracle"></a>Replicación de instantáneas en Oracle  
 Las publicaciones de instantáneas de Oracle se implementan de manera similar a las publicaciones de instantáneas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Cuando se ejecuta en una publicación de Oracle, el Agente de instantáneas conecta al publicador de Oracle y procesa cada tabla de la publicación. Cuando se procesa cada tabla, el agente recupera las filas de la tabla y crea scripts del esquema, que a continuación se almacenan en el recurso compartido de instantáneas de la publicación. Todo el conjunto de datos se crea cada vez que se ejecuta el Agente de instantáneas, por lo que el cambio en los desencadenadores de seguimiento no se agrega a las tablas de Oracle como sucede con la replicación transaccional. La replicación de instantáneas proporciona una manera cómoda de migrar datos con el mínimo impacto en el sistema de publicación.  
  
## <a name="transactional-replication-for-oracle"></a>Replicación transaccional en Oracle  
 Las publicaciones transaccionales de Oracle se implementan usando la arquitectura de publicación transaccional de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; no obstante, el seguimiento de los cambios se realiza mediante una combinación de desencadenadores de base de datos en la base de datos de Oracle y en el Agente de registro del LOG. Los suscriptores de una publicación transaccional de Oracle se inicializan automáticamente con la replicación de instantáneas; se realiza el seguimiento de los cambios subsiguientes y se entregan a los suscriptores cuando se producen mediante el Agente de registro del LOG.  
  
 Cuando se crea una publicación de Oracle, se crean los desencadenadores y las tablas de seguimiento para cada tabla publicada en la base de datos de Oracle. Cuando se realizan cambios en las tablas publicadas, los desencadenadores de la base de datos de las tablas se activan e insertan información en las tablas de seguimiento de la replicación de cada fila modificada. A continuación, el Agente de registro del LOG en el distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mueve la información de los cambios de datos de las tablas de seguimiento a la base de datos de distribución en el distribuidor. Finalmente, como sucede en la replicación transaccional estándar, el Agente de distribución mueve los cambios del distribuidor a los suscriptores.  
  
## <a name="see-also"></a>Consulte también  
 [Configurar un publicador de Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Glosario de términos de publicaciones de Oracle](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Replicación de bases de datos heterogéneas](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
