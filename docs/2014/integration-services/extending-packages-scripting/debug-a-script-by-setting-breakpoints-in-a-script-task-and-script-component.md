---
title: Depurar un script estableciendo puntos de interrupción en una tarea Script y un componente de script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 97c41b4ca75336f70b049239112132c89b05fba5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768491"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Depurar un script estableciendo puntos de interrupción en una tarea Script y un componente Script
  Este procedimiento describe cómo establecer puntos de interrupción en los scripts que se utilizan en la tarea Script y en el componente Script.  
  
 Después de establecer puntos de interrupción en el script, en el cuadro de diálogo **Establecer puntos de interrupción - \<nombre de objeto>** se muestran los puntos de interrupción, junto con los puntos de interrupción integrados.  
  
> [!IMPORTANT]  
>  En determinadas circunstancias, se omiten los puntos de interrupción en la tarea Script y el componente de script. Para obtener más información, consulte el **depurar la tarea Script** sección [codificar y depurar la tarea Script](../control-flow/script-task.md) y **Debugging the Script Component** sección en [código y depurar el componente de Script] (.. / extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.  
  
### <a name="to-set-a-breakpoint-in-script"></a>Para establecer un punto de interrupción en un script  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  Haga doble clic en el paquete que contiene el script en la que desea establecer puntos de interrupción.  
  
3.  Para abrir la tarea Script, haga clic en la pestaña **Flujo de control** y, a continuación, haga doble clic en la tarea Script.  
  
4.  Para abrir el componente de script, haga clic en la pestaña **Flujo de datos** y, a continuación, haga doble clic en el componente de script.  
  
5.  Haga clic en **Script** y, a continuación, en **Editar script**.  
  
6.  En [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA), ubique la línea del script en la que desea establecer un punto de interrupción, haga clic con el botón derecho en la línea, apunte al **Punto de interrupción** y haga clic en **Insertar punto de interrupción**.  
  
     El icono de punto de interrupción aparece en la línea de código.  
  
7.  En el menú **Archivo** , haga clic en **Salir**.  
  
8.  Haga clic en **Aceptar**.  
  
9. Para guardar el paquete, haga clic en **Guardar los elementos seleccionados** , en el menú **Archivo** .  
  
  
