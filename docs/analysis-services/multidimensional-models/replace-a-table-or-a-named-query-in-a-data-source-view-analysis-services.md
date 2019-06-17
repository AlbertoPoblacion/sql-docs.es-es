---
title: Reemplazar una tabla o una consulta con nombre en una vista del origen de datos (Analysis Services) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a171eafc35446f588d64c74457792912dcebe75a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641119"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a>Reemplazar una tabla o una consulta con nombre en una vista del origen de datos (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  En el Diseñador de vistas del origen de datos, puede reemplazar una tabla, una vista o una consulta con nombre de una vista del origen de datos (DSV) por una vista o tabla diferente del mismo origen de datos o de otro, o por una consulta con nombre definida en la DSV. Cuando se reemplaza una tabla, los demás objetos de la base de datos o proyecto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que contienen referencias a dicha tabla continúan haciendo referencia a ella, ya que el identificador de objeto de la tabla no cambia en la DSV. Se conservan todas las relaciones que siguen siendo pertinentes (basadas en la coincidencia de nombre y tipo de columna). Por el contrario, si elimina y luego agrega una tabla, las referencias y relaciones se pierden y se tienen que volver a crear.  
  
 Para reemplazar una tabla por otra tabla, debe tener una conexión activa a los datos de origen en el Diseñador de vistas del origen de datos en el modo de proyecto.  
  
 La mayoría de las veces, reemplaza una tabla de la vista del origen de datos por otra tabla del origen de datos. No obstante, también puede reemplazar una consulta con nombre por una tabla. Por ejemplo, ha reemplazado una tabla por una consulta con nombre y ahora desea revertir a la tabla.  
  
> [!IMPORTANT]  
>  Si cambia el nombre de una tabla en un origen de datos, siga los pasos para reemplazar una tabla y especifique la tabla cuyo nombre acaba de cambiar como el origen de la tabla correspondiente en la DSV antes de actualizar una DSV. Si se completa el proceso de reemplazo y cambio de nombre de la tabla, se conservan la tabla, las referencias de la tabla y las relaciones de la tabla en la DSV. En caso contrario, cuando actualice la DSV, se interpretará que se ha eliminado la tabla a la que se ha cambiado el nombre en el origen de datos. Para obtener más información, vea [Actualizar el esquema de una vista del origen de datos &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/refresh-the-schema-in-a-data-source-view-analysis-services.md).  
  
##  <a name="bkmk_nq"></a> Reemplazar una tabla por una consulta con nombre  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto o conéctese a la base de datos que contiene la vista del origen de datos en la que desea reemplazar una tabla o una consulta con nombre.  
  
2.  En el Explorador de soluciones, expanda la carpeta **Vistas del origen de datos** y, después, haga doble clic en la vista del origen de datos.  
  
3.  Abra el cuadro de diálogo **Crear consulta con nombre** . En el panel **Tablas** o **Diagrama** , haga clic con el botón derecho en la tabla que quiere reemplazar, seleccione **Reemplazar tabla** y, después, haga clic en **Con nueva consulta con nombre**.  
  
4.  En el cuadro de diálogo **Crear consulta con nombre** , defina la consulta con nombre y, a continuación, haga clic en **Aceptar**.  
  
5.  Guarde la vista del origen de datos modificada.  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a>Reemplazar una tabla o una consulta con nombre por una tabla  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto o conéctese a la base de datos que contiene la vista del origen de datos en la que desea reemplazar una tabla o una consulta con nombre.  
  
2.  En el Explorador de soluciones, expanda la carpeta **Vistas del origen de datos** y, después, haga doble clic en la vista del origen de datos.  
  
3.  Abra el cuadro de diálogo **Reemplazar tabla por otra tabla** . En el panel **Tablas** o **Diagrama** , haga clic con el botón derecho en la tabla o la consulta con nombre que quiere reemplazar, seleccione **Reemplazar tabla** y, después, haga clic en **Con otra tabla**.  
  
4.  En el cuadro de diálogo **Reemplazar tabla por otra tabla** :  
  
    1.  En la lista desplegable **Origen de datos** , seleccione el origen de datos que quiera.  
  
    2.  Seleccione la tabla por la que desea reemplazar la tabla o consulta con nombre.  
  
5.  Haga clic en **Aceptar**.  
  
6.  Guarde la vista del origen de datos modificada.  
  
## <a name="see-also"></a>Vea también  
 [Vistas del origen de datos en modelos multidimensionales](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
