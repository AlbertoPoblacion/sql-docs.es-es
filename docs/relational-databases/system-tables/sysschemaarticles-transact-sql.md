---
title: sysschemaarticles (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysschemaarticles_TSQL
- sysschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysschemaarticles system table
ms.assetid: 67a1c039-c283-4a9c-bacc-b9b3973590c3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa29325540bbf30c69a46990a9fa473ca6cff84b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="sysschemaarticles-transact-sql"></a>sysschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Realiza un seguimiento de los artículos de solo esquema para publicaciones transaccionales y de instantáneas. Esta tabla se almacena en la base de datos de publicación.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|El identificador de artículo.|  
|**creation_script**|**nvarchar(255)**|Ruta de acceso y nombre de un script del esquema del artículo que se utiliza para crear la tabla de destino.|  
|**Descripción**|**nvarchar(255)**|La entrada descriptiva del artículo.|  
|**dest_object**|**sysname**|Nombre del objeto en la base de datos de suscripciones si el artículo es de solo esquema, como un procedimiento almacenado, una vista o una UDF.|  
|**Nombre**|**sysname**|Nombre del artículo de solo esquema de una publicación.|  
|**ObjID**|**int**|Identificador de objeto del objeto base del artículo. Puede ser el identificador de objeto de un procedimiento, una vista, una vista indizada o una UDF.|  
|**pubid**|**int**|El identificador de la publicación.|  
|**pre_creation_cmd**|**tinyint**|Especifica lo que debería hacer el sistema si detecta un objeto existente con el mismo nombre en el suscriptor cuando se aplica la instantánea para este artículo:<br /><br /> **0** = nothing.<br /><br /> **1** = eliminar la tabla de destino.<br /><br /> **2** = tabla de destino de colocación.<br /><br /> **3** = destino truncate table.|  
|**status**|**int**|Mapa de bits utilizado para indicar el estado del artículo.|  
|**tipo**|**tinyint**|Valor que indica el tipo de artículo de solo esquema:<br /><br /> **32** = procedimiento almacenado.<br /><br /> **64** = vista o vista indizada. <br /><br /> **96** = función de agregado.<br /><br /> **128** = función.|  
|**schema_option**|**binary (8)**|Máscara de bits de la opción de generación del esquema para el artículo dado. Especifica la creación automática del procedimiento almacenado en la base de datos de destino para todas las sintaxis CALL/MCALL/XCALL, y puede ser el resultado OR bit a bit lógico de uno o más de estos valores:<br /><br /> **0 x 00** = deshabilita el scripting por el agente de instantáneas y se utiliza *creation_script*.<br /><br /> **0 x 01** = genera la creación del objeto (CREATE TABLE, CREATE PROCEDURE etc.). Este valor es el predeterminado en los artículos de procedimientos almacenados.<br /><br /> **0 x 02** = genera procedimientos almacenados personalizados para el artículo, si ha definido.<br /><br /> **0 x 10** = genera un índice clúster correspondiente.<br /><br /> **0 x 20** = convierte los tipos de datos definidos por el usuario para tipos de datos base.<br /><br /> **0 x 40**= genera correspondiente uno o varios índices no clúster.<br /><br /> **0 x 80**= incluye la integridad referencial declarada para las claves principales.<br /><br /> **0 x 73** = genera la instrucción CREATE TABLE, crea índices agrupados y no agrupados, convierte los tipos de datos definidos por el usuario a tipos de datos base y genera secuencias de comandos de procedimiento almacenado personalizado que se aplicará en el suscriptor. Este valor es el predeterminado en todos los artículos excepto en los de procedimientos almacenados.<br /><br /> **0 x 100**= replica los desencadenadores de usuario en un artículo de tabla, si ha definido.<br /><br /> **0 x 200**= replica las restricciones foreign key. Si la tabla a la que se hace referencia no forma parte de una publicación, no se replicará ninguna restricción de clave externa de una tabla publicada.<br /><br /> **0 x 400**= replica las restricciones check.<br /><br /> **0 x 800**= replica los valores predeterminados.<br /><br /> **0 x 1000**= replica la intercalación de nivel de columna.<br /><br /> **0 x 2000**= replica propiedades extendidas asociadas con el objeto de origen del artículo publicado.<br /><br /> **0 x 4000**= replica las claves únicas si están definidas en un artículo de tabla.<br /><br /> **0 x 8000**= replica la clave principal y las claves únicas de un artículo de tabla como restricciones mediante instrucciones ALTER TABLE.|  
|**dest_owner**|**sysname**|Propietario de la tabla de la base de datos de destino.|  
  
## <a name="see-also"></a>Vea también  
 [Tablas de replicación &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vistas de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
