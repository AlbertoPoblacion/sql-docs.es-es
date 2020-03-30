---
title: Proporcionar una consulta de origen OData en tiempo de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa8a5454fb85c4a6bcfe53088549107f09b9772f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "71298211"
---
# <a name="provide-an-odata-source-query-at-runtime"></a>Proporcionar una consulta de origen OData en tiempo de ejecución

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 Puede modificar la consulta de origen OData en tiempo de ejecución si agrega una *expresión* a la propiedad **[OData Source].[Query]** de la tarea Flujo de datos.  
  
 Las columnas devueltas deben ser las mismas que las que se devolvieron en tiempo de diseño; de lo contrario, recibirá un error cuando se ejecute el paquete. Asegúrese de especificar las mismas columnas (en el mismo orden) cuando use la opción de consulta $select. Una alternativa más segura a la opción $select consiste en anular la selección de las columnas que no quiera usar directamente desde la interfaz de usuario del componente de origen.  
  
 Hay varias maneras de establecer de forma dinámica el valor de consulta en tiempo de ejecución. A continuación se muestran algunos de los métodos más frecuentes.  
  
## <a name="provide-the-query-as-a-parameter"></a>Proporcionar la consulta como un parámetro  
 En el procedimiento siguiente se muestra cómo exponer la consulta usada por un componente de origen OData como un parámetro del paquete.  
  
1.  Haga clic con el botón derecho en **Tarea Flujo de datos** y seleccione la opción **Parametrizar…** .  
  
2.  En el diálogo **Parametrizar**, seleccione **[\<Nombre del componente de origen OData>].[Query]** para **Propiedad**.  
  
3.  Elija si se va a **Crear nuevo parámetro** o **Usar un parámetro existente**.  
  
4.  Si selecciona **Crear nuevo parámetro**:  
  
    1.  Escriba el **nombre** y la **descripción** del parámetro.  
  
    2.  Especifique el **valor** predeterminado del parámetro.  
  
    3.  Especifique el **ámbito** (**paquete** o **proyecto**) del parámetro.  
  
    4.  Especifique si el parámetro es **obligatorio** o no  
  
5.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
## <a name="provide-the-query-with-an-expression"></a>Proporcionar la consulta con una expresión
 Este método resulta útil si desea crear dinámicamente la cadena de consulta en tiempo de ejecución.
  
1.  Seleccione la **tarea Flujo de datos** que contiene el **origen OData**.  
  
2.  En la ventana **Propiedades** , resalte la propiedad **Expresiones** .  
  
3.  Haga clic en el botón … (puntos suspensivos) para abrir el cuadro de diálogo **Editor de expresiones de propiedad**.  
  
4.  Seleccione la propiedad **[OData Source].[Query]** .  
  
5.  Haga clic en el botón … (puntos suspensivos) en el cuadro **Expresión**.  
  
6.  Escriba la **expresión**.  
  
7.  Haga clic en **OK**.  
  
> [!NOTE]  
> Cuando se usa este enfoque, debe asegurarse de que los valores establecidos están codificados correctamente como una dirección URL. Cuando reciba valores de datos proporcionados por el usuario (por ejemplo, al establecer valores de opción de consulta individuales de un parámetro), debe asegurarse de que los valores se validan para impedir posibles ataques de inyección de código SQL.  
  
  
