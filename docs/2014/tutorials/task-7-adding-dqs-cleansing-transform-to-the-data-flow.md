---
title: 'Tarea 7: Agregar transformación al flujo de datos de limpieza de DQS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 209659609c2cf19196cc35050fb32e39e079d1c7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65488942"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>Tarea 7: Adición de la transformación Limpieza de DQS al flujo de datos
  En esta tarea, agregará la transformación Limpieza de DQS al flujo de datos para limpiar los datos de proveedor de entrada mediante DQS. Consulte **[transformación limpieza de DQS](https://msdn.microsoft.com/library/ee677619.aspx)** para obtener más información acerca de la transformación.  
  
1.  Haga clic en **limpieza de DQS** en el **de flujo de datos** ficha y haga clic en **cambiar el nombre**. Tipo **limpiar datos de proveedor**y presione **ENTRAR**.  
  
2.  Seleccione **leer datos de proveedor de archivo de Excel**; arrastre el conector azul hasta **limpiar datos de proveedor**. Los componentes ahora están conectados.  
  
     ![Leer datos de proveedor -> Limpiar datos de proveedor](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "leer datos de proveedor -> Limpiar datos de proveedor")  
  
3.  Haga doble clic en **limpiar datos de proveedor**.  
  
4.  En el **Editor de transformación limpieza de DQS**, haga clic en **New** junto a la **lista desplegable de administrador de conexiones de calidad de datos**.  
  
5.  En el **DQS Cleansing Connection Manager** cuadro de diálogo, escriba **(local)** o **período** (.) para conectarse al servidor local. En esta lección se da por supuesto que ha instalado DQS en un servidor local.  
  
6.  Haga clic en **Probar conexión** para probar la conexión al servidor DQS.  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
8.  Seleccione **proveedores** para el **Data Quality Knowledge Base**.  
  
     ![Editor de transformación: KB de proveedores de limpieza de DQS](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "Editor de transformación: KB de proveedores de limpieza de DQS")  
  
9. Cambie a la **asignación** ficha en la parte superior.  
  
10. Desde **columnas de entrada disponibles**, seleccione **Supplier Name**, **ContactEmailAddress**, **Address Line**, **Ciudad**, **Estado**, **país**, y **código postal** seleccionando las casillas de verificación.  
  
     ![Editor de transformación: asignaciones de limpieza de DQS](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "Editor de transformación: asignaciones de limpieza de DQS")  
  
11. En el panel inferior, asigne estas columnas mediante las listas desplegables en el **dominio** columna:  
  
    |columna|Dominio|  
    |------------|------------|  
    |Nombre de proveedor|Nombre de proveedor|  
    |ContactEmailAddress|Póngase en contacto con el correo electrónico|  
    |Address Line|Address Line|  
    |City|City|  
    |State|State|  
    |País|País|  
    |Zip Code|Zip|  
  
12. Haga clic en **Aceptar** para cerrar el **Editor de transformación limpieza de DQS** cuadro de diálogo.  
  
## <a name="next-step"></a>Paso siguiente  
 [Tarea 8: Agregar la transformación División condicional para dividir el resultado de limpieza](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
