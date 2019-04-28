---
title: sys.columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.columns_TSQL
- sys.columns
- columns_TSQL
- columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.columns catalog view
ms.assetid: 323ac9ea-fc52-4b8c-8a7e-e0e44f8ed86c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c028fe9a09ad1f0f0da06a75f8ac7e0cc02b8095
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62668971"
---
# <a name="syscolumns-transact-sql"></a>sys.columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve una fila para cada columna de un objeto que incluye columnas, como vistas o tablas. La siguiente lista incluye tipos de objetos que contienen columnas:  
  
-   Funciones de ensamblado con valores de tabla (FT)  
  
-   Funciones SQL con valores de tabla insertados (IF)  
  
-   Tablas internas (IT)  
  
-   Tablas del sistema (S)  
  
-   Funciones SQL con valores de tabla (TF)  
  
-   Tablas de usuario (U)  
  
-   Vistas (V)  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Identificador del objeto al que pertenece esta columna.|  
|NAME|**sysname**|Nombre de la columna. Es único en el objeto.|  
|column_id|**int**|Identificador de la columna. Es único en el objeto.<br /><br /> Los Id. de columna no tienen que ser secuenciales.|  
|system_type_id|**tinyint**|Id. del tipo de sistema de la columna.|  
|user_type_id|**int**|Id. del tipo de la columna, tal como lo ha definido el usuario.<br /><br /> Para devolver el nombre del tipo, unir a la [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) en esta columna de la vista de catálogo.|  
|max_length|**smallint**|Longitud máxima de la columna, en bytes.<br /><br /> -1 = la columna es de tipo de datos **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, o **xml**.<br /><br /> Para **texto** columnas, el valor max_length será 16 o el valor establecido por la opción "text in row" de sp_tableoption.|  
|precisión|**tinyint**|Precisión de la columna si basado en numerales; en caso contrario, es 0.|  
|escala|**tinyint**|La escala de la columna se basa en valores numéricos; en caso contrario, es 0.|  
|collation_name|**sysname**|Nombre de la intercalación de la columna si basados en caracteres; en caso contrario, es NULL.|  
|is_nullable|**bit**|1 = La columna acepta valores NULL.|  
|is_ansi_padded|**bit**|1 = La columna utiliza el comportamiento ANSI_PADDING ON si es de tipo character, binary o variant.<br /><br /> 0 = La columna no es de tipo character, binary o variant.|  
|is_rowguidcol|**bit**|1 = La columna se ha declarado como ROWGUIDCOL.|  
|is_identity|**bit**|1 = La columna tiene valores de identidad.|  
|is_computed|**bit**|1 = La columna es una columna calculada.|  
|is_filestream|**bit**|1 = La columna es una columna FILESTREAM.|  
|is_replicated|**bit**|1 = La columna está replicada.|  
|is_non_sql_subscribed|**bit**|1 = La columna tiene un suscriptor que no es de SQL Server.|  
|is_merge_published|**bit**|1 = La columna está publicada para mezcla.|  
|is_dts_replicated|**bit**|1 = La columna se replica con [!INCLUDE[ssIS](../../includes/ssis-md.md)].|  
|is_xml_document|**bit**|1 = El contenido es un documento XML completo.<br /><br /> 0 = el contenido es un fragmento de documento o el tipo de datos de columna no es **xml**.|  
|xml_collection_id|**int**|Distinto de cero si el tipo de datos de la columna es **xml** y se escribe el código XML. El valor será el identificador de la colección que contiene el espacio de nombres de esquema XML validación de la columna.<br /><br /> 0 = No es una colección de esquemas XML.|  
|default_object_id|**int**|Identificador del objeto de forma predeterminada, independientemente de si es un objeto independiente [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), o una restricción de valor predeterminado de nivel de columna insertada. La columna parent_object_id de un objeto predeterminado de nivel de columna insertada es una referencia a la propia tabla.<br /><br /> 0 = No hay un valor predeterminado.|  
|rule_object_id|**int**|Id. de la regla independiente enlazada a la columna mediante sys.sp_bindrule.<br /><br /> 0 = No hay ninguna regla independiente. Para las restricciones CHECK de nivel de columna, vea [sys.check_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = La columna es una columna dispersa. Para obtener más información, vea [Usar columnas dispersas](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|**bit**|1 = La columna es un conjunto de columnas. Para obtener más información, vea [Usar columnas dispersas](../../relational-databases/tables/use-sparse-columns.md).|  
|generated_always_type|**tinyint**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Identifica cuándo se genera el valor de columna (siempre será 0 para las columnas en las tablas del sistema):<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END<br /><br /> Para obtener más información, consulte [las tablas temporales &#40;bases de datos relacionales&#41;](../../relational-databases/tables/temporal-tables.md).|  
|generated_always_type_desc|**nvarchar(60)**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Descripción textual del `generated_always_type`del valor (siempre NOT_APPLICABLE para las columnas en las tablas del sistema) <br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END|  
|encryption_type|**int**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Tipo de cifrado:<br /><br /> 1 = cifrado determinista<br /><br /> 2 = cifrado aleatorio|  
|encryption_type_desc|**nvarchar(64)**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Descripción del tipo de cifrado:<br /><br /> ALEATORIO<br /><br /> DETERMINISTIC|  
|encryption_algorithm_name|**sysname**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Nombre del algoritmo de cifrado.<br /><br /> AEAD_AES_256_CBC_HMAC_SHA_512 solo se admite.|  
|column_encryption_key_id|**int**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Id. de la CEK.|  
|column_encryption_key_database_name|**sysname**|**Se aplica a**: de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDW_md](../../includes/sssds-md.md)].<br /><br /> El nombre de la base de datos donde la clave de cifrado de columna existe si es diferente de la base de datos de la columna. Es NULL si la clave existe en la misma base de datos como la columna.|  
|is_hidden|**bit**|**Se aplica a**: de [!INCLUDE[ssCurrentLong](../../includes/sscurrent-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Indica si la columna está oculta:<br /><br /> 0 = la columna normal, no ocultos, visible<br /><br /> 1 = la columna oculta|  
|is_masked|**bit**|**Se aplica a**: de [!INCLUDE[ssCurrentLong](../../includes/sscurrent-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Indica si la columna se enmascara mediante un enmascaramiento dinámico de datos:<br /><br /> 0 = la columna normal, no con máscara<br /><br /> 1 = están enmascaradas|  


 
## <a name="permissions"></a>Permisos  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas del sistema &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Consultar el catálogo del sistema SQL Server preguntas más frecuentes](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)  
  
  
