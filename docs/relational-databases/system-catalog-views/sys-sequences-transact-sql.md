---
title: Sys.sequences (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sequences_TSQL
- sys.sequences
- sequences
- sequences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sys. sequences catalog view
- sys.sequences catalog view
ms.assetid: 0e1b0e32-1cce-40f7-83c8-860ec660138a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a5efd9edac7b69a390501acce3058530b51eba7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="syssequences-transact-sql"></a>sys.sequences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una fila por cada objeto de secuencia de una base de datos.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|\<hereda columnas >||Hereda todas las columnas de [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**start_value**|**sql_variant no NULL**|El valor de inicio del objeto de secuencia. Si se reinicia el objeto de secuencia usando ALTER SEQUENCE, se reiniciará en ese valor. Cuando el objeto de secuencia ciclos, continúa en el **minimum_value** o **maximum_value**, no el **start_value**.|  
|**incremento**|**sql_variant no NULL**|El valor que se usa para incrementar el objeto de secuencia a continuación de cada valor generado.|  
|**minimum_value**|**sql_variant es NULL**|El valor mínimo que puede generar el objeto de secuencia. Después de llegar a este valor, el objeto de secuencia devolverá un error al intentar generar más valores o se reiniciará si se especifica la opción CYCLE. Si no se ha especificado MINVALUE, esta columna devuelve el valor mínimo admitido por el tipo de datos del generador de secuencias.|  
|**maximum_value**|**sql_variant es NULL**|El valor máximo que puede generar el objeto de secuencia. Después de llegar a este valor, el objeto de secuencia empezará a devolver un error al intentar generar más valores o se reiniciará si se especifica la opción CYCLE. Si no se ha especificado MAXVALUE, esta columna devuelve el valor máximo admitido por el tipo de datos del objeto de secuencia.|  
|**is_cycling**|**bits no NULL**|Devuelve 0 si se ha especificado NO CYCLE para el objeto de secuencia y 1 si se ha especificado CYCLE.|  
|**is_cached**|**bits no NULL**|Devuelve 0 si se ha especificado NO CACHE para el objeto de secuencia y 1 si se ha especificado CACHE.|  
|**cache_size**|**int NULL**|Devuelve el tamaño de memoria caché especificado para el objeto de secuencia. Esta columna contiene NULL si se creó la secuencia con la opción NO CACHE o si se especificó CACHE sin especificar ningún tamaño de memoria caché. Si el valor especificado por el tamaño de memoria caché es mayor que el número máximo de valores que puede devolver el objeto de secuencia, se sigue mostrando ese tamaño de memoria caché que no se puede obtener.|  
|**system_type_id**|**tinyint no NULL**|Identificador del tipo de sistema del tipo de datos del objeto de secuencia.|  
|**user_type_id**|**int NOT NULL**|Identificador del tipo de datos para el objeto de secuencia definido por el usuario.|  
|**precisión**|**tinyint no NULL**|Precisión máxima del tipo de datos.|  
|**escala**|**tinyint no NULL**|Escala máxima del tipo de datos. Se devuelve la escala con la precisión para proporcionar a los usuarios los metadatos completos. La escala siempre es 0 para los objetos de secuencia porque solo se permiten tipos enteros.|  
|**Current_value**|**sql_variant no NULL**|El último valor obligado. Es decir, el valor devuelto de la ejecución más reciente de la función NEXT VALUE FOR o el último valor de ejecución de la **sp_sequence_get_range** procedimiento. Devuelve el valor START WITH si nunca se ha usado la secuencia.|  
|**is_exhausted**|**bits no NULL**|0 indica que se pueden generar más valores desde la secuencia. 1 indica que el objeto de secuencia ha alcanzado el parámetro MAXVALUE y la secuencia no se ha establecido en CYCLE. La función NEXT VALUE FOR devuelve un error hasta que la secuencia la reinicie ALTER SEQUENCE.|  
  
## <a name="permissions"></a>Permissions  
 En [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y versiones posteriores, la visibilidad de los metadatos se limita a los elementos protegibles que son propiedad de un usuario o sobre los que el usuario tiene algún permiso. Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Números de secuencia](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [Crear secuencia de &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Eliminar secuencia &#40; Transact-SQL &#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [VALOR siguiente para &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [sp_sequence_get_range &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  
