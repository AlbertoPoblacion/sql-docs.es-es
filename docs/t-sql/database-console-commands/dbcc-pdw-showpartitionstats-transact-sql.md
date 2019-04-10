---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7b80b96436b8cc7346a69a8b2448ade60dd009b5
ms.sourcegitcommit: 3cfedfeba377560d460ca3e42af1e18824988c07
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042304"
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Muestra el tamaño y el número de filas de cada partición de una tabla en una base de datos [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Icono de vínculo a artículos](../../database-engine/configure-windows/media/topic-link.gif "Article link icon") [Convenciones de sintaxis de Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Argumentos  
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 Nombre de una, dos o tres partes de la tabla que se va a mostrar.  En el caso de los nombres de tabla de dos o tres partes, el nombre debe incluirse entre comillas dobles (""). El uso de comillas en un nombre de tabla de una parte es opcional.  
  
## <a name="permissions"></a>Permisos
Requiere el permiso **VIEW SERVER STATE**.
  
## <a name="result-sets"></a>Conjuntos de resultados  
Este conjunto es el resultado del comando DBCC PDW_SHOWPARTITIONSTATS.
  
|Nombre de la columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|partition_number|INT|Número de partición.|  
|used_page_count|BIGINT|Número de páginas usadas para los datos.|  
|reserved_page_count|BIGINT|Número de páginas reservadas para la partición.|  
|row_count|BIGINT|Número de filas de la partición.|  
|pdw_node_id|INT|Nodo de proceso de los datos.|  
|distribution_id|INT|Identificador de distribución de los datos.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Ejemplos de sintaxis básica de DBCC PDW_SHOWPARTITIONSTATS  
Los ejemplos siguientes muestran el espacio usado y el número de filas por partición de la tabla FactInternetSales de la base de datos [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>Vea también
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)  
 
