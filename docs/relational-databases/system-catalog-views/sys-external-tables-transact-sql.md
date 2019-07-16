---
title: Sys.external_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c26dbafb76ecf318fa497e11ccac09e800691900
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054316"
---
# <a name="sysexternaltables-transact-sql"></a>Sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contiene una fila por cada tabla externa en la base de datos actual.  
  
|Nombre de la columna|Tipo de datos|Descripción|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|\<hereda columnas >||Para obtener una lista de columnas que hereda esta vista, consulte [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|Id. de columna máximo usado jamás para esta tabla.||  
|uses_ansi_nulls|**bit**|La tabla se creó con la opción de base de datos SET ANSI_NULLS establecida en ON.||  
|data_source_id|**int**|Id. de objeto para el origen de datos externo.||  
|file_format_id|**int**|Para las tablas externas a través de un origen de datos externo de HADOOP, es el identificador de objeto para el formato de archivo externo.||  
|ubicación|**nvarchar(4000)**|Para las tablas externas a través de un origen de datos externo de HADOOP, esto es la ruta de acceso de los datos externos en HDFS.||  
|reject_type|**tinyint**|Para las tablas externas a través de un origen de datos externo de HADOOP, esta es la manera en que se cuentan las filas rechazadas al consultar datos externos.|VALOR: el número de filas rechazadas.<br /><br /> PORCENTAJE: el porcentaje de filas rechazadas.|  
|reject_value|**float**|Para las tablas externas a través de un origen de datos externo de HADOOP:<br /><br /> Para *reject_type =* valor, este es el número de rechazos de fila que se permiten antes de establecer la consulta.<br /><br /> Para *reject_type* = porcentaje, este es el porcentaje de rechazos de fila que se permiten antes de establecer la consulta.||  
|reject_sample_value|**int**|Para *reject_type* = porcentaje, este es el número de filas que se va a cargar, ya sea correcta o incorrectamente, antes de calcular el porcentaje de filas rechazadas.|NULL si reject_type = VALUE.|  
|distribution_type|**int**|Para las tablas externas a través de un origen de datos externos SHARD_MAP_MANAGER, esta es la distribución de datos de las filas entre las tablas base subyacentes.|0 - particionadas<br /><br /> 1 - replicado<br /><br /> 2 - Round robin|  
|distribution_desc|**nvarchar(120)**|Para las tablas externas a través de un origen de datos externos SHARD_MAP_MANAGER, este es el tipo de distribución que se muestra como una cadena.||  
|sharding_column_id|**int**|Para las tablas externas a través de un origen de datos externos SHARD_MAP_MANAGER y una distribución con particiones, se trata del Id. de columna de la columna que contiene los valores de clave de particionamiento.||  
|remote_schema_name|**sysname**|Para las tablas externas a través de un origen de datos externos SHARD_MAP_MANAGER, éste es el esquema donde se encuentra la tabla base en las bases de datos remotos (si difiere del esquema donde se define la tabla externa).||  
|remote_object_name|**sysname**|Para las tablas externas a través de un origen de datos externos SHARD_MAP_MANAGER, este es el nombre de la tabla base en las bases de datos remotos (si es diferente del nombre de la tabla externa).||  
  
## <a name="permissions"></a>Permisos  
 La visibilidad de los metadatos en las vistas de catálogo se limita a los elementos protegibles y que son propiedad de un usuario o sobre los que el usuario tiene algún permiso. Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
