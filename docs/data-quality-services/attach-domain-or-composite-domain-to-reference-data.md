---
title: Adjuntar un dominio o un dominio compuesto a datos de referencia
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.refdata.f1
- sql13.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: swinarko
ms.author: sawinark
ms.openlocfilehash: dbd64575acaf5ddf2f57e99b010a8a3b1555780e
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75258873"
---
# <a name="attach-domain-or-composite-domain-to-reference-data"></a>Adjuntar un dominio o un dominio compuesto a datos de referencia

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En este tema se describe cómo adjuntar dominios o dominios compuestos de una base de conocimiento de calidad de datos a un servicio de datos de referencia de Azure Marketplace para generar conocimiento con los datos de referencia de alta calidad. Cada servicio de datos de referencia contiene un esquema (columnas de datos). Después de adjuntar un dominio o un dominio compuesto a un servicio de datos de referencia, debe asignar el dominio adjunto o los dominios individuales dentro del dominio compuesto adjunto a las columnas adecuadas de un esquema del servicio de datos de referencia. Adjuntar un dominio compuesto a un servicio de datos de referencia permite adjuntar solo un dominio a un servicio de datos de referencia y, a continuación, asignar los dominios individuales incluidos en el dominio compuesto a las columnas adecuadas del esquema del servicio de datos de referencia.  

> [!IMPORTANT]
> En este artículo se mencionan algunos servicios de datos de referencia de terceros que anteriormente no estaban disponibles desde Azure DataMarket. DataMarket y Data Services (incluidos los datos de dirección de Melissa, por ejemplo), se suspendieron después del 31/12/2016. Como resultado, ya no se pueden ejecutar los ejemplos de este artículo con los servicios especificados de DataMarket. Sin embargo, se pueden usar los servicios de datos de referencia que están disponibles directamente en línea de los proveedores de datos de referencia de terceros.

> [!WARNING]  
>  El dominio compuesto adjunto a un servicio de datos de referencia está disponible en la lista desplegable de dominios al asignar dominios a las columnas del esquema del servicio de datos de referencia. No asigne el dominio compuesto a una columna del esquema del servicio de datos de referencia; solo debe asignar dominios individuales dentro de un dominio compuesto a las columnas adecuadas del esquema del servicio de datos de referencia. De lo contrario, se producirá un error.  
  
 Un esquema del servicio de datos de referencia puede tener una columna obligatoria que se debe asignar al dominio apropiado si decide usar el servicio de datos de referencia. La columna obligatoria de un esquema de datos de referencia se identifica mediante "(M)" en el nombre de columna. Por ejemplo, **AddressLine** es la columna de esquema obligatoria en **Melissa Data - Address Data** y **CompanyName** es la columna de esquema obligatoria en **Digital Trowel Inc. - Us companies and professional data for SQL users**.  
  
 En este tema, se crearán cuatro dominios: **Address Line**, **City**, **State** y **Zip**, bajo un dominio compuesto, **Address Verification**, se adjuntará el dominio compuesto al servicio de datos de referencia **Melissa Data - Address Check** y después se asignarán los dominios individuales dentro del dominio compuestas a las columnas adecuadas del esquema del servicio de datos de referencia.  
  
## <a name="before-you-begin"></a>Antes de empezar  
  
###  <a name="Prerequisites"></a>Requisitos previos  
 Es necesario configurar [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) para utilizar los servicios de datos de referencia. Vea [Configurar DQS para usar datos de referencia](../data-quality-services/configure-dqs-to-use-reference-data.md).  
  
###  <a name="Security"></a>Bursátil  
  
#### <a name="permissions"></a>Permisos  
 Debe disponer del rol dqs_kb_editor en la base de datos DQS_MAIN para asignar dominios a datos de referencia.  
  
##  <a name="Map"></a>Asignación de dominios a datos de referencia de Melissa Data  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , en **Administración de la base de conocimiento**, haga clic en **Nueva base de conocimiento**.  
  
3.  En la pantalla **Nueva base de conocimiento** , escriba un nombre para la nueva base de conocimiento, haga clic en la actividad **Administración de dominios** y, por último, haga clic en **Crear**.  
  
4.  En la pantalla **Administración de dominios** , haga clic en el icono **Crear un dominio** para crear un dominio. Cree los cuatro dominios siguientes: **Address line**, **City**, **State**y **Zip**.  
  
5.  Haga clic en el icono **Crear un dominio compuesto** para crear un dominio compuesto. En el cuadro de diálogo **Crear un dominio compuesto** , escriba **Address Verification** en el cuadro **Nombre de dominio compuesto** e incluya en el dominio compuesto todos los dominios creados en el paso 3. Haga clic en **Aceptar**.  
  
6.  En el panel **Dominio** del lado izquierdo, seleccione el dominio compuesto haciendo clic en **Address Verification**y, a continuación, haga clic en la pestaña **Datos de referencia** situada en el lado derecho.  
  
7.  Haga clic en el icono **Examinar** .  
  
8.  En el cuadro de diálogo **Catálogo de proveedores de datos de referencia en línea** :  
  
    1.  En **DataMarket Data Quality Services**, active la casilla **Melissa Data - Address Check**.  
  
    2.  Asigne las columnas del servicio de datos de referencia Melissa Data - Address Check a los dominios adecuados (Address Line, City, State y Zip). Para asignar las columnas, seleccione una columna del servicio de datos de referencia en la columna **Esquema RDS** y, a continuación, seleccione el dominio adecuado en la columna **Dominio** . Para agregar más filas a la tabla, haga clic en el icono **Agregar entrada de esquema** .  
  
    3.  Haga clic en **Aceptar** para guardar los cambios y cerrar el cuadro de diálogo **Catálogo de proveedores de datos de referencia en línea** .  
  
         ![Cuadro de diálogo Catálogo de proveedores de datos de referencia en línea](../data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Cuadro de diálogo Catálogo de proveedores de datos de referencia en línea")  
  
        > [!NOTE]  
        >  -   En el cuadro de diálogo **Catálogo de proveedores de datos de referencia en línea** , el nodo **Datamarket Data Quality Services** muestra todos los proveedores de servicios de datos de referencia a los que se ha suscrito en Azure Marketplace. Si ha configurado proveedores de servicios directos de datos de referencia de terceros en línea en DQS, estos aparecerán en otro nodo denominado **Proveedores en línea directa de terceros** (no disponible en este momento debido a que se ha configurado ningún proveedor de servicios directos de datos de referencia de terceros en línea en DQS).  
  
9. Volverá a la pestaña **datos de referencia** . En el área **configuración de proveedor** , cambie los valores de los cuadros siguientes, si es necesario:  
  
    -   **Umbral de corrección automática**: las correcciones del servicio de datos de referencia con un nivel de confianza por encima de este umbral se realizarán automáticamente. Escriba un valor en la notación decimal del valor de porcentaje correspondiente. Por ejemplo, escriba 0,9 para un porcentaje del 90%.  
  
    -   **Candidatos sugeridos**: el número de candidatos sugeridos que se van a mostrar desde el servicio de datos de referencia.  
  
    -   **Confianza mínima**: las sugerencias del servicio de datos de referencia con un nivel de confianza inferior a este valor se omitirán. Escriba un valor en la notación decimal del valor de porcentaje correspondiente. Por ejemplo, escriba 0,6 para un porcentaje del 60 %.  
  
10. Haga clic en **Finalizar** para publicar la base de conocimiento. Aparecerá un mensaje de confirmación una vez que la base de conocimiento se haya publicado correctamente.  
  
 Ahora puede usar esta base de conocimiento para la actividad de limpieza en un proyecto de calidad de datos para normalizar y limpiar direcciones de EE. UU. en los datos de origen en función del conocimiento proporcionado por Melissa data a través de Azure Marketplace.  
  
##  <a name="FollowUp"></a>Seguimiento: después de asignar un dominio a datos de referencia  
 Cree un proyecto de calidad de datos y ejecute la actividad de limpieza en los datos de origen que incluyan direcciones de EE. UU., comparándolos con la base de conocimiento creada en este tema. Vea [Limpiar datos mediante el conocimiento de datos de referencia &#40;externo&#41;](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
## <a name="see-also"></a>Véase también  
 [Data Services de referencia en DQS](../data-quality-services/reference-data-services-in-dqs.md)   
 [Limpieza de datos](../data-quality-services/data-cleansing.md)  
  
  
