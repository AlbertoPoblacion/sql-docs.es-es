---
title: 'Lección 3: Diseñar el informe primario mediante el Asistente para informes | Microsoft Docs'
description: Obtenga información sobre cómo diseñar el informe primario mediante el Asistente para informes del Diseñador de informes después de crear una conexión de datos y una tabla de datos para el informe primario.
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 74b71002f5f84f4d9b80966f6b44721b9942c8b4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247534"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>Lección 3: Diseño del informe primario usando el Asistente para informes
Después de crear una conexión de datos y una tabla de datos para el informe primario, el paso siguiente consiste en diseñar dicho informe usando el Asistente para informes del Diseñador de informes. Para más información sobre el Diseñador de informes, vea [Diseñar informes con el Diseñador de informes &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>Para diseñar el informe primario usando el Asistente para informes  
  
1.  Asegúrese de que el sitio web de nivel superior está seleccionado en el **Explorador de soluciones**.  
  
2.  Haga clic con el botón derecho en el sitio web y seleccione **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Asistente para informes**, escriba un nombre para el archivo de informe y, después, seleccione **Agregar**.  
  
    Así se inicia el Asistente para informes.  
  
4.  En la página **Propiedades de conjunto de datos** , en el cuadro **Origen de datos** , seleccione el **DataSet1** que creó en la [Lección 2: Definir una conexión de datos y una tabla de datos para el informe primario](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
  
    El cuadro **Conjuntos de datos disponibles** se actualiza automáticamente con la **DataTable** que creó anteriormente.  
  
5.  Seleccione **Next** (Siguiente).  
  
6.  En la página **Organizar campos** , haga lo siguiente:  
  
    1.  Arrastre **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**y **ReorderLevel** desde **Campos disponibles** hasta el cuadro **Valores** .  
  
    2.  Seleccione la flecha situada junto a **Sum(ProductID)** , **Sum(SafetyStockLevel)** y **Sum(ReorderLevel)** , y desactive la selección de **Suma** .  
  
7.  Seleccione **Siguiente** dos veces y, después, seleccione **Finalizar** para cerrar el **Asistente para informes**.  
  
    Ahora ha creado el archivo .rdlc. El archivo se abre en el Diseñador de informes. El Tablix que se diseñó se muestra en la superficie de diseño.  
  
8.  Guarde el archivo .rdlc.  
  
## <a name="next-task"></a>Tarea siguiente  
Ha diseñado correctamente el informe primario usando el Asistente para informes. A continuación, creará una conexión de datos y una tabla de datos para el informe secundario. Consulte [Lección 4: Definición de una conexión de datos y una tabla de datos para el informe secundario](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
  
  

