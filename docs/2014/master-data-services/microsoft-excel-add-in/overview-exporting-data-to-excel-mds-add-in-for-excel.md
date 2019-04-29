---
title: Carga de datos (complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 465b14ab5cb96f3f587222427ea793bbaf225b01
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923962"
---
# <a name="loading-data-mds-add-in-for-excel"></a>Cargar datos (complemento MDS para Excel)
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], debe cargar datos desde el repositorio MDS en una hoja de cálculo de Excel activa para poder trabajar con él. Cuando termine de trabajar con los datos, publíquelos en el repositorio MDS para que otros usuarios puedan compartirlos.  
  
 Los datos que puede cargar se limitan a aquellos para los que tiene permiso de acceso. El permiso de acceso a datos se establece en la aplicación web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] o mediante programación.  
  
 Cuando cargue grandes cantidades de datos, puede establecer las advertencias que se mostrarán cuando los datos pueden tardar mucho en cargarse. Para ello, en el grupo **Opciones** , haga clic en **Configuración**. En la pestaña **Datos** , seleccione **Mostrar advertencia de filtro para grandes conjuntos de datos**.  
  
> [!WARNING]  
>  Es preciso abrir un libro habilitado para MDS y actualizarlo solo en Excel con un complemento de MDS para Excel. Cuando se abre un libro habilitado para MDS en Excel en un equipo en el que no esté instalado el complemento de MDS para Excel, o no se admita, podría dañarse el archivo del libro. Si desea compartir datos con otra persona, envíele por correo electrónico un archivo de consulta de acceso directo, en lugar de guardar la hoja de cálculo y enviarla por correo electrónico. Para obtener más información sobre la consulta, consulte [Enviar por correo electrónico un archivo de consulta de acceso directo &#40;complemento MDS para Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Filtrado de datos  
 Puede filtrar datos antes de cargarlos para limitar la cantidad de datos que se va a descargar. Esto incluye elegir qué atributos (columnas) desea cargar, el orden que desea mostrar los atributos y los miembros (filas de datos) con los que desea trabajar. Para obtener más información, consulte [filtrar datos antes de la carga &#40;complemento MDS para Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Conectar automáticamente y cargar datos utilizados con frecuencia  
 Si desea conectarse al mismo servidor y cargar siempre el mismo conjunto de datos, puede crear archivos de consulta de acceso directo, que contienen la información de conexión y filtro. Para obtener más información sobre los archivos de consulta, consulte [Archivos de consulta de acceso directo &#40;complemento MDS para Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Actualizar datos  
 Otros usuarios pueden actualizar los datos del repositorio MDS después de que usted los haya cargado. Puede recuperar estos datos sin perder los cambios realizados en los datos que no son de MDS. Para obtener más información, consulte [Actualizar datos &#40;complemento MDS para Excel&#41;](refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Filtrar los datos MDS antes de cargarlos en Excel.|[Filtrar datos antes de cargarlos &#40;complemento MDS para Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Cargar datos MDS en Excel.|[Cargar datos de MDS en Excel](export-data-to-excel-from-master-data-services.md)|  
|Cambiar el orden de las columnas antes de descargar datos.|[Reordenar columnas &#40;complemento MDS para Excel&#41;](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Conexiones &#40;complemento MDS para Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Archivos de consulta de acceso directo &#40;complemento MDS para Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Complemento Master Data Services para Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Seguridad &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  
