---
title: Configuración de SQL Server para enviar comentarios a Microsoft | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: ''
ms.technology: configuration
ms.openlocfilehash: 63a8812e4596233db2bd5b5675e29d340b3df120
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493579"
---
# <a name="configure-sql-server-to-send-feedback-to-microsoft"></a>Configuración de SQL Server para enviar comentarios a Microsoft
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

## <a name="summary"></a>Resumen
De forma predeterminada, Microsoft SQL Server recopila información sobre cómo sus clientes usan la aplicación. En concreto, SQL Server recopila información sobre la experiencia de instalación, el uso y el rendimiento. Esta información ayuda a Microsoft a mejorar el producto para satisfacer mejor las necesidades del cliente. Por ejemplo, Microsoft recopila información sobre los tipos de códigos de error que encuentran los clientes para que podamos corregir errores relacionados, mejorar nuestra documentación sobre cómo usar SQL Server y determinar si deben agregarse características al producto para ofrecer un mejor servicio a los clientes.

En concreto, Microsoft no envía ninguno de los tipos de información siguientes a través de este mecanismo:
- Valores de dentro de las tablas de usuario
- Credenciales de inicio de sesión u otra información de autenticación
- Información de identificación personal (PII)

En el escenario de ejemplo siguiente se incluye información de uso de características que ayuda a mejorar el producto.

SQL Server 2017 admite índices de almacén de columnas para habilitar escenarios de análisis rápido. Los índices de almacén de columnas combinan una estructura de índices de "árbol B" tradicional para los datos recién insertados con una estructura comprimida orientada a columnas especial para comprimir los datos y acelerar la ejecución de las consultas. El producto contiene heurística para migrar datos desde la estructura de árbol B hasta la estructura comprimida en el fondo, lo que acelera, por tanto, los resultados de la consulta futuros.

Si la operación en segundo plano no va al compás de la velocidad de inserción de los datos, el rendimiento de las consultas puede ser más lento de lo esperado. Para mejorar el producto, Microsoft recopila información sobre lo bien que SQL Server sigue el ritmo del proceso de compresión de datos automático. El equipo del producto usa esta información para ajustar la frecuencia y el paralelismo del código que realiza la compresión. Esta consulta se ejecuta de forma ocasional para recopilar esta información a fin de que nosotros, Microsoft, podamos evaluar la velocidad de movimiento de los datos. Esto nos ayuda a optimizar la heurística del producto.  

```sql
SELECT object_id, type_desc, data_space_id, db_id() AS database_id FROM sys.indexes WITH(nolock) WHERE type = 5 or type = 6 
```

```sql
SELECT cntr_value as merge_policy_evaluation
FROM sys.dm_os_performance_counters WITH(nolock)
WHERE object_name LIKE '%columnstore%' 
AND counter_name ='Total Merge Policy Evaluations' 
AND instance_name = '_Total'
```

Tenga en cuenta que este proceso se centra en los mecanismos necesarios para entregar valor a los clientes. El equipo del producto no examina los datos del índice ni envía dichos datos a Microsoft. SQL Server 2017 siempre recopila y envía información sobre la experiencia de instalación del proceso de configuración para que podamos encontrar y corregir con rapidez cualquier problema de instalación que experimente el cliente. SQL Server 2017 se puede configurar para que no se envíe información (por instancia por servidor) a Microsoft a través de los mecanismos siguientes:
- Mediante el uso de la aplicación Informes de uso y errores
- Mediante el establecimiento de subclaves del Registro en el servidor

Para SQL Server en Linux, consulte [Customer Feedback for SQL Server on Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-customer-feedback) (Comentarios del usuario para SQL Server en Linux)

> [!NOTE]
> Puede deshabilitar el envío de información a Microsoft solo en versiones de pago de SQL Server.

## <a name="error-and-usage-reporting-application"></a>Aplicación Informes de uso y errores 

Tras la instalación, la configuración de recopilación de datos de uso para componentes e instancias de SQL Server se puede cambiar a través de la aplicación Informes de uso y errores. Esta aplicación está disponible como parte de la instalación de SQL Server. Esta herramienta permite a cada instancia de SQL Server establecer su propia configuración Datos de uso.

> [!NOTE]
> La aplicación Informes de uso y errores se incluye en las herramientas de configuración de SQL Server. Puede usar esta herramienta para administrar su preferencia por la recopilación de comentarios de uso e informes de error de la misma forma que en SQL Server 2017. Los informes de error son independientes de la recopilación de comentarios de uso, de modo que pueden activarse o desactivarse independientemente de la recopilación de comentarios de uso. Los informes de errores recopilan volcados de memoria que se envían a Microsoft y que pueden contener información confidencial, como se describe en la [declaración de privacidad](https://go.microsoft.com/fwlink/?LinkID=868444).

Para iniciar Informes de uso y errores de SQL Server, haga clic o pulse **Iniciar** y, a continuación, busque en "Error" en el cuadro de búsqueda. Se mostrará el elemento Informes de uso y errores de SQL Server. Tras iniciar la herramienta, puede administrar comentarios de uso y errores graves que se recopilan para instancias y componentes instalados en ese equipo.

Para las versiones de pago, use las casillas "Informes de uso" para administrar el envío de comentarios de uso a Microsoft.

Para las versiones de pago o gratuitas, use las casillas "Informes de error" para administrar el envío de comentarios sobre errores graves y volcados de memoria a Microsoft.

## <a name="set-registry-subkeys-on-the-server"></a>Establecer subclaves del Registro en el servidor

Los clientes empresariales pueden establecer la configuración de directiva de grupo para participar o no en la recopilación de datos de uso. Esto se hace configurando una directiva basada en el Registro. La subclave del Registro y la configuración necesarias son:

- Para las características de instancia de SQL Server:
    
    Subclave = HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\{InstanceID}\CPE
    
    Nombre EntradaRegistro = CustomerFeedback
    
    Tipo de entrada DWORD: 0 es no participar; 1 es participar
    
    {InstanceID} hace referencia al tipo de instancia y a la instancia, como en los ejemplos siguientes:

    - MSSQL14.CANBERRA para motor de base de datos SQL Server 2017 y nombre de instancia de "CANBERRA"
    - MSAS14.CANBERRA para SQL Server 2017 Analysis Services y nombre de instancia de "CANBERRA"
    - MSRS14.CANBERRA para SQL Server 2017 Reporting Services y nombre de instancia de "CANBERRA"

- Para todas las características compartidas:
    
    Subclave = HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\{Major Version}
    
    Nombre EntradaRegistro = CustomerFeedback
    
    Tipo de entrada DWORD: 0 es no participar; 1 es participar

> [!NOTE]
> {Versión principal} hace referencia a la versión de SQL Server, por ejemplo 140 para SQL Server 2017.

- Para SQL Server Management Studio 17:
  
    Subclave = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\14.0

    Nombre EntradaRegistro = UserFeedbackOptIn

    Tipo de entrada DWORD: 0 es no participar; 1 es participar

    Además, SSMS 17.x se basa en el shell de Visual Studio 2015 y la instalación de Visual Studio admite los comentarios de los clientes de forma predeterminada.  

    Para configurar Visual Studio para deshabilitar los comentarios de los clientes en equipos específicos, cambie el valor de la siguiente subclave del registro por la cadena "0":  
    HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn

    Por ejemplo, modifique la subclave así:  
    HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn="0")

    La recopilación de datos de uso de SQL Server 2017 respeta la directiva de grupo basada en el Registro sobre estas subclaves del Registro.

- Para SQL Server Management Studio 18:
    
    Subclave = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\18.0_IsoShell

    Nombre EntradaRegistro = UserFeedbackOptIn

    Tipo de entrada DWORD: 0 es no participar; 1 es participar
## <a name="set-registry-subkeys-for-crash-dump-collection"></a>Establecer subclaves del Registro para la recopilación de volcados de memoria

De forma similar al comportamiento en una versión anterior de SQL Server, los clientes de SQL Server 2017 Enterprise pueden establecer la configuración de directivas de grupo en el servidor para participar o no en la recopilación de volcados de memoria. Esto se hace configurando una directiva basada en el Registro. Las claves del Registro y la configuración necesarias son: 

- Para las características de instancia de SQL Server:

    Subclave = HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\{InstanceID}\CPE

    Nombre EntradaRegistro = EnableErrorReporting

    Tipo de entrada DWORD: 0 es no participar; 1 es participar
 
    {InstanceID} hace referencia al tipo de instancia y a la instancia, como en los ejemplos siguientes: 

    - MSSQL14.CANBERRA para motor de base de datos SQL Server 2017 y nombre de instancia de "CANBERRA"
    - MSAS14.CANBERRA para SQL Server 2017 Analysis Services y nombre de instancia de "CANBERRA"
    - MSRS14.CANBERRA para SQL Server 2017 Reporting Services y nombre de instancia de "CANBERRA"
 

- Para todas las características compartidas:
    
    Subclave = HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\{Major Version}

    Nombre EntradaRegistro = EnableErrorReporting

    Tipo de entrada DWORD: 0 es no participar; 1 es participar

> [!NOTE]
> {Major Version} hace referencia a la versión de SQL Server. Por ejemplo, "140" hace referencia a SQL Server 2017.

La recopilación de volcados de memoria de SQL Server 2017 respeta la directiva de grupo basada en el Registro sobre estas subclaves del Registro. 

## <a name="crash-dump-collection-for-ssms"></a>Recopilación de volcados de memoria para SSMS
SSMS no recopila su propio volcado de memoria. Cualquier volcado de memoria relativo a SSMS se recopila como parte de Informe de errores de Windows.

El procedimiento para activar o desactivar esta característica depende de la versión del SO. Para activar o desactivar la característica, siga los pasos en el artículo adecuado para su versión de Windows.
 
- Windows Server 2016 y Windows 10

    [Configurar la telemetría de Windows en la organización](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization)
- Windows Server 2008 R2 y Windows 7

    [WER Settings](/windows/desktop/wer/wer-settings) (Configuración de WER)
 
## <a name="feedback-for-analysis-services"></a>Comentarios sobre Analysis Services

Durante la instalación, SQL Server 2016 Analysis Services agrega una cuenta especial a su instancia de Analysis Services. Esta cuenta es miembro del rol de administrador del servidor de Analysis Services. La cuenta se usa para recopilar información de comentarios de la instancia de Analysis Services.  

Puede configurar su servicio para que no se envíen datos de uso, tal como se describe en la sección "Establecer subclaves del Registro en el servidor". Sin embargo, al hacer esto no se quita la cuenta de servicio. 
 
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
