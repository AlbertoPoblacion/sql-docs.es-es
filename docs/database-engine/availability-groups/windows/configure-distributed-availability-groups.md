---
title: Configuración de un grupo de disponibilidad distribuido
description: 'Se describe cómo crear y configurar un grupo de disponibilidad Always On distribuido. '
ms.custom: seodec18
ms.date: 08/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b311802506ac8d0517026a9258a340e927a10f9
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58566564"
---
# <a name="configure-a-distributed-always-on-availability-group"></a>Configuración de un grupo de disponibilidad Always On distribuido  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Para crear un grupo de disponibilidad distribuido, debe tener dos grupos de disponibilidad, cada uno con su propio agente de escucha. Después, combine estos grupos de disponibilidad en un grupo de disponibilidad distribuido. En los pasos siguientes se proporciona un ejemplo básico de Transact-SQL. Este ejemplo no cubre todos los detalles relativos a cómo crear grupos de disponibilidad y agentes de escucha, sino que se centra en resaltar los requisitos clave.

Para ver una introducción técnica de los grupos de disponibilidad distribuidos, vea [Distributed availability groups](distributed-availability-groups.md) (Grupos de disponibilidad distribuidos).

## <a name="prerequisites"></a>Prerequisites

### <a name="set-the-endpoint-listeners-to-listen-to-all-ip-addresses"></a>Establecer los agentes de escucha de punto de conexión para que escuchen en todas las direcciones IP

Asegúrese de que los puntos de conexión pueden comunicarse entre los diferentes grupos de disponibilidad del grupo de disponibilidad distribuido. Si un grupo de disponibilidad está configurado en una red específica en el punto de conexión, el grupo de disponibilidad distribuido no funcionará correctamente. Establezca el agente de escucha para escuchar en todas las direcciones IP (`LISTENER_IP = ALL`) en cada servidor que hospede una réplica en el grupo de disponibilidad distribuido.

#### <a name="create-a-listener-to-listen-to-all-ip-addresses"></a>Crear un agente de escucha para que escuche en todas las direcciones IP

Por ejemplo, con el siguiente script se crea un punto de conexión de agente de escucha en el puerto TCP 5022 que escucha en todas las direcciones IP.  

```sql
CREATE ENDPOINT [aodns-hadr] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
FOR DATA_MIRRORING (
   ROLE = ALL, 
   AUTHENTICATION = WINDOWS NEGOTIATE,
   ENCRYPTION = REQUIRED ALGORITHM AES
)
GO
```

#### <a name="alter-a-listener-to-listen-to-all-ip-addresses"></a>Modificar un agente de escucha para que escuche en todas las direcciones IP

Por ejemplo, con el siguiente script se cambia un punto de conexión de agente de escucha para que escuche en todas las direcciones IP.  

```sql
ALTER ENDPOINT [aodns-hadr] 
    AS TCP (LISTENER_IP = ALL)
GO
```

## <a name="create-first-availability-group"></a>Crear el primer grupo de disponibilidad

### <a name="create-the-primary-availability-group-on-the-first-cluster"></a>Creación del grupo de disponibilidad principal en el primer clúster  
Cree un grupo de disponibilidad en el primer clúster de conmutación por error de Windows Server (WSFC).   En este ejemplo, el grupo de disponibilidad se denomina `ag1` en la base de datos `db1`. La réplica principal del grupo de disponibilidad principal se conoce como **principal global** en un grupo de disponibilidad distribuido. Servidor1 es el principal global en este ejemplo.        
  
```sql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
>[!NOTE]
>En este ejemplo se emplea la propagación directa, donde el valor **SEEDING_MODE** se establece en **AUTOMATIC** para las réplicas y el grupo de disponibilidad distribuido. En esta configuración, las réplicas secundarias y el grupo de disponibilidad secundario se rellenarán automáticamente sin requerir una copia de seguridad manual y la restauración de la base de datos principal.  
  
### <a name="join-the-secondary-replicas-to-the-primary-availability-group"></a>Unión de las réplicas secundarias al grupo de disponibilidad principal  
Cualquier réplica secundaria debe estar unida al grupo de disponibilidad mediante **ALTER AVAILABILITY GROUP** con la opción **JOIN** . Como en este ejemplo se utiliza la propagación directa, también se debe llamar a  **ALTER AVAILABILITY GROUP** con la opción **GRANT CREATE ANY DATABASE** . De esta forma, el grupo de disponibilidad puede crear la base de datos y comenzar la propagación automáticamente a partir de la réplica principal.  
  
En este ejemplo, se ejecutan los comandos siguientes en la réplica secundaria, `server2`, para unir el grupo de disponibilidad `ag1` . Después, el grupo de disponibilidad puede crear bases de datos en la secundaria.  
  
```sql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  

>[!NOTE]
>Cuando el grupo de disponibilidad crea una base de datos en una réplica secundaria, establece como propietario de la base de datos la cuenta que ha ejecutado la instrucción `ALTER AVAILABILITY GROUP` para conceder permiso para crear una base de datos. Para obtener más información, consulte [Grant create database permission on secondary replica to availability group (Permitir que un grupo de disponibilidad cree bases de datos en réplicas secundarias)](automatic-seeding-secondary-replicas.md#grantCreate).
  
### <a name="create-a-listener-for-the-primary-availability-group"></a>Crear un agente de escucha del grupo de disponibilidad principal  

Luego, agregue un agente de escucha para el grupo de disponibilidad principal del primer WSFC. En este ejemplo, el agente de escucha se denomina " `ag1-listener`". Para obtener instrucciones detalladas sobre cómo crear un agente de escucha, vea [Crear o configurar un agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```sql
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( 
        WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , 
        PORT = 60173);    
GO  
```  
  

## <a name="create-second-availability-group"></a>Crear un segundo grupo de disponibilidad  
 Después, en el segundo WSFC, cree un segundo grupo de disponibilidad, `ag2`. En este caso, no se especifica la base de datos, ya que se propagará automáticamente desde el grupo de disponibilidad principal.  La réplica principal del grupo de disponibilidad secundario se conoce como **reenviador** en un grupo de disponibilidad distribuido. En este ejemplo, servidor3 es el reenviador. 
  
```sql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
> El grupo de disponibilidad secundario debe usar el mismo punto de conexión de creación de reflejo de la base de datos (en este ejemplo, el puerto 5022). En caso contrario, se detendrá la replicación después de una conmutación por error local.  
  
### <a name="join-the-secondary-replicas-to-the-secondary-availability-group"></a>Unión de las réplicas secundarias al grupo de disponibilidad secundario  
 En este ejemplo, se ejecutan los comandos siguientes en la réplica secundaria, `server4`, para unir el grupo de disponibilidad `ag2` . Después, el grupo de disponibilidad puede crear bases de datos en la secundaria con el fin de admitir la propagación directa.  
  
```sql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### <a name="create-a-listener-for--the-secondary-availability-group"></a>Creación de un agente de escucha para el grupo de disponibilidad secundario  
 Después, agregue un agente de escucha para el grupo de disponibilidad secundaria del segundo WSFC. En este ejemplo, el agente de escucha se denomina " `ag2-listener`". Para obtener instrucciones detalladas sobre cómo crear un agente de escucha, vea [Crear o configurar un agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
## <a name="create-distributed-availability-group-on-first-cluster"></a>Crear un grupo de disponibilidad distribuido en el primer clúster  
 En el primer WSFC, cree un grupo de disponibilidad distribuido (denominado " `distributedag` " en este ejemplo). Utilice el comando **CREATE AVAILABILITY GROUP** con la opción **DISTRIBUTED** . El parámetro **AVAILABILITY GROUP ON** especifica los grupos de disponibilidad de los miembros, `ag1` y `ag2`.  
  
```sql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** especifica el agente de escucha de cada grupo de disponibilidad, con el punto de conexión de creación de reflejo de la base de datos del grupo de disponibilidad. En este ejemplo, es el puerto `5022` (no el puerto `60173` usado para crear el agente de escucha). Si usa un equilibrador de carga, por ejemplo, en Azure, [agregue una regla de equilibrio de carga para el puerto del grupo de disponibilidad distribuido](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener#add-load-balancing-rule-for-distributed-availability-group). Agregue la regla al puerto de escucha, además del puerto de la instancia de SQL Server. 
  
## <a name="join-distributed-availability-group-on-second-cluster"></a>Unir el grupo de disponibilidad distribuido en el segundo clúster  
 Después, únase al grupo de disponibilidad distribuido del segundo WSFC.  
  
```sql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

## <a name="failover"></a> Unión a la base de datos de la réplica secundaria del segundo grupo de disponibilidad
Una vez que la base de datos de la réplica secundaria del segundo grupo de disponibilidad se encuentre en un estado de restauración, deberá unirla manualmente al grupo de disponibilidad.

```sql  
ALTER DATABASE [db1] SET HADR AVAILABILITY GROUP = [ag2];   
```
  
## <a name="failover"></a> Conmutación por error de un grupo de disponibilidad secundario  

En estos momentos, solo se admite la conmutación por error manual. Para conmutar por error manualmente un grupo de disponibilidad distribuido:

1. Para asegurarse de que no se pierden datos, establezca el grupo de disponibilidad distribuido en confirmación sincrónica.
1. Espere a que el grupo de disponibilidad distribuido esté sincronizado.
1. En la réplica principal global, establezca el rol del grupo de disponibilidad distribuido en `SECONDARY`.
1. Pruebe la preparación de la conmutación por error.
1. Conmute por error el grupo de disponibilidad principal.

Los ejemplos de Transact-SQL siguientes muestran los pasos detallados para conmutar por error el grupo de disponibilidad distribuido denominado `distributedag`:

1. Establezca el grupo de disponibilidad distribuido en confirmación sincrónica ejecutando el siguiente código *tanto* en el principal global como en el reenviador.   
    
      ```sql  
      -- sets the distributed availability group to synchronous commit 
       ALTER AVAILABILITY GROUP [distributedag] 
       MODIFY 
       AVAILABILITY GROUP ON
       'ag1' WITH 
        ( 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT 
        ), 
        'ag2' WITH  
        ( 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT 
        );
       
       -- verifies the commit state of the distributed availability group
       select ag.name, ag.is_distributed, ar.replica_server_name, ar.availability_mode_desc, ars.connected_state_desc, ars.role_desc, 
       ars.operational_state_desc, ars.synchronization_health_desc from sys.availability_groups ag  
       join sys.availability_replicas ar on ag.group_id=ar.group_id
       left join sys.dm_hadr_availability_replica_states ars
       on ars.replica_id=ar.replica_id
       where ag.is_distributed=1
       GO

      ```  
   >[!NOTE]
   >En los grupos de disponibilidad distribuidos, el estado de sincronización entre dos elementos de réplica de grupos de disponibilidad depende del modo de disponibilidad de ambas réplicas. Para el modo de confirmación sincrónica, tanto el grupo de disponibilidad principal actual como el grupo de disponibilidad secundario actual deben estar configurados en modo de disponibilidad `SYNCHRONOUS_COMMIT`. Por este motivo, debe ejecutar el script anterior en la réplica principal global y en el reenviador.

1. Espere hasta que el estado del grupo de disponibilidad distribuida haya cambiado a `SYNCHRONIZED`. Ejecute la siguiente consulta en el principal global, que es la réplica principal del grupo de disponibilidad principal. 
    
      ```sql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    Continúe después de que el grupo de disponibilidad **synchronization_state_desc** sea `SYNCHRONIZED`. Si **synchronization_state_desc** no es `SYNCHRONIZED`, ejecute el comando cada cinco segundos hasta que cambie. No continúe hasta **synchronization_state_desc** = `SYNCHRONIZED`. 

1. En el principal global, establezca el rol del grupo de disponibilidad distribuido en `SECONDARY`. 

    ```sql
    ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
    ```  

    En este punto, el grupo de disponibilidad distribuido no estará disponible.

1. Pruebe la preparación de la conmutación por error. Ejecute la siguiente consulta:

    ```sql
    SELECT ag.name, 
        drs.database_id, 
        drs.group_id, 
        drs.replica_id, 
        drs.synchronization_state_desc, 
        drs.end_of_log_lsn 
    FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
    WHERE drs.group_id = ag.group_id; 
    ```  
    El grupo de disponibilidad estará preparado para la conmutación por error cuando **synchronization_state_desc** sea `SYNCHRONIZED` y **end_of_log_lsn** sea igual para ambos grupos de disponibilidad. 

1. Conmute por error el grupo de disponibilidad secundario desde el grupo de disponibilidad principal. Ejecute el siguiente comando en SQL Server que hospeda la réplica principal para el grupo de disponibilidad principal. 

    ```sql
    ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
    ```  

    Después de este paso, el grupo de disponibilidad distribuido estará disponible.
      
Después de completar los pasos anteriores, el grupo de disponibilidad distribuido conmuta por error sin pérdida de datos. Si los grupos de disponibilidad se encuentran a una distancia geográfica que provoca latencia, vuelva a establecer el modo de disponibilidad como ASYNCHRONOUS_COMMIT. 
  
## <a name="remove-a-distributed-availability-group"></a>Eliminación de un grupo de disponibilidad distribuido  
 La siguiente instrucción Transact-SQL quita un grupo de disponibilidad distribuido denominado " `distributedag`":  
  
```sql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## <a name="create-distributed-availability-group-on-failover-cluster-instances"></a>Crear un grupo de disponibilidad distribuido en instancias del clúster de conmutación por error

Puede crear un grupo de disponibilidad distribuido mediante un grupo de disponibilidad en una instancia de clúster de conmutación por error (FCI). En este caso, no necesita un agente de escucha del grupo de disponibilidad. Use el nombre de red virtual (VNN) para la réplica principal de la instancia FCI. El ejemplo siguiente muestra un grupo de disponibilidad distribuido llamado SQLFCIDAG. Un grupo de disponibilidad es SQLFCIAG. SQLFCIAG tiene dos réplicas FCI. El VNN para la réplica FCI principal es SQLFCIAG-1 y el VNN para la réplica FCI secundaria es SQLFCIAG-2. El grupo de disponibilidad distribuido también incluye SQLAG-DR, para recuperación ante desastres.

![Grupo de disponibilidad distribuido AlwaysOn](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 El siguiente DDL crea este grupo de disponibilidad distribuido. 

```sql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

La dirección URL del agente de escucha es el VNN de la instancia de FCI principal.

## <a name="manually-fail-over-fci-in-distributed-availability-group"></a>Conmutar por error el FCI manualmente en el grupo de disponibilidad distribuido

Para conmutar por error manualmente el grupo de disponibilidad FCI, actualice el grupo de disponibilidad distribuido para reflejar el cambio de dirección URL del agente de escucha. Por ejemplo, ejecute el siguiente DDL tanto en el grupo de disponibilidad principal como en el grupo de disponibilidad secundario de SQLFCIAG:

```sql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2.contoso.com:5022'
    )
```  
  
## <a name="next-steps"></a>Pasos siguientes

 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
