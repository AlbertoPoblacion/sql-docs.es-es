---
title: Propiedades del servidor (página Configuración adicional del servidor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d726e1e79b1a3e24aea074c0821e1f8773b233c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809335"
---
# <a name="server-properties-misc-server-settings-page"></a>Propiedades del servidor (página Configuración adicional del servidor)
  Utilice esta página para ver o modificar la configuración del servidor.  
  
## <a name="options"></a>Opciones  
 **Idioma predeterminado para los usuarios**  
 Especifica el idioma predeterminado de los nuevos inicios de sesión creados.  
  
 **Permitir que los desencadenadores activen otros desencadenadores**  
 Controla si un desencadenador puede realizar una acción que inicie otro desencadenador. Cuando esta opción está desactivada, un desencadenador no puede activar otros desencadenadores. Si está activada, un desencadenador puede activar otros desencadenadores, hasta un máximo de 32 niveles.  
  
 **Usar el regulador de consultas para evitar consultas de ejecución prolongada**  
 Especifica un límite de tiempo para la ejecución de una consulta. El término costo de consultas hace referencia al tiempo estimado, en segundos, necesario para ejecutar una consulta en una configuración de hardware específica. De manera predeterminada, el regulador de consultas está desactivado y se pueden ejecutar todas las consultas. Si esta opción está activada, debe indicar un límite de tiempo en el cuadro de texto que aparece a continuación. Si especifica un valor positivo distinto de cero, el regulador de consultas no permitirá la ejecución de ninguna consulta que tenga un costo estimado superior al valor especificado.  
  
 **Interpretar un año de dos dígitos como comprendido entre**  
 Especifica el rango de fechas de 100 años para interpretar valores de año de dos dígitos. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpretará los valores de fecha de dos dígitos para hacer referencia al año que finaliza en los dígitos que se encuentran dentro del intervalo especificado.  
  
 Establezca el año final en el cuadro de la derecha. Cuando se guarda el año final, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muestra automáticamente el año inicial en el cuadro izquierdo.  
  
 **Valores configurados**  
 Muestra los valores configurados para las opciones de este panel. Si cambia estos valores, haga clic en **Valores actuales** para comprobar si los cambios han surtido efecto. Si los cambios no han surtido efecto, debe reiniciarse la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Valores actuales**  
 Presenta los valores actuales de las opciones de este panel. Estos valores son de solo lectura.  
  
## <a name="see-also"></a>Consulte también  
 [Opciones de configuración de servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
