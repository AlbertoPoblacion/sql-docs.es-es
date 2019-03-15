---
title: Identificar la SKU de base de datos SQL de Azure adecuada para la base de datos local (Data Migration Assistant) | Microsoft Docs
description: Aprenda a usar Data Migration Assistant para identificar a la derecha de la SKU de base de datos SQL de Azure para la base de datos local
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 578e6ac47e84ad764cb050112eae768ff21444f3
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57973837"
---
# <a name="identify-the-right-azure-sql-database-sku-for-your-on-premises-database"></a>Identificar la SKU de base de datos SQL de Azure adecuada para la base de datos local

La tarea de migrar las bases de datos a la nube es un complicado y lento, que implica a una serie de variables. Elección de la SKU y el destino de la base de datos de Azure correctas para la base de datos puede ser complicado. Nuestro objetivo con la base de datos Migration Assistant (DMA) es resolver estas cuestiones y facilitar la migración de base de datos experiencia sencilla y eficaz.

En este artículo se centra principalmente en la característica de recomendaciones de SKU de Azure SQL Database de DMA, que le permite identificar las mínimas recomendadas SKU de base de datos de SQL Azure en función de los contadores de rendimiento recopilados de los equipos que aloja las bases de datos. Esta característica proporciona recomendaciones relacionadas con los precios de nivel, el nivel de proceso y tamaño máximo de datos, así como el costo estimado por mes. También ofrece la posibilidad de aprovisionar todas las bases de datos a Azure de forma masiva.

> [!NOTE] 
> Esta funcionalidad está disponible actualmente solo a través de la interfaz de línea de comandos (CLI). Compatibilidad con esta característica a través de la interfaz de usuario DMA se agregará en una próxima versión.

Las instrucciones siguientes ayudan a determinar las recomendaciones de SKU de base de datos de SQL Azure y aprovisionar las bases de datos asociadas en Azure mediante Data Migration Assistant.

## <a name="prerequisites"></a>Requisitos previos

Descargar Database Migration Assistant v4.0 o posterior y, a continuación, vuelva a instalarlo. Si ya tiene la herramienta instalado, cierre y vuelva a abrirlo y le pedirá que la herramienta de actualización.

## <a name="collect-performance-counters"></a>Recopilar contadores de rendimiento

Es el primer paso en el proceso recopilar contadores de rendimiento para las bases de datos. Puede recopilar los contadores de rendimiento mediante la ejecución de un comando de PowerShell en el equipo que hospeda las bases de datos. DMA le proporciona una copia de este archivo de PowerShell, pero también puede usar su propio método para capturar los contadores de rendimiento del equipo.

No es necesario realizar esta tarea para cada base de datos individualmente. Los contadores de rendimiento recopilados desde un equipo se pueden utilizar para recomendar la SKU para todas las bases de datos hospedadas en el equipo.

> [!IMPORTANT]
> El equipo desde el que se ejecuta este comando requiere permisos de administrador en el equipo que hospeda las bases de datos.

1. Compruebe que el archivo de PowerShell necesario para recopilar los contadores de rendimiento está instalado en la carpeta DMA.

    ![Archivo de PowerShell que se muestra en la carpeta DMA](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Ejecute el script de PowerShell con los argumentos siguientes:
    - **ComputerName**: El nombre del equipo que hospeda las bases de datos.
    - **OutputFilePath**: La ruta de acceso de archivo de salida para guardar los contadores recopilados.
    - **CollectionTimeInSeconds**: La cantidad de tiempo durante el cual desea recopilar datos del contador de rendimiento.
      Capturar los contadores de rendimiento de al menos 40 minutos en obtener una recomendación significativa. La duración de la captura, más precisa la recomendación será.
    - **DbConnectionString**: La cadena de conexión que apunte a la base de datos maestra alojado en el equipo desde el que está recopilando datos del contador de rendimiento.
     
    Aquí es una invocación de ejemplo:

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 2400
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```
    
    Cuando se ejecuta el comando, el proceso dará como resultado un archivo con los contadores de rendimiento en la ubicación especificada. Este archivo se puede usar como entrada para el comando de la recomendación de SKU en la sección siguiente.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Usar la CLI de DMA para obtener recomendaciones de SKU

Usar el archivo de salida de los contadores de rendimiento en el paso anterior como entrada para este paso. DMA le proporcionará recomendaciones para la base de datos de SQL Azure tarifa, el nivel de proceso y el tamaño máximo de los datos para cada base de datos en el equipo. DMA también le proporcionará el costo mensual estimado para cada base de datos.

Ejecute el dmacmd.exe con los argumentos siguientes:

- **/Action=SkuRecommendation**: Escriba este argumento para ejecutar las evaluaciones de SKU.
- **/SkuRecommendationInputDataFilePath**: La ruta de acceso al archivo de contadores recopilado en la sección anterior.
- **/SkuRecommendationTsvOutputResultsFilePath**: La ruta de acceso para escribir los resultados de salida en formato TSV.
- **/SkuRecommendationJsonOutputResultsFilePath**: La ruta de acceso para escribir los resultados de salida en formato JSON.
- **/SkuRecommendationHtmlResultsFilePath**: Ruta de acceso para escribir los resultados de salida en formato HTML.

Además, debe elegir uno de los argumentos siguientes:
- Evitar la actualización de precios
    - **/SkuRecommendationPreventPriceRefresh**: Impide que la actualización de precios que se producen. Utilizar si está ejecutando en modo sin conexión.
- Obtener los precios más recientes 
    - **/SkuRecommendationCurrencyCode**: La moneda en que se va a mostrar los precios (p. ej. "USD").
    - **/SkuRecommendationOfferName**: Nombre de la oferta (p. ej. "MS-AZR-0003P"). Para obtener más información, consulte el [detalles de la oferta de Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) página.
    - **/SkuRecommendationRegionName**: Nombre de la región (por ejemplo "WestUS").
    - **/SkuRecommendationSubscriptionId**: Identificador de la suscripción.
    - **/AzureAuthenticationTenantId**: El inquilino de autenticación.
    - **/AzureAuthenticationClientId**: El identificador de cliente de la aplicación AAD que se usa para la autenticación.
    - Una de las opciones de autenticación siguientes:
        - Interactiva
            - **AzureAuthenticationInteractiveAuthentication**: Establecido en true para una ventana emergente de autenticación.
        - Basada en certificados
            - **AzureAuthenticationCertificateStoreLocation**: Establecido en la ubicación del almacén de certificados (p. ej. "CurrentUser").
            - **AzureAuthenticationCertificateThumbprint**: Se establece en la huella digital del certificado.
        - En función del token
            - **AzureAuthenticationToken**: Establecer en el token de certificado.

Estos son algunos invocaciones de ejemplo:

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationInteractiveAuthentication=true
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

El archivo de salida TSV contendrá las columnas mostradas en el gráfico siguiente:

   ![Archivo de PowerShell que se muestra en la carpeta DMA](../dma/media/dma-tsv-file-column.png)

Sigue una descripción de cada columna.

- **DatabaseName** -el nombre de la base de datos.
- **MetricName** : si se ha ejecutado una métrica.
- **MetricType** -nivel recomienda Azure SQL Database.
- **MetricValue** -recomienda SKU de Azure SQL Database.
- **SQLMiEquivalentCores** : Si decide ir para instancia administrada de Azure SQL Database, puede usar este valor para el número de núcleos.
- **IsTierRecommended** -realizamos una recomendación de SKU mínima para cada nivel. A continuación, aplicamos la heurística para determinar el nivel correcto de la base de datos. 
- **ExclusionReasons** : este valor está en blanco si se recomienda un nivel. Para cada nivel que no se recomienda, proporcionamos los motivos por qué lo no se ha seleccionado.
- **AppliedRules** -una notación breve de las reglas que se aplicaron.

El valor recomendado es la SKU mínima necesaria para que las consultas ejecutar en Azure con una tasa de éxito similar a las bases de datos de forma local. Por ejemplo, si la SKU mínima recomendada es S4 del nivel estándar, a continuación, elegir S3 o por debajo se generan consultas en tiempo de espera o no se pueden ejecutar.

El archivo HTML contiene esta información en un formato gráfico. Puede usar el archivo HTML para introducir información de suscripción de Azure, elija el plan de tarifa, nivel y el tamaño máximo de datos de proceso para las bases de datos y generar un script para aprovisionar las bases de datos. Este script se puede ejecutar con PowerShell.

## <a name="provision-your-databases-to-azure"></a>Aprovisionar las bases de datos en Azure
Con tan solo unos clics, puede usar las recomendaciones del paso anterior para aprovisionar bases de datos de destino en Azure a la que puede migrar las bases de datos. También puede realizar cambios a las recomendaciones mediante la actualización del archivo HTML como sigue.

1. Abra el archivo HTML y escriba la siguiente información:
    - **Id. de suscripción** -el identificador de suscripción de la suscripción de Azure a la que desea aprovisionar las bases de datos.
    - **Región** -la región en que se va a aprovisionar las bases de datos. Asegúrese de que la suscripción es compatible con la región que seleccione.
    - **Grupo de recursos** : el grupo de recursos al que desea implementar las bases de datos. Escriba un grupo de recursos existente.
    - **Nombre del servidor** -servidor de la base de datos SQL de Azure al que desea que las bases de datos implementadas. Si escribe un nombre de servidor que no existe, se creará.
    - **Administrador Username\Password** -el nombre de usuario de administrador de servidor y la contraseña.

2. Revise las recomendaciones para cada base de datos y modificar el plan de tarifa, proceso nivel y el tamaño de datos máximo según sea necesario. Asegúrese de anular la selección de las bases de datos que actualmente no desee aprovisionar.

3. Seleccione **generar Script de aprovisionamiento**, guarde el script y, a continuación, ejecutarlo en PowerShell.

    Este proceso debe crear todas las bases de datos que seleccionó en la página HTML.

Puede realizar todos los pasos de este proceso en un único equipo o puede realizar en varios equipos para determinar las recomendaciones de SKU a escala. DMA permite que una experiencia sencilla y escalable que admiten todos estos pasos a través de la interfaz de línea de comandos. Nuevamente, compatibilidad con esta característica a través de la interfaz de usuario DMA estará disponible más adelante este año.

## <a name="next-steps"></a>Pasos siguientes
- Descargue la versión más reciente de [Data Migration Assistant](https://aka.ms/get-dma).
- Consulte el artículo [ejecutar Data Migration Assistant desde la línea de comandos](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017) para obtener una lista completa de comandos para ejecutar DMA desde la CLI.
