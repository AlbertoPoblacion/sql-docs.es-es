---
title: Especifique una versión como la versión más reciente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f34631e979ded7a329939c23a758ccc0c9aea959
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "62773481"
---
# <a name="specify-a-version-as-the-latest-version"></a>Especificar una versión como última versión
  Al proteger un archivo en el control de código fuente, la versión protegida se convierte en la última; los usuarios que desprotegen o recuperan la última versión reciben copias locales del elemento protegido más recientemente.  
  
 Sin embargo, en algunas situaciones, quizás desee designar una versión anterior de un elemento como la última. Por ejemplo, desprotege un archivo, lo modifica y, a continuación, lo protege. Posteriormente decide descartar las modificaciones. Puesto que ha protegido el elemento, deshacer la desprotección original no es una opción. En estos casos, puede designar la versión que desprotegió originalmente como última versión del elemento.  
  
 Para designar la última versión puede:  
  
-   **Anclar una versión**. Al fijar una versión de un archivo, las versiones más recientes que la fijada no se eliminan. Además, es posible liberar un archivo que se ha fijado anteriormente. Al hacer esto, la versión del archivo que se ha protegido más recientemente se convierte en la última. No obstante, no es posible desproteger un archivo fijado.  
  
-   **Revertir a una versión especificada**. Al revertir a una versión, todas las versiones posteriores se eliminan del control de código fuente. A continuación, se puede desproteger la última versión que queda.  
  
### <a name="to-pin-a-version"></a>Para fijar una versión  
  
1.  En [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], abra la solución.  
  
2.  En el Explorador de soluciones, seleccione el archivo que desea especificar como última versión.  
  
3.  En el menú **archivo** , seleccione **control de código fuente** y haga clic en **ViewHistory**.  
  
4.  En el cuadro **de diálogo historial de> de** \<archivos, seleccione la versión que desea especificar como última y haga clic en **anclar**.  
  
     Aparece un símbolo junto a la versión seleccionada que indica que ésta es la versión actual del archivo. Si tiene cargada una versión distinta en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], se le pedirá que vuelva a cargar el archivo.  
  
### <a name="to-roll-back-to-a-version"></a>Para revertir a una versión  
  
1.  En [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], abra la solución.  
  
2.  En el Explorador de soluciones, seleccione el elemento que desea especificar como última versión.  
  
3.  En el menú **archivo** , seleccione **control de código fuente** y haga clic en **historial**.  
  
4.  En el cuadro de diálogo **Opciones de historial** , haga clic en **Aceptar** para mostrar el cuadro **de diálogo historial del archivo** .  
  
5.  En el cuadro **historial de archivo** , seleccione la versión que desea especificar como última versión y haga clic en **revertir**.  
  
     Aparece un mensaje diciendo que todas las versiones siguientes a la seleccionada serán eliminadas.  
  
6.  Haga clic en **sí** para revertir a la versión seleccionada.  
  
## <a name="see-also"></a>Consulte también  
 [Administrar protecciones](../../2014/database-engine/manage-checkins.md)   
 [Proteger archivos](../../2014/database-engine/check-in-files.md)  
  
  
