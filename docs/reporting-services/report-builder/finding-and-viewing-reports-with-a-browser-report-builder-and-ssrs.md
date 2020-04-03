---
title: Búsqueda y visualización de informes con un explorador (Generador de informes) | Microsoft Docs
description: Puede ver un informe con un explorador web que tenga una conexión directa a un servidor de informes. El informe incluye la barra de herramientas de informe para que pueda navegar y buscar.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: edf4843a-2a0a-486f-be25-14a3c1c6bc72
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 489d91bc5f410b6bdce4ef61bd694861bd1c1a7d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2020
ms.locfileid: "80342825"
---
# <a name="finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs"></a>Buscar y ver informes con un explorador (Generador de informes y SSRS)
  Puede utilizar cualquier explorador web compatible para ver un informe mediante una conexión directa a un servidor de informes. Cada informe dispone de una dirección URL en el servidor de informes. Puede escribir la dirección web de un informe para abrirlo por sí solo en una ventana del explorador de una aplicación web. El informe se abre en formato HTML e incluye la barra de herramientas de informe para que pueda navegar por las páginas o buscar valores de datos dentro del informe. Puede establecer parámetros en la dirección URL para ocultar la barra de herramientas o para seleccionar el formato de salida del informe.  
  
 La apertura de un informe a través de su dirección web es adecuada para verlo, pero no para administrarlo. No se puede tener acceso a las páginas de propiedades de un elemento ni a las páginas de definición de suscripciones. Debe utilizar el Administrador de informes o un sitio de SharePoint para esas tareas.  
  
 Si no conoce la dirección web de un informe, puede abrir la dirección web del servidor de informes y, a continuación, examinar la jerarquía de carpetas del servidor de informes para seleccionar el informe desea ver. El siguiente diagrama muestra una jerarquía de carpetas tal como aparecería en una ventana de explorador.  
  
 ![Carpetas en un explorador](../../reporting-services/report-builder/media/rs-browserfolder.GIF "Carpetas en un explorador")  
Carpetas en un explorador  
  
> [!NOTE]  
>  Si obtiene acceso a un informe desde un dispositivo de mano, deberá utilizar el explorador para abrir los informes. El Administrador de informes todavía no ofrece compatibilidad con este tipo de dispositivos.  
  
 Para más información sobre los tipos de exploradores que puede usar, consulte [Compatibilidad del explorador de Reporting Services y Power View](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="navigating-report-server-folders-in-a-web-browser"></a>Navegar por las carpetas del servidor de informes en un explorador web  
 Puede utilizar un explorador web para navegar por las carpetas del servidor de informes y ejecutar informes. Los informes y los elementos se muestran en forma de vínculos en la jerarquía de carpetas. Para abrir un informe, un recurso o una carpeta, o ver el contenido de un origen de datos compartido, haga clic en estos vínculos. La navegación por la jerarquía de carpetas puede resultarle útil si desconoce la dirección URL de un informe. Para abrir una conexión con el explorador en el nodo raíz de la jerarquía de carpetas, solo tiene que especificar la dirección web del servidor de informes; a continuación, puede hacer clic en los vínculos de las carpetas para navegar por la jerarquía.  
  
 Al tener acceso a un directorio virtual de un servidor de informes, solo se visualizan las carpetas, los informes y los elementos cargados para los que se tiene permiso de acceso. La interfaz de usuario muestra únicamente la jerarquía de carpetas e información básica como, por ejemplo, la fecha de creación o modificación, el tamaño del archivo o el tipo de elemento de cada elemento:  
  
-   Un vínculo sin ningún otro indicador es un informe o un modelo.  
  
-   La etiqueta \<ds> indica un origen de datos compartido.  
  
-   La etiqueta \<dir> indica un elemento de carpeta.  
  
-   Una extensión de nombre de archivo indica que se trata de un recurso. La extensión del nombre del archivo identifica el tipo MIME del recurso. Por ejemplo, .jpg indica que se trata de una imagen en formato JPEG.  
  
## <a name="typing-the-url-address-of-a-report"></a>Escribir la dirección URL de un informe  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] admite el acceso con direcciones URL a determinados elementos de un servidor de informes. La dirección URL debe incluir una ruta de acceso completa al informe y comandos para representarlo. Si el informe incluye parámetros, también debe especificar cualquier valor necesario para abrir el informe. Si escribe una dirección URL para un informe que incluya espacios en la ruta de acceso, valores de parámetros o una extensión de representación, incluya en la dirección URL caracteres con codificación URL para obtener el resultado deseado. El siguiente ejemplo corresponde a una dirección URL de informe que incluye codificación para los espacios del nombre de la ruta de acceso, los parámetros y la extensión de representación:  
  
 `https://<Webservername>/reportserver?/<reportfolder>/employee+sales+summary&ReportYear=2004&ReportMonth=06&EmpID=24&rs:Command=Render&rs:Format=HTML4.0`  
  
 El límite máximo para una dirección URL en Internet Explorer es de 2.083 caracteres. Para obtener más información, vea [La longitud máxima de la dirección URL es de 2083 caracteres en Internet Explorer](https://support.microsoft.com/kb/208427).  
  
 Para obtener más información sobre el acceso a informes mediante una dirección URL, incluida información sobre cómo generar este tipo de direcciones, consulte [Acceso URL (SSRS)](../../reporting-services/url-access-ssrs.md).  
  
  
