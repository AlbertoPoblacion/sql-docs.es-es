---
title: Nueva columna de salida de sp_helptrigger podría afectar las aplicaciones | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c7ad878072f8139cc95d6dc34c01f5f48835774a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63067603"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>La nueva columna de la salida de sp_helptrigger podría afectar a las aplicaciones
  procedimiento almacenado de trigger_schemaias la última columna del conjunto de resultados devuelto por el sistema sp_helptrigger.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Para obtener más información acerca de los desencadenadores definidos en una tabla determinada, consulte la vista de catálogo sys.triggers.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Acción correctora  
 Revise el uso de sp_helptrigger en las aplicaciones. Puede que tenga que modificar las aplicaciones para que se ajusten a la columna adicional. O bien, puede utilizar en su lugar la vista de catálogo sys.triggers.  
  
## <a name="see-also"></a>Vea también  
 [Problemas de actualización de motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Asesor de actualizaciones de SQL Server 2014 &#91;nuevo&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
