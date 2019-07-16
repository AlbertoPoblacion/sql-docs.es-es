---
title: sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9f883b7eafc59a3d9d93541e07fe4c4db08b9c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950594"
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información detallada de nivel de artículo sobre una sesión determinada de Agente de mezcla de replicación, que se utiliza para supervisar la replicación de mezcla. El conjunto de resultados incluye una fila de detalles para cada artículo sincronizado durante la sesión. También incluye una fila que representa la inicialización de la sesión y filas que resumen las fases de carga y descarga de la sesión. Este procedimiento almacenado se ejecuta en el distribuidor de la base de datos de distribución o en el suscriptor de la base de datos de suscripciones.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @session_id = ] session_id` Especifica una sesión de agente. *session_id* es **int** no tiene ningún valor predeterminado.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Es la fase de la sesión de sincronización, que puede ser:<br /><br /> **0** = inicialización o fila de resumen<br /><br /> **1** = carga<br /><br /> **2** = descarga|  
|**ArticleName**|**sysname**|Es el nombre del artículo que se va a sincronizar. **ArticleName** también contiene información de resumen para las filas del conjunto de resultados que no representan detalles del artículo.|  
|**PercentComplete**|**decimal**|Indica el porcentaje de los cambios totales aplicados en una fila determinada de detalles del artículo para las sesiones en ejecución o con errores.|  
|**RelativeCost**|**decimal**|Indica el tiempo dedicado a la sincronización del artículo como porcentaje del tiempo de sincronización total para la sesión.|  
|**Duración**|**int**|Duración de la sesión de agente.|  
|**Inserts**|**int**|Número de inserciones de cada sesión.|  
|**Actualizaciones**|**int**|Número de actualizaciones de cada sesión.|  
|**Eliminaciones**|**int**|Número de eliminaciones de cada sesión.|  
|**Conflictos**|**int**|Número de conflictos ocurridos en una sesión.|  
|**ErrorID**|**int**|Identificador de un error de la sesión.|  
|**SeqNo**|**int**|Orden de las sesiones en el conjunto de resultados.|  
|**RowType**|**int**|Indica el tipo de información que representa cada fila del conjunto de resultados.<br /><br /> **0** = inicialización<br /><br /> **1** = resumen de la carga<br /><br /> **2** = detalles de la carga de artículo<br /><br /> **3** = resumen de la descarga<br /><br /> **4** = detalles de descarga del artículo|  
|**Modificar esquema**|**int**|Número de cambios de esquema de cada sesión.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_replmonitorhelpmergesessiondetail** se usa para supervisar la replicación de mezcla.  
  
 Cuando se ejecuta en el suscriptor, **sp_replmonitorhelpmergesessiondetail** sólo devuelve información detallada acerca de las últimas 5 sesiones del agente de mezcla.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **db_owner** o **replmonitor** fijo de base de datos en la base de datos de distribución en el distribuidor o en la base de datos de suscripción en el suscriptor pueden ejecutar **sp_ replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>Vea también  
 [Supervisar la replicación mediante programación](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
