---
title: Sys.system_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd94f90a823ba57910809a54aed470ddd0bb0010
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108859"
---
# <a name="syssystemcolumns-transact-sql"></a>sys.system_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una fila para cada columna de objetos de sistema que tienen columnas.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Identificador del objeto al que pertenece esta columna.|  
|**name**|**sysname**|Nombre de la columna. Es único en el objeto.|  
|**column_id**|**int**|Identificador de la columna. Es único en el objeto.<br /><br /> Los Id. de columna no tienen que ser secuenciales.|  
|**system_type_id**|**tinyint**|Id. del tipo de sistema de la columna|  
|**user_type_id**|**int**|Id. del tipo de la columna, tal como lo ha definido el usuario.<br /><br /> Para devolver el nombre del tipo, unir a la [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) en esta columna de la vista de catálogo.|  
|**max_length**|**smallint**|Longitud máxima (en bytes) de la columna.<br /><br /> -1 = la columna es de tipo de datos **varchar (max)** , **nvarchar (max)** , **varbinary (max)** , o **xml**.<br /><br /> Para **texto** columnas, el **max_length** valor será 16 o el valor establecido por **sp_tableoption** 'text in row'.|  
|**precisión**|**tinyint**|Precisión de la columna si basado en numerales; en caso contrario, es 0.|  
|**scale**|**tinyint**|Escala de la columna, si está basada en números; en caso contrario, es 0.|  
|**collation_name**|**sysname**|Nombre de la intercalación de la columna si basados en caracteres; en caso contrario, es NULL.|  
|**is_nullable**|**bit**|1 = La columna acepta valores NULL.|  
|**is_ansi_padded**|**bit**|1 = La columna utiliza el comportamiento ANSI_PADDING ON si es de tipo character, binary o variant.<br /><br /> 0 = La columna no es de tipo character, binary o variant.|  
|**is_rowguidcol**|**bit**|1 = La columna se ha declarado como ROWGUIDCOL.|  
|**is_identity**|**bit**|1 = columna tiene valores de identidad.|  
|**is_computed**|**bit**|1 = La columna es una columna calculada.|  
|**is_filestream**|**bit**|1 = La columna se ha declarado para utilizar el almacenamiento FILESTREAM.|  
|**is_replicated**|**bit**|1 = La columna está replicada.|  
|**is_non_sql_subscribed**|**bit**|1 = La columna tiene un suscriptor que no es de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_merge_published**|**bit**|1 = La columna está publicada para mezcla.|  
|**is_dts_replicated**|**bit**|1 = La columna se replica con [!INCLUDE[ssIS](../../includes/ssis-md.md)].|  
|**is_xml_document**|**bit**|1 = El contenido es un documento XML completo.<br /><br /> 0 = el contenido es un fragmento de documento o el tipo de datos de columna no es **xml**.|  
|**xml_collection_id**|**int**|Distinto de cero si el tipo de datos de columna es **xml** y se escribe el código XML. El valor será el identificador de la colección que contiene el espacio de nombres de esquema XML validación de la columna.<br /><br /> 0 = No es una colección de esquemas XML.|  
|**default_object_id**|**int**|Identificador del objeto de forma predeterminada, independientemente de que sea independiente [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), o una restricción de valor predeterminado de nivel de columna insertada. El **parent_object_id** columna de un objeto de valor predeterminado de nivel de columna insertada es una referencia a la propia tabla. O bien, es 0 si no hay valor predeterminado.|  
|**rule_object_id**|**int**|Id. de la regla independiente enlazada a la columna mediante **sys.sp_bindrule**.<br /><br /> 0 = No hay ninguna regla independiente.<br /><br /> Para las restricciones CHECK de nivel de columna, vea [sys.check_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = La columna es una columna dispersa. Para obtener más información, vea [Usar columnas dispersas](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|**bit**|1 = La columna es un conjunto de columnas. Para obtener más información, vea [Usar conjuntos de columnas](../../relational-databases/tables/use-column-sets.md).|  
|generated_always_type|**tinyint**|El valor numérico que representa el tipo de columna:<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar(60)**|La descripción de texto del tipo de columna:<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **Se aplica a**: desde [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Permisos  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Consultar el catálogo del sistema SQL Server preguntas más frecuentes](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [Sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
