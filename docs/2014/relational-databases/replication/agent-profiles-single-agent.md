---
title: Perfiles de agente (un solo agente) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4c6d6c421e976290f17a3e49848a1600445a7da1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186970"
---
# <a name="agent-profiles-single-agent"></a>Perfiles de agente (un solo agente)
  Use el cuadro de diálogo **Perfiles de agente** para administrar los perfiles de un agente. Los perfiles de agente proporcionan una manera cómoda de administrar los parámetros en tiempo de ejecución para cada agente. Cada agente tiene un perfil predeterminado y algunos tienen perfiles adicionales predefinidos. Por ejemplo, el Agente de mezcla tiene un perfil de "vínculo lento" diseñado para conexiones de banda ancha lentas. Los perfiles predefinidos son suficientes para la mayoría de las aplicaciones, pero también pueden crearse perfiles definidos por el usuario, que permiten personalizar el comportamiento del agente.  
  
## <a name="options"></a>Opciones  
 **Predeterminado para nuevos**  
 Seleccione el perfil que se utilizará al crear los trabajos de un determinado tipo de agente. Por ejemplo, si crea varias suscripciones para una publicación de combinación, el trabajo del Agente de mezcla de cada suscripción utilizará el perfil seleccionado. Si desea cambiar el perfil de los trabajos existentes, seleccione un perfil y, a continuación, haga clic en **Cambiar agentes existentes**.  
  
 **Name**  
 El nombre del perfil.  
  
 **Tipo**  
 Tipo de perfil: **Usuario** (definido por el usuario) o **System** (predefinido).  
  
 **Propiedades (...)**  
 Haga clic para ver los valores utilizados por cada parámetro en el perfil del agente.  
  
 **Nueva**  
 Haga clic para crear un perfil nuevo.  
  
 **Eliminar**  
 Seleccione un perfil definido por el usuario y, a continuación, haga clic en **Eliminar** para eliminar ese perfil. Los perfiles predefinidos no se pueden eliminar.  
  
 **Cambiar agentes existentes**  
 Seleccione un perfil y, a continuación, haga clic en **Cambiar agentes existentes** para especificar que todos los trabajos existentes de un determinado tipo de agente deben utilizar el perfil seleccionado. Por ejemplo, si ha creado varias suscripciones para una publicación de combinación y desea cambiar el perfil para especificar que el trabajo del Agente de mezcla de cada una de esas suscripciones debe utilizar el **Perfil de agente de conexión lenta**, seleccione ese perfil y, a continuación, haga clic en **Cambiar agentes existentes**.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con perfiles del Agente de replicación](agents/work-with-replication-agent-profiles.md)   
 [Replication Agents Overview](agents/replication-agents-overview.md)  (Información general sobre los agentes de replicación)  
 [Perfiles del Agente de replicación](agents/replication-agent-profiles.md)  
  
  
