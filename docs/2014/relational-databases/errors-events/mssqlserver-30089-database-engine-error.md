---
title: MSSQLSERVER_30089 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f452da206afd91c2db49d32600c34397ef7b2609
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868780"
---
# <a name="mssqlserver_30089"></a>MSSQLSERVER_30089
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre de producto|SQL Server|  
|Id. de evento|30089|  
|Origen de eventos|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|IFTS_FDHOST_TERMINATEDABNORMAL|  
|Texto del mensaje|El proceso de host de demonio de filtro (FDHost) de texto completo se ha detenido de forma anormal. Esto puede ocurrir si un componente lingüístico mal configurado o con un funcionamiento incorrecto, como un separador de palabras, un lematizador o un filtro, ha causado un error irrecuperable durante la indización de texto completo o el procesamiento de consultas. El proceso se reiniciará de forma automática.|  
  
## <a name="explanation"></a>Explicación  
 El host de demonio de filtro de texto completo ha encontrado algún problema que le ha obligado a detenerse de forma anómala. La causa del problema puede ser un documento con un formato incorrecto, un error en el filtro o en el separador de palabras, o un problema en el demonio de filtro.  
  
## <a name="user-action"></a>Acción del usuario  
 Normalmente, el demonio se recuperará del error. Si el error se produce sistemáticamente, hay que investigar y solucionar el problema. Intente la siguiente acción para solucionarlo:  
  
1.  Si se ha instalado recientemente un nuevo componente lingüístico, quítelo del sistema.  
  
2.  Examine el registro de rastreo para identificar los documentos nuevos cuya indización de texto completo no ha sido posible y quítelos.  
  
## <a name="see-also"></a>Consulte también  
 [sp_help_fulltext_system_components &#40;&#41;de Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [Configurar y administrar separadores de palabras y lematizadores para la búsqueda](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Configurar y administrar filtros para búsquedas](../search/configure-and-manage-filters-for-search.md)  
  
  
