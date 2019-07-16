---
title: Sys.dm_db_mirroring_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_mirroring_connections
- dm_db_mirroring_connections
- sys.dm_db_mirroring_connections_TSQL
- dm_db_mirroring_connections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_mirroring_connections dynamic management view
ms.assetid: e4df91b6-0240-45d0-ae22-cb2c0d52e0b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 57987f90552897b57e2efe685a9f7ea95152daa9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090950"
---
# <a name="database-mirroring---sysdmdbmirroringconnections"></a>Creación de reflejo: la base de datos sys.dm_db_mirroring_connections
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila para cada conexión establecida para la creación de reflejo de la base de datos.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**connection_id**|**uniqueidentifier**|Identificador de la conexión.|  
|**transport_stream_id**|**uniqueidentifier**|Identificador de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conexión de la interfaz de red (SNI) utilizado por esta conexión para las comunicaciones TCP/IP.|  
|**state**|**smallint**|Estado actual de la conexión. Valores posibles:<br /><br /> 1 = NEW<br /><br /> 2 = CONNECTING<br /><br /> 3 = CONNECTED<br /><br /> 4 = LOGGED_IN<br /><br /> 5 = CERRADA|  
|**state_desc**|**nvarchar(60)**|Estado actual de la conexión. Valores posibles:<br /><br /> NEW<br /><br /> CONNECTING<br /><br /> CONNECTED<br /><br /> LOGGED_IN<br /><br /> CLOSED|  
|**connect_time**|**datetime**|Fecha y hora a la que se inició la conexión.|  
|**login_time**|**datetime**|Fecha y hora a la que se inició una sesión correctamente para la conexión.|  
|**authentication_method**|**nvarchar(128)**|Nombre del método de autenticación de Windows, como por ejemplo NTLM o KERBEROS. Este valor proviene de Windows.|  
|**principal_name**|**nvarchar(128)**|Nombre de inicio de sesión que fue validado para obtener permiso de conexión. En el caso de la autenticación de Windows, este valor es el nombre del usuario remoto. En el caso de autenticación basada en certificados, este valor es el propietario del certificado.|  
|**remote_user_name**|**nvarchar(128)**|Nombre del usuario del mismo nivel en la otra base de datos utilizado por la Autenticación de Windows.|  
|**last_activity_time**|**datetime**|Fecha y hora a la que se utilizó la conexión por última vez para enviar o recibir información.|  
|**is_accept**|**bit**|Indica si la conexión se originó en el lado remoto.<br /><br /> 1 = La conexión es una solicitud aceptada por la instancia remota.<br /><br /> 0 = La conexión fue iniciada por la instancia local.|  
|**login_state**|**smallint**|Estado del proceso de inicio de sesión de esta conexión. Valores posibles:<br /><br /> 0 = INITIAL<br /><br /> 1 = WAIT LOGIN NEGOTIATE<br /><br /> 2 = ONE ISC<br /><br /> 3 = ONE ASC<br /><br /> 4 = TWO ISC<br /><br /> 5 = TWO ASC<br /><br /> 6 = WAIT ISC Confirm<br /><br /> 7 = WAIT ASC Confirm<br /><br /> 8 = WAIT REJECT<br /><br /> 9 = WAIT PRE-MASTER SECRET<br /><br /> 10 = WAIT VALIDATION<br /><br /> 11 = WAIT ARBITRATION<br /><br /> 12 = EN LÍNEA<br /><br /> 13 = ERROR|  
|**login_state_desc**|**nvarchar(60)**|Estado actual del inicio de sesión en el equipo remoto. Valores posibles:<br /><br /> Se está inicializando el protocolo de enlace de la conexión.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de negociación de inicio de sesión.<br /><br /> El protocolo de enlace de la conexión se ha inicializado y ha enviado el contexto de seguridad para la autenticación.<br /><br /> El protocolo de enlace de la conexión ha recibido y aceptado el contexto de seguridad para la autenticación.<br /><br /> El protocolo de enlace de la conexión se ha inicializado y ha enviado el contexto de seguridad para la autenticación. Existe un mecanismo opcional disponible para la autenticación de los elementos del mismo nivel.<br /><br /> El protocolo de enlace de la conexión ha recibido y enviado el contexto de seguridad aceptado para la autenticación. Existe un mecanismo opcional disponible para la autenticación de los elementos del mismo nivel.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de confirmación de inicialización del contexto de seguridad.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de confirmación de aceptación del contexto de seguridad.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de rechazo de SSPI para un error de autenticación.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de secreto maestro preliminar.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de validación.<br /><br /> El protocolo de enlace de la conexión está esperando el mensaje de arbitraje.<br /><br /> El protocolo en enlace de la conexión está completado y en línea (listo) para el intercambio de mensajes.<br /><br /> La conexión tiene errores.|  
|**peer_certificate_id**|**int**|El identificador de objeto local del certificado usado por la instancia remota para la autenticación. El propietario de este certificado debe contar con permiso CONNECT en el extremo de la creación de reflejo de la base de datos.|  
|**encryption_algorithm**|**smallint**|Algoritmo de cifrado utilizado para esta conexión. QUE ACEPTA VALORES NULL. Valores posibles:<br /><br /> **Valor:** 0<br /><br /> **Descripción:** None<br /><br /> **Opción DDL:** Disabled<br /><br /> **Valor:** 1<br /><br /> **Descripción:** RC4<br /><br /> **Opción DDL:** {necesario &#124; necesita el algoritmo RC4}<br /><br /> **Valor:** 2<br /><br /> **Descripción:** AES<br /><br /> **Opción DDL:** Necesita el algoritmo AES<br /><br /> **Valor:** 3<br /><br /> **Descripción:** None, RC4<br /><br /> **Opción DDL:** {admitidas &#124; admite el algoritmo RC4}<br /><br /> **Valor:** 4<br /><br /> **Descripción:** none, AES<br /><br /> **Opción DDL:** Se admite el algoritmo RC4<br /><br /> **Valor:** 5<br /><br /> **Descripción:** RC4, AES<br /><br /> **Opción DDL:** Se necesita el algoritmo RC4 AES<br /><br /> **Valor:** 6<br /><br /> **Descripción:** AES, RC4<br /><br /> **Opción DDL:** Se necesita el algoritmo AES RC4<br /><br /> **Valor:** 7<br /><br /> **Descripción:** NONE, RC4, AES<br /><br /> **Opción DDL:** Admite el algoritmo RC4 AES<br /><br /> **Valor:** 8<br /><br /> **Descripción:** NONE, AES, RC4<br /><br /> **Opción DDL:** Se admite el algoritmo AES RC4<br /><br /> **Nota:** El algoritmo RC4 se admite únicamente por razones de compatibilidad con versiones anteriores. El material nuevo solo se puede cifrar con RC4 o RC4_128 cuando la base de datos tenga el nivel de compatibilidad 90 o 100. (No se recomienda). Use un algoritmo más reciente como uno de los algoritmos AES en su lugar. En [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] y versiones posteriores, el material cifrado con RC4 o RC4_128 se puede descifrar en cualquier nivel de compatibilidad.|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Representación de texto del algoritmo de cifrado. QUE ACEPTA VALORES NULL. Valores posibles:<br /><br /> **Descripción:** None<br /><br /> **Opción DDL:** Disabled<br /><br /> **Descripción:** RC4<br /><br /> **Opción DDL:** {necesario &#124; requiere el algoritmo RC4}<br /><br /> **Descripción:** AES<br /><br /> **Opción DDL:** Necesita el algoritmo AES<br /><br /> **Descripción:** NONE, RC4<br /><br /> **Opción DDL:** {admite &#124; admite el algoritmo RC4}<br /><br /> **Descripción:** NONE, AES<br /><br /> **Opción DDL:** Se admite el algoritmo RC4<br /><br /> **Descripción:** RC4, AES<br /><br /> **Opción DDL:** Requiere el algoritmo RC4 AES<br /><br /> **Descripción:** AES, RC4<br /><br /> **Opción DDL:** Se necesita el algoritmo AES RC4<br /><br /> **Descripción:** NONE, RC4, AES<br /><br /> **Opción DDL:** Admite el algoritmo RC4 AES<br /><br /> **Descripción:** NONE, AES, RC4<br /><br /> **Opción DDL:** Se admite el algoritmo AES RC4|  
|**receives_posted**|**smallint**|Número de recepciones asincrónicas de red que aún no se han completado para esta conexión.|  
|**is_receive_flow_controlled**|**bit**|Determina si se han postergado las recepciones de red debido al control de flujo de la red porque la red está ocupada.<br /><br /> 1 = True|  
|**sends_posted**|**smallint**|El número de envíos asincrónicos de red que aún no se han completado para esta conexión.|  
|**is_send_flow_controlled**|**bit**|Determina si se han postergado los envíos de red debido al control de flujo de la red porque la red está ocupada.<br /><br /> 1 = True|  
|**total_bytes_sent**|**bigint**|Número total de bytes enviados por esta conexión.|  
|**total_bytes_received**|**bigint**|Número total de bytes recibidos por esta conexión.|  
|**total_fragments_sent**|**bigint**|Número total de fragmentos de mensajes de creación de reflejo de la base de datos enviados por esta conexión.|  
|**total_fragments_received**|**bigint**|Número total de fragmentos de mensajes de creación de reflejo de la base de datos recibidos por esta conexión.|  
|**total_sends**|**bigint**|Número total de la red envían solicitudes emitidas por esta conexión.|  
|**total_receives**|**bigint**|Número total de solicitudes de recepción de red emitidas por esta conexión.|  
|**peer_arbitration_id**|**uniqueidentifier**|Identificador interno para el extremo. QUE ACEPTA VALORES NULL.|  
  
## <a name="permissions"></a>Permisos  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="physical-joins"></a>Combinaciones físicas  
 ![combinación para sys.join_dm_db_mirroring_connections](../../relational-databases/system-dynamic-management-views/media/join-dm-db-mirroring-connections.gif "combinación para sys.join_dm_db_mirroring_connections")  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relación  
  
|De|En|Relación|  
|----------|--------|------------------|  
|**dm_db_mirroring_connections.connection_id**|**dm_exec_connections.connection_id**|Uno a uno|  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Supervisar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  
