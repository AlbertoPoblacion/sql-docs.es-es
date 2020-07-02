---
title: Sys. fn_cdc_has_column_changed (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_has_column_changed_TSQL
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed_TSQL
- fn_cdc_has_column_changed
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed
ms.assetid: 2b9e6278-050d-4ffc-8d1a-09606180facc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e5ad2f17c31508b8d712474723af169becd794b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760243"
---
# <a name="sysfn_cdc_has_column_changed-transact-sql"></a>sys.fn_cdc_has_column_changed (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Identifica si la máscara de actualización especificada indica que se ha actualizado la columna especificada en la fila de cambio asociada.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sys.fn_cdc_has_column_changed ( 'capture_instance','column_name' , update_mask )  
```  
  
## <a name="arguments"></a>Argumentos  
 **'** *capture_instance* **'**  
 Es el nombre de la instancia de captura. *capture_instance* es de **tipo sysname**.  
  
 **'** *column_name* **'**  
 Es la columna capturada de la instancia de captura especificada para la que se creará un informe. *column_name* es de **tipo sysname**.  
  
 *update_mask*  
 Es la máscara que identifica las columnas actualizadas en cualquier fila de cambio asociada. *update_mask* es **varbinary (128)**.  
  
## <a name="return-type"></a>Tipo de valor devuelto  
 **bit**  
  
## <a name="remarks"></a>Comentarios  
 Puede utilizar esta función para extraer información de una máscara de actualización devuelta en una consulta de datos de cambio. Resulta muy útil en el procesamiento posterior de la máscara de actualización para saber si se ha modificado una columna en particular en la fila de cambio asociada. Para obtener más información, vea [Acerca de la captura de datos modificados &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md).  
  
 Cuando esta información se devuelva como parte de una consulta de datos modificados, se recomienda usar las funciones [Sys. fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md) y [Sys. fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) en lugar de esta función. Utilice la función fn_cdc_get_column_ordinal antes de consultar los datos modificados para que se calcule el ordinal de columna deseado solo una vez. Utilice fn_cdc_is_bit_set dentro de la consulta para extraer la información de la máscara de actualización para cada fila devuelta.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer al rol fijo de servidor sysadmin o al rol fijo de base de datos db_owner. Para el resto de usuarios, requiere el permiso SELECT en todas las columnas capturadas en la tabla de origen y, si se ha definido un rol de acceso para la instancia de captura, la pertenencia a ese rol de base de datos.  
  
## <a name="see-also"></a>Consulte también  
 [CDC. &#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)   
 [cdc.captured_columns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
  
  
