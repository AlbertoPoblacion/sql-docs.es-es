---
title: Abrir una plantilla | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b00a531c3b8abde6e9728039ece1de6a1866d3d2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63071874"
---
# <a name="open-a-template"></a>Abrir una plantilla
  Puede abrir una plantilla desde el Explorador de plantillas.  
  
## <a name="to-open-a-template-from-template-explorer"></a>Para abrir una plantilla desde el Explorador de plantillas  
 Puede abrir plantillas desde el Explorador de plantillas.  
  
1.  Para abrir el Explorador de plantillas, en el menú **Ver** , haga clic en **Explorador de plantillas**.  
  
2.  En la lista de categorías de plantilla, expanda la categoría que contiene la plantilla que desea abrir.  
  
3.  Hay tres formas de abrir la plantilla:  
  
    1.  Haga doble clic en la plantilla para abrirla en una ventana del editor de código.  
  
    2.  Haga clic con el botón derecho en la plantilla y seleccione **Abrir** para abrirla en una ventana del editor de código.  
  
    3.  Arrastre la plantilla a una ventana del editor de código para agregar el código de plantilla al contenido de la ventana del editor.  
  
 Una vez abierta la plantilla, use el cuadro de diálogo **Reemplazar parámetros de plantilla** para reemplazar los parámetros de la plantilla por sus valores.  
  
 Si la apertura de una plantilla inicia una nueva ventana del editor, la ventana se abrirá con las credenciales de la conexión activa actual. Por ejemplo, si se centra en una instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] en el Explorador de objetos al abrir la plantilla CREATE DATABASE, se abrirá una nueva ventana del editor mediante una conexión a dicha instancia. Si no hay ninguna conexión activa, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] presentará un cuadro de diálogo de inicio de sesión.  
  
## <a name="see-also"></a>Vea también  
 [Explorador de plantillas](template-explorer.md)   
 [Reemplazar parámetros de plantilla](replace-template-parameters.md)  
  
  
