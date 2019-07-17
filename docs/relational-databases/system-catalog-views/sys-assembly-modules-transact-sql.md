---
title: Sys.assembly_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.assembly_modules
- sys.assembly_modules_TSQL
- assembly_modules
- assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_modules catalog view
ms.assetid: 5f9e644e-8065-49a2-b53d-db7df98f70d8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 68e91d6935549bc8dd421361c092c3ad1fb01905
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118167"
---
# <a name="sysassemblymodules-transact-sql"></a>sys.assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Devuelve una fila para cada función, procedimiento o desencadenador definido por un ensamblado de Common Language Runtime (CLR). Esta vista de catálogo asigna los procedimientos almacenados, desencadenadores o funciones CLR a su implementación subyacente. Los objetos de tipo TA, AF, PC, FS y FT tienen un módulo de ensamblado asociado. Para encontrar la asociación entre el objeto y el ensamblado, puede combinar esta vista de catálogo con otras. Por ejemplo, cuando se crea un procedimiento almacenado CLR, se representa mediante una fila en **sys.objects**, una fila en **sys.procedures** (que hereda de **sys.objects**), y una fila en **sys.assembly_modules**. El propio procedimiento almacenado está representado por los metadatos de **sys.objects** y **sys.procedures**. Las referencias a la implementación de CLR subyacente del procedimiento se encuentran en **sys.assembly_modules**.  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Número de identificación del objeto de SQL. Es único en una base de datos.|  
|**assembly_id**|**int**|Id. del ensamblado desde el que se creó este módulo.|  
|**assembly_class**|**sysname**|Nombre de la clase dentro del ensamblado que define este módulo.|  
|**assembly_method**|**sysname**|Nombre del método dentro de la **assembly_class** que define este módulo.<br /><br /> Es NULL para las funciones de agregado (AF).|  
|**null_on_null_input**|**bit**|El módulo se ha declarado para generar una salida NULL para cualquier entrada NULL.|  
|**execute_as_principal_id**|**int**|Id. de la entidad de seguridad de base de datos en la que se produce el contexto de ejecución, tal como lo especifica la cláusula EXECUTE AS de la función, procedimiento almacenado o desencadenador CLR.<br /><br /> NULL = EXECUTE AS CALLER. Ésta es la opción predeterminada.<br /><br /> Identificador de la entidad especificada de la base de datos = EXECUTE AS SELF, EXECUTE AS *user_name*, o EXECUTE AS *login_name*.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Permisos  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
