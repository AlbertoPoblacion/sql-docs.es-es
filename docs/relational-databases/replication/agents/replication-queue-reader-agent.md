---
title: Agente de lectura de cola de replicación | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c3dacfe725541c93f3d5fe1276513423d77aeba9
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81529399"
---
# <a name="replication-queue-reader-agent"></a>Agente de lectura de cola de replicación
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El Agente de lectura de cola de replicación es un ejecutable que lee los mensajes almacenados en una cola de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o una cola de mensajes [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Message Queue y luego aplica esos mensajes al publicador. El Agente de lectura de cola se utiliza con la instantánea y las publicaciones transaccionales que permiten la actualización en cola.  
  
> [!NOTE]  
>  Los parámetros se pueden especificar en cualquier orden. Cuando no se especifican parámetros opcionales, se utilizan valores predefinidos basados en el perfil de agente predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFile definition_file]  
[-Distributor server_name[\instance_name]]  
[-DistributionDB distribution_database]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOut login_time_out_seconds]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingInterval polling_interval]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-ProfileName agent_profile_name]  
[-QueryTimeOut query_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a>Argumentos  
 **-?**  
 Muestra información de uso.  
  
 **-Continuous**  
 Especifica si el agente intenta procesar continuamente las transacciones en cola. Si se especifica, el agente continúa la ejecución incluso si no hay transacciones en cola pendientes de cualquiera de los suscriptores.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Es la ruta de acceso del archivo de definición de agente. Un archivo de definición de agente contiene los argumentos de línea de comandos para el agente. El contenido del archivo se analiza como un archivo ejecutable. Utilice las comillas tipográficas (") para especificar valores de argumento que contienen caracteres arbitrarios.  
  
 **-Distributor** _server_name_[ **\\** _instance_name_]  
 Es el nombre del distribuidor. Especifique *server_name* para conectarse a la instancia predeterminada del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor. Especifique *server_name*\\*instance_name* para una instancia con nombre de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en ese servidor. Si no se especifica, el nombre tiene como valor predeterminado el nombre de la instancia predeterminada de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en el equipo local.  
  
 **-DistributionDB** _distribution_database_  
 Es la base de datos de distribución.  
  
 **-DistributorLogin** _distributor_login_  
 Es el nombre de inicio de sesión del distribuidor.  
  
 **-DistributorPassword** _distributor_password_  
 Es la contraseña del distribuidor.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Especifica el modo de seguridad del distribuidor. Un valor de **0** hace referencia a la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (valor predeterminado) y un valor de **1** hace referencia al modo de autenticación de Windows.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Es el nivel de cifrado de la Seguridad de la capa de transporte (TLS), conocida anteriormente como Capa de sockets seguros (SSL), utilizado por el Agente de lectura de cola cuando realiza conexiones.  
  
|Valor de EncryptionLevel|Descripción|  
|---------------------------|-----------------|  
|**0**|Especifica que no se utiliza TLS.|  
|**1**|Especifica que se utiliza TLS, pero el agente no comprueba que un emisor confiable haya firmado el certificado del servidor TLS/SSL.|  
|**2**|Especifica que se usa TLS y que se ha comprobado el certificado.|  

 > [!NOTE]  
 >  Un certificado TLS/SSL válido se define con un nombre de dominio completo de SQL Server. Para que el agente se conecte correctamente al establecer -EncryptionLevel en 2, cree un alias en la instancia local de SQL Server. El parámetro "Alias Name" debe ser el nombre del servidor, mientras que el parámetro "Server" debe establecerse en el nombre completo de la instancia de SQL Server.
  
 Para más información, consulte [Ver y modificar la configuración de seguridad de la replicación](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 Especifica la cantidad de historial registrado durante una operación del lector de cola. Puede minimizar el efecto sobre el rendimiento del registro del historial seleccionando **1**.  
  
|Valor HistoryVerboseLevel|Descripción|  
|-------------------------------|-----------------|  
|**0**|Ningún registro del historial (no se recomienda).|  
|**1**|Predeterminada. Siempre actualiza un mensaje del historial anterior del mismo estado (inicio, progreso, éxito, etc.). Si no existe ningún registro anterior con el mismo estado, inserta un nuevo registro.|  
|**2**|Inserte nuevos registros del historial, incluso mensajes inactivos o mensajes del trabajo de ejecución prolongada.|  
|**3**|Inserte nuevos registros de historial que incluyen detalles adicionales que pueden ser útiles para solucionar problemas.|  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Es el número de segundos antes de que el inicio de sesión exceda el tiempo de espera. El valor predeterminado es 15 segundos.  
  
 **-Output** _output_path_and_file_name_  
 Es la ruta de acceso del archivo de salida del agente. Si no se proporciona un nombre de archivo, el resultado se envía a la consola. Si el nombre de archivo especificado existe, el resultado se anexa al archivo.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Especifica si el resultado debería ser detallado. Si el nivel detallado es **0**, solo se imprimen los mensajes de error. Si el nivel detallado es **1**, se imprimen todos los mensajes del informe de progreso. Si el nivel detallado es **2** (valor predeterminado), se imprimen todos los mensajes de error y mensajes del informe de progreso, lo que es útil para la depuración.  
  
 **-PollingInterval** _polling_interval_  
 Solo es pertinente para actualizar las suscripciones que utilizan colas basadas en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Especifica la frecuencia, en segundos, con la que se sondea la cola [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] las transacciones en cola pendientes. El valor puede estar comprendido entre 0 y 240 segundos. El valor predeterminado es 5 segundos.  
  
 **-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]  
 Especifica la instancia del asociado de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que participa en una sesión de creación de reflejo de la base de datos con la base de datos de publicación. Para obtener más información, vea [Replicación y creación de reflejo de la base de datos &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-ProfileName** _agent_profile_name_  
 Es el nombre de un perfil de agente utilizado para proporcionar un conjunto de valores predeterminados al agente. Para obtener información, vea [Perfiles del Agente de replicación](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Es el número de segundos antes de que la consulta exceda el tiempo de espera. El valor predeterminado es 1800 segundos.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Especifica cómo se resuelven los conflictos de actualización en cola. Un valor de **1** indica que el Publicador gana el conflicto, y la transacción en cola actual que está en conflicto se revertirá en el Publicador y el Suscriptor que originó la actualización; el procesamiento de las transacciones en cola posteriores continuará. Un valor de **2** indica que el Suscriptor gana el conflicto, y la transacción en cola invalidará los valores en el Publicador. Un valor de **3** indica que cualquier conflicto provocará la reinicialización del Suscriptor; el Publicador gana el conflicto, se finalizará el proceso de las transacciones en cola subsiguientes y se reinicializará la suscripción. La configuración predeterminada es **1** para las publicaciones transaccionales y **3** para las publicaciones de instantáneas.  
  
## <a name="remarks"></a>Observaciones  
 Para iniciar el Agente de lectura de cola, ejecute **qrdrsvc.exe** en el símbolo del sistema. Para obtener información, vea [Aplicaciones ejecutables del Agente de replicación](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Consulte también  
 [Administración del Agente de replicación](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
