---
title: Solución alternativa a la limitación de filas de Excel 2003 | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3898e4202d958c1d20d5436a143e80bb45c7490f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65577789"
---
# <a name="work-around-the-excel-2003-row-limitation"></a>Work Around the Excel 2003 Row Limitation
  En este tema se explica cómo resolver la limitación de filas de Excel 2003 al exportar informes paginados a Excel. La solución alternativa es para un informe que solo contiene una tabla.  
  
> [!IMPORTANT]  
>  La extensión de representación de [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2003 (.xls) está en desuso. Para más información, vea [Características obsoletas de SQL Server Reporting Services en SQL Server 2016](../../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
 Excel 2003 admite un máximo de 65.536 filas por hoja de cálculo. Puede evitar esta limitación si fuerza un salto de página explícito después de un número determinado de filas. El representador de Excel crea una nueva hoja de cálculo por cada salto de página explícito.  
  
### <a name="to-create-an-explicit-page-break"></a>Para crear un salto de página explícito  
  
1.  Abra el informe en [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] con el portal web de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Haga clic con el botón derecho en la fila Datos de la tabla y, después, haga clic en **Agregar grupo** > **Grupo primario** para agregar un grupo de tablas externo.  
  
     ![Seleccionar el grupo primario](../../reporting-services/report-builder/media/datarow-selectparentgroup.png "Seleccionar el grupo primario")  
  
3.  Escriba la fórmula siguiente en el cuadro de expresión **Agrupar por** y, a continuación, haga clic en **Aceptar** para agregar el grupo primario.  
  
     =Int((RowNumber(Nothing)-1)/65000)  
  
     La fórmula asigna un número a cada conjunto de 65000 filas del conjunto de datos. Cuando se define un salto de página para el grupo, la expresión produce un salto de página cada 65000 filas.  
  
     Al agregar el grupo de tablas exterior agrega una columna de grupo al informe.  
  
4.  Elimine la columna de grupo; para ello, haga clic con el botón derecho en el encabezado de columna, haga clic en **Eliminar columnas**, seleccione **Eliminar solo columnas**y, después, haga clic en **Aceptar**.  
  
     ![Eliminar un grupo de columnas](../../reporting-services/report-builder/media/groupcolumn-delete-updated.png "Eliminar un grupo de columnas")  
  
5.  Haga clic con el botón secundario en **Grupo 1** en la sección **Grupos de filas** y, a continuación, haga clic en **Propiedades de grupo**.  
  
     ![Ver propiedades de grupo](../../reporting-services/report-builder/media/groupproperties-updated.png "Ver propiedades de grupo")  
  
6.  En la página **Ordenación** del cuadro de diálogo **Propiedades de grupo** , seleccione la opción de ordenación predeterminada y haga clic en **Eliminar**.  
  
     ![Eliminar la ordenación predeterminada](../../reporting-services/report-builder/media/groupproperties-sorting-updated.png "Eliminar la ordenación predeterminada")  
  
7.  En la página **Saltos de página** , haga clic en **Entre cada instancia de un grupo** y, a continuación, haga clic en **Aceptar**.  
  
     ![Establecer saltos de página](../../reporting-services/report-builder/media/groupproperties-pagebreaks-updated.png "Establecer saltos de página")  
  
8.  Guarde el informe. Cuando lo exporta a Excel, se exporta a varias hojas de cálculo y cada hoja de cálculo contiene un máximo de 65000 filas.  
  
  
