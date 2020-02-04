---
title: Maneras alternativas de obtener una conexión de datos (Generador de informes) | Microsoft Docs
ms.date: 06/15/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 887104ff6667844071e44e1933592e8238b124dc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "62703890"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a>Maneras alternativas de obtener una conexión de datos (Generador de informes)
Una conexión de datos contiene la información para conectarse a un origen de datos externo, por ejemplo una base de datos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Normalmente, la información de conexión y el tipo de credenciales que se debe usar utilizar se obtienen del propietario del origen de datos.  
  
Para especificar una conexión de datos, puede utilizar un origen de datos compartido del servidor de informes o crear un origen de datos incrustado que solo se utilice en un informe específico.  
  
En la mayoría de los tutoriales se utilizan orígenes de datos incrustados, pero si tiene acceso a orígenes de datos compartidos, puede utilizarlos en su lugar.  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a>Recibir una conexión de datos desde un origen de datos compartido  
Si el servidor de informes dispone de orígenes de datos compartidos para los que tiene permiso de uso, puede usarlos en lugar de los orígenes de datos insertados. Los siguientes procedimientos indican cómo buscar los orígenes de datos compartidos y proporcionar las credenciales necesarias para usarlos.  
  
Para usar un origen de datos compartido, vaya a un servidor de informes y seleccione uno. Normalmente, obtendrá la dirección URL del servidor de informes del administrador del servidor de informes.  
  
### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a>Especificar una conexión de datos de una lista de orígenes de datos compartidos  
  
1.  En el Asistente para nueva tabla o matriz o para nuevo gráfico, en la página **Elegir un conjunto de datos** , seleccione **Crear un conjunto de datos**y, después, haga clic en **Siguiente**. Se abre la página **Elegir una conexión a un origen de datos** .  
  
2.  De la lista de orígenes de datos, seleccione un origen de datos para el que tenga permiso de acceso.  
  
3.  Para comprobar que se puede conectar al origen de datos, haga clic en **Probar conexión**. Aparece un mensaje que indica que la conexión se ha creado correctamente. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  Haga clic en **Next**.  
  
    Si es necesario, escriba sus credenciales. Para guardar las credenciales de forma local, seleccione **Guardar contraseña con conexión**. Si no selecciona esta opción, se le pedirán las credenciales cada vez que ejecute el informe  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a>Especificar una conexión de datos desplazándose a un origen de datos compartido en un servidor de informes  
  
1.  En el Asistente para nueva tabla o matriz o para nuevo gráfico, en la página **Elegir un conjunto de datos** , seleccione **Crear un conjunto de datos**y, después, haga clic en **Siguiente**. Se abre la página **Elegir una conexión a un origen de datos** .  
  
2.  Haga clic en **Examinar**. Se abre el cuadro de diálogo **Seleccionar origen de datos** .  
  
3.  En la lista desplegable **Buscar en** , seleccione **Sitios y servidores recientes**. En el panel de origen de datos, haga clic en la dirección URL del servidor y, después, haga clic en **Abrir**.  
  
    Se muestra la lista de orígenes o modelos de datos.  
  
4.  Alternativamente, en **Name**, escriba la dirección URL del servidor de informes. Haga clic en **Abrir**.  
  
    El Generador de informes se conecta al servidor de informes y carga los orígenes de datos que están disponibles en la carpeta raíz.  
  
5.  Vaya hasta una carpeta que contenga un origen de datos para el que disponga de los permisos de conexión necesarios, seleccione el origen de datos y luego haga clic en **Abrir**.  
  
    Volverá a encontrarse en la página **Elegir una conexión a un origen de datos** .  
  
6.  Para comprobar que se puede conectar al origen de datos, haga clic en **Probar conexión**.  
  
    Aparece un mensaje que indica que la conexión se ha creado correctamente. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Haga clic en **Next**.  
  
8.  Si se le solicita un nombre de usuario y contraseña, escriba sus credenciales. Para guardar las credenciales de forma local, seleccione **Guardar contraseña con conexión**.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte también  
[Conjuntos de datos de informe &#40;SSRS&#41;](../reporting-services/report-data/report-datasets-ssrs.md)  
[Tutoriales del Generador de informes](../reporting-services/report-builder-tutorials.md) 
  

