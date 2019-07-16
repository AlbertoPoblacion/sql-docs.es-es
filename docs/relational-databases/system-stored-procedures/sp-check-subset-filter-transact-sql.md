---
title: sp_check_subset_filter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_check_TSQL
- sp_check_subset_filter
- filter
- subset
- subset_TSQL
- sp_check
- sp_check_subset_filter_TSQL
helpviewer_keywords:
- sp_check_subset_filter
ms.assetid: 525cfcfc-f317-478d-ba84-72e62285f160
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa956275619286c059dacf25a5b9b2b83ed732e6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070524"
---
# <a name="spchecksubsetfilter-transact-sql"></a>sp_check_subset_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Se utiliza para comprobar una cláusula de filtro en una tabla para determinar si es válida para esa tabla. Este procedimiento almacenado devuelve información sobre el filtro suministrado, incluso si el filtro es apto para su uso con particiones precalculadas. Este procedimiento almacenado se ejecuta en el publicador de la base de datos que contiene la publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_check_subset_filter [ @filtered_table = ] 'filtered_table'  
        , [ @subset_filterclause = ] 'subset_filterclause'  
    [ , [ @has_dynamic_filters = ] has_dynamic_filters OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @filtered_table = ] 'filtered_table'` Es el nombre de una tabla filtrada. *filtered_table* es **nvarchar (400)** , no tiene ningún valor predeterminado.  
  
`[ @subset_filterclause = ] 'subset_filterclause'` Se está probando la cláusula de filtro. *subset_filterclause* es **nvarchar (1000)** , no tiene ningún valor predeterminado.  
  
`[ @has_dynamic_filters = ] has_dynamic_filters` Es si la cláusula de filtro es un filtro de fila con parámetros. *has_dynamic_filters* es **bit**, su valor predeterminado es null y es un parámetro de salida. Devuelve un valor de **1** cuando la cláusula de filtro es un filtro de fila con parámetros.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Es si la publicación cumple los requisitos para usar particiones precalculadas; donde **1** significa que las particiones precalculadas pueden estar usando, y **0** significa que no puede utilizarse.|  
|**has_dynamic_filters**|**bit**|Si la cláusula de filtro suministrada incluye al menos un filtro de fila con parámetros; donde **1** significa que se utiliza un filtro de fila con parámetros, y **0** significa que no se utiliza una función de ese tipo.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Lista de las funciones de la cláusula de filtro que filtran un artículo dinámicamente; las funciones están separadas por puntos y comas.|  
|**uses_host_name**|**bit**|Si el [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) función se utiliza en la cláusula de filtro, donde **1** significa que esta función está presente.|  
|**uses_suser_sname**|**bit**|Si el [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) función se utiliza en la cláusula de filtro, donde **1** significa que esta función está presente.|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_check_subset_filter** se utiliza en la replicación de mezcla.  
  
 **sp_check_subset_filter** se puede ejecutar en cualquier tabla, incluso si no se publica la tabla. Este procedimiento almacenado se puede utilizar para comprobar una cláusula de filtro antes de definir un artículo filtrado.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos se puede ejecutar **sp_check_subset_filter**.  
  
## <a name="see-also"></a>Vea también  
 [Optimizar el rendimiento de los filtros con parámetros con particiones calculadas previamente](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)  
  
  
