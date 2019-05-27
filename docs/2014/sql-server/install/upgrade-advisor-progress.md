---
title: Progreso del Asesor de actualizaciones de la actualización | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 697f70d4435213a991e55adecb51a98120d8df1b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091562"
---
# <a name="upgrade-advisor-progress"></a>Progreso del Asesor de actualizaciones
  El análisis del Asesor de actualizaciones se inicia con un analizador dedicado que realiza un análisis de cada componente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que seleccionó. Cuando se analizan los componentes, se informa del progreso en el **progreso** cuadro de diálogo.  
  
## <a name="options"></a>Opciones  
 **Acción**  
 Especifica el componente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seleccionado para el análisis.  
  
 **Estado**  
 Muestra el valor de estado devuelto desde la interfaz de progreso del componente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **de mensaje**  
 Muestra el mensaje de error o de confirmación que devuelve cada analizador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Si el análisis se prolonga demasiado tiempo, puede detenerlo, salir del Asistente para análisis del Asesor de actualizaciones y, a continuación, volver a ejecutar el asistente. Para reducir el tiempo del análisis, seleccione menos componentes para analizar.  
  
 Cuando el análisis se haya completado, el informe se escribe en un archivo. Puede ver el informe, haga clic en **iniciar informe** para iniciar el Visor de informes desde esta página. Si desea ver el informe más adelante, puede abrir el **Visor de informes del Asesor de actualizaciones** desde la página de inicio del Asesor de actualizaciones.  
  
> [!NOTE]  
>  Los informes anteriores se guardan cada vez que se analice un servidor. Los informes se guardan con la marca de tiempo como nombre de archivo. El visor de informes muestra los cinco últimos informes guardados.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Iniciar el Asesor de actualizaciones](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Cómo: Ejecute al Asistente para análisis del Asesor](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Componentes de SQL Server](../../../2014/sql-server/install/sql-server-components.md)   
 [Actualización del Asistente para la referencia de la interfaz de usuario](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Trabajar con el Asesor de actualizaciones](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
