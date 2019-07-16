---
title: Sys.dm_hadr_availability_replica_states (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_availability_replica_states
- sys.dm_hadr_availability_replica_states_TSQL
- sys.dm_hadr_availability_replica_states
- dm_hadr_availability_replica_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_replica_states dynamic management view
ms.assetid: d2e678bb-51e8-4a61-b223-5c0b8d08b8b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 05964e0557cb08e874424af542b8fc8a57ce0835
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900624"
---
# <a name="sysdmhadravailabilityreplicastates-transact-sql"></a>sys.dm_hadr_availability_replica_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila para cada réplica local y una fila para cada réplica remota en el mismo grupo de disponibilidad Always On que una réplica local. Cada fila contiene información sobre el estado de una réplica determinada.  
  
> [!IMPORTANT]  
>  Para obtener información acerca de cada réplica en un grupo de disponibilidad determinado, consulte **sys.dm_hadr_availability_replica_states** en la instancia del servidor que hospeda la réplica principal. Cuando se consulta en una instancia de servidor que hospeda una réplica secundaria de un grupo de disponibilidad, esta vista de administración dinámica devuelve solo información local para el grupo de disponibilidad.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Identificador único de la réplica.|  
|**group_id**|**uniqueidentifier**|Identificador único del grupo de disponibilidad.|  
|**is_local**|**bit**|Si la réplica es local, uno de:<br /><br /> 0 = Indica una réplica secundaria remota en un grupo de disponibilidad cuya réplica principal está hospedada en la instancia del servidor local. Este valor solo se produce en la ubicación de la réplica principal.<br /><br /> 1 = indica una réplica local. En las réplicas secundarias, es el único valor disponible para el grupo de disponibilidad al que pertenece la réplica.|  
|**role**|**tinyint**|Actual [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] rol de una réplica local o una réplica remota conectada, uno de:<br /><br /> 0 = Resolver<br /><br /> 1 = Principal<br /><br /> 2 = Secundario<br /><br /> Para obtener más información sobre los roles de [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], vea [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).|  
|**role_desc**|**nvarchar(60)**|Descripción de **rol**, uno de:<br /><br /> RESOLVING<br /><br /> PRIMARY<br /><br /> SECONDARY|  
|**operational_state**|**tinyint**|Estado operativo actual de la réplica, uno de:<br /><br /> 0 = pendiente de conmutación por error<br /><br /> 1 = pendiente<br /><br /> 2 = en línea<br /><br /> 3 = sin conexión<br /><br /> 4 = Error<br /><br /> 5 = No se pudo establecer quórum<br /><br /> NULL = La réplica no es local.<br /><br /> Para obtener más información, consulte [Roles y estados operativos](#RolesAndOperationalStates), más adelante en este tema.|  
|**operativa\_estado\_desc**|**nvarchar(60)**|Descripción de **operativa\_estado**, uno de:<br /><br /> PENDING_FAILOVER<br /><br /> PENDING<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> FAILED<br /><br /> FAILED_NO_QUORUM<br /><br /> NULL|  
|**recuperación\_mantenimiento**|**tinyint**|Paquete acumulativo de actualizaciones de la **base de datos\_estado** columna de la [sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) vista de administración dinámica. Los siguientes son los valores posibles y sus descripciones.<br /><br /> 0: En curso.  Al menos una base de datos combinada y tiene un estado de la base de datos distinto de ONLINE (**base de datos\_estado** es no 0).<br /><br /> 1: en línea. Todas las bases de datos unidas tienen un estado de la base de datos de en línea (**database_state** es 0).<br /><br /> NULL: **is_local** = 0|  
|**recovery_health_desc**|**nvarchar(60)**|Descripción de **recovery_health**, uno de:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**sincronización\_mantenimiento**|**tinyint**|Refleja un resumen del estado de sincronización de base de datos (**synchronization_state**) de todos los unido las bases de datos de disponibilidad (también conocido como *réplicas*) y el modo de disponibilidad de la réplica () modo confirmación sincrónica o asincrónica). La acumulación reflejará el estado acumulado menos correcto las bases de datos en la réplica. A continuación se muestran los valores posibles y sus descripciones.<br /><br /> 0: No es correcto.   El estado de al menos una de las bases de datos unidas es NOT SYNCHRONIZING.<br /><br /> 1: Parcialmente correcto. Algunas réplicas no están en el estado de sincronización del destino: las réplicas de confirmación sincrónica deben ser sincronizadas y las réplicas de confirmación asincrónica deberían estar sincronizándose.<br /><br /> 2: En buen estado. Todas las réplicas están en el estado de sincronización del destino: las réplicas de confirmación sincrónica se sincronizan y las réplicas de confirmación asincrónica se están sincronizando.|  
|**synchronization_health_desc**|**nvarchar(60)**|Descripción de **synchronization_health**, uno de:<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**connected_state**|**tinyint**|Si una réplica secundaria está actualmente conectado a la réplica principal. Los valores posibles se muestran a continuación con sus descripciones.<br /><br /> 0: Desconectado La respuesta de una réplica de disponibilidad al estado DISCONNECTED depende de su rol: En la réplica principal, si una réplica secundaria está desconectada, sus bases de datos secundarias se marcan como NOT SYNCHRONIZED en la réplica principal, que espera a que la base de datos secundaria volver a conectar; En una réplica secundaria, cuando detecta que está desconectada, la réplica secundaria intenta volver a conectarse a la réplica principal.<br /><br /> 1: Conectado.<br /><br /> Cada réplica principal realiza un seguimiento del estado de conexión de cada réplica secundaria en el mismo grupo de disponibilidad. Las réplicas secundarias realizan un seguimiento del estado de solo la réplica principal.|  
|**connected_state_desc**|**nvarchar(60)**|Descripción de **connection_state**, uno de:<br /><br /> DISCONNECTED<br /><br /> CONNECTED|  
|**last_connect_error_number**|**int**|Número del último error de conexión.|  
|**last_connect_error_description**|**nvarchar(1024)**|Texto de la **last_connect_error_number** mensaje.|  
|**last_connect_error_timestamp**|**datetime**|Marca de tiempo de fecha y hora que indica cuándo el **last_connect_error_number** se produjo el error.|  
  
##  <a name="RolesAndOperationalStates"></a> Roles y estados operativos  
 El rol, **rol**, refleja el estado de una réplica de disponibilidad determinado y el estado operativo, **operational_state**, describe si la réplica está preparada procesar las solicitudes de cliente para todos los base de datos de la réplica de disponibilidad. Este es un resumen de los Estados operativos que son posibles para cada rol: RESOLVING, principal y secundario.  
  
 **RESOLUCIÓN:** Cuando una réplica de disponibilidad está en el rol RESOLVING, los Estados operativos posibles son como se muestra en la tabla siguiente.  
  
|Estado operativo|Descripción|  
|-----------------------|-----------------|  
|PENDING_FAILOVER|Se procesa un comando de conmutación por error para el grupo de disponibilidad.|  
|OFFLINE|Todos los datos de configuración para la réplica de disponibilidad se han actualizado en el clúster de WSFC y, además, en los metadatos locales, pero el grupo de disponibilidad no tiene actualmente una réplica principal.|  
|FAILED|Se ha producido un error de lectura al intentar recuperar información del clúster de WSFC.|  
|FAILED_NO_QUORUM|El nodo WSFC local no tiene quórum. Es un estado deducido.|  
  
 **PRINCIPAL:** Cuando una réplica de disponibilidad está realizando el rol principal, es actualmente la réplica principal. Los posibles estados operativos son como se muestra en la tabla siguiente.  
  
|Estado operativo|Descripción|  
|-----------------------|-----------------|  
|PENDING|Es un estado transitorio, pero una réplica principal se puede bloquear en este estado si los subprocesos de trabajo no están disponibles para procesar las solicitudes.|  
|ONLINE|El recurso de grupo de disponibilidad está en línea, y todos los subprocesos de trabajo de la base de datos se han seleccionado.|  
|FAILED|La réplica de disponibilidad no puede leer ni escribir en el clúster de WSFC.|  
  
 **BASE DE DATOS SECUNDARIA:** Cuando una réplica de disponibilidad está realizando el rol secundario, es actualmente una réplica secundaria. Los Estados operativos posibles son como se muestra en la tabla siguiente.  
  
|Estado operativo|Descripción|  
|-----------------------|-----------------|  
|ONLINE|La réplica secundaria local no está conectada a la réplica principal.|  
|FAILED|La réplica secundaria local no puede leer ni escribir en el clúster de WSFC.|  
|NULL|En una réplica principal, se devuelve este valor cuando la fila está relacionada con una réplica secundaria.|  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permisos  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Supervisar grupos de disponibilidad &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
