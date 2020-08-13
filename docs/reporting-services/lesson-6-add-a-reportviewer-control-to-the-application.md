---
title: 'Lección 6: Agregar un control ReportViewer a la aplicación | Microsoft Docs'
description: Aprenda a agregar un control ReportViewer a la aplicación de sitio web después de diseñar el informe secundario con el Asistente de informes.
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4090a01d4aa50fcbbfa64182dcd23a3e01c50e78
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245104"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lección 6: Adición de un control ReportViewer a la aplicación
Después de diseñar el informe secundario con el Asistente de informes, el paso siguiente consiste en agregar un control ReportViewer a la aplicación del sitio Web. Si usa el sitio web de informes ASP.NET, habrá agregado el control ReportViewer a la página default.aspx.   
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Para agregar un control ReportViewer a la aplicación  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **Default.aspx**y, después, haga clic en **Diseñador de vistas**.  
  
2.  Si default.aspx ya tiene el control ReportViewer en él, vaya al **Paso 4**. En caso contrario, en el grupo **Extensiones AJAX** , en la ventana **Cuadro de herramientas** , arrastre un control **ScriptManager** a la superficie de diseño.  
  
3.  En el grupo **Reporting** , arrastre un control **ReportViewer** a la superficie de diseño debajo del control **ScriptManager** .  
  
4.  Haga clic en la flecha de la esquina superior derecha del control **ReportViewer** para abrir la ventana **Tareas de ReportViewer** .  
  
5.  En el cuadro **Elegir informe** , seleccione el informe primario que ha creado.  
  
    Al seleccionar un informe, las instancias de los orígenes de datos usados en el informe se crean automáticamente. El código se genera para crear una instancia de cada DataTable (y el contenedor [DataSet](https://msdn.microsoft.com/library/system.data.dataset.aspx) ). Un control [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource.aspx) se agrega a la superficie de diseño, correspondiente a cada origen de datos usado en el informe. Este control de origen de datos se configura automáticamente.  
  
6.  En el menú Compilar, haga clic en Compilar sitio Web.  
  
    Se compila el informe y errores como un error de sintaxis en una expresión de informe aparecen en el área de **Lista de errores** . Haga clic en **Lista de errores** en la parte inferior de la ventana de Visual Studio para mostrar el área de **Lista de errores** .  
  
## <a name="next-task"></a>Tarea siguiente  
Ha agregado correctamente un control ReportViewer a la aplicación del sitio Web. Después, agregará una acción de obtención de detalles en el informe primario. Vea [Lección 7: Incorporación de una acción de obtención de detalles en el informe primario](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md).  
  

