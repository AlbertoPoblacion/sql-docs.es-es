---
title: Crear un grupo de jerarquía recursiva (Generador de informes y SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8a506442cca08dfa40cb3665571662a477ef5345
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581560"
---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a>Crear un grupo de jerarquía recursiva (Generador de informes y SSRS)
En los informes paginados de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , un grupo de jerarquía recursiva organiza los datos existentes en un único conjunto de datos de informe donde existen varios niveles jerárquicos, como puede ser la estructura de mando para las relaciones entre jefes y empleados en una jerarquía de organización.  
  
 Para poder organizar los datos de una tabla como un grupo de jerarquía recursiva, todos los datos jerárquicos deben hallarse en un único conjunto de datos, con campos independientes para el elemento que se va a agrupar y para el elemento por el que se va a agrupar. Por ejemplo, un conjunto de datos donde quiere agrupar a los empleados recursivamente bajo su jefe podría contener contenga un nombre, un nombre de empleado, un identificador de empleado y un identificador de jefe.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-create-a-recursive-hierarchy-group"></a>Para crear un grupo de jerarquía recursiva  
  
1.  En la vista Diseño, agregue una tabla y arrastre los campos del conjunto de datos que desea mostrar. Normalmente, el campo que se desea mostrar como una jerarquía se encuentra en la primera columna.  
  
2.  Haga clic con el botón secundario en cualquier lugar de la tabla para seleccionarla. El Panel de agrupación muestra el grupo de detalles para la tabla seleccionada. En el panel Grupos de filas, haga clic con el botón derecho en **Detalles**y, después, haga clic en **Editar grupo**. Se abrirá el cuadro de diálogo **Propiedades de grupo** .  
  
3.  En **Expresiones de grupo**, haga clic en **Agregar**. Aparecerá una nueva fila en la cuadrícula.  
  
4.  En la lista **Agrupar por** , escriba o seleccione el campo para agrupar.  
  
5.  Haga clic en **Avanzadas**.  
  
6.  En la lista **Primaria recursiva** , escriba o seleccione el campo por el que va a agrupar.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Ejecute el informe. El informe muestra el grupo de jerarquía recursiva, aunque no hay sangría que muestre la jerarquía.  
  
## <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a>Para dar formato a un grupo de jerarquía recursiva con niveles de sangría  
  
1.  Haga clic en el cuadro de texto que contiene el campo al que desea agregar niveles de sangría para mostrar la jerarquía con formato. Las propiedades del cuadro de texto aparecen en el panel de propiedades.  
  
    > [!NOTE]  
    >  Si el panel Propiedades no está visible, en la pestaña **Ver** , haga clic en **Propiedades** .  
  
2.  En el panel Propiedades, expanda el nodo **Relleno**, haga clic en **Izquierda** y, en la lista desplegable, seleccione **\<Expresión...>** .  
  
3.  En el panel Expresión, escriba la expresión siguiente:  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     Las propiedades de relleno requieren una cadena con el formato *nnyy*, donde *nn* es un número e *yy* es la unidad de medida. La expresión de ejemplo genera una cadena que usa la función **Level** para aumentar el tamaño del relleno según el nivel de recursividad. Por ejemplo, una fila que tenga un nivel de 1 daría lugar a un relleno de (2 + (1\*10))=12pt, y una fila que tenga un nivel de 3 se traduciría en un relleno de (2 + (3\*10))=32pt. Para obtener más información acerca de la función **Level** , vea [Level](../../reporting-services/report-design/report-builder-functions-level-function.md).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Ejecute el informe. El informe muestra una vista jerárquica de los datos agrupados.  
  
## <a name="see-also"></a>Consulte también  
 [Crear grupos de jerarquía recursiva &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)   
 [Filtrar, agrupar y ordenar datos &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Referencia a las funciones de agregado &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Tablas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Listas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tablas, matrices y listas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
