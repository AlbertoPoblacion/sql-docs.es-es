---
title: Metadatos de parámetros con valores de tabla adicionales | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7b9aea58b56308764f907f8cf54bf74bb0663c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200576"
---
# <a name="additional-table-valued-parameter-metadata"></a>Metadatos de parámetros con valores de tabla adicionales
  Para recuperar metadatos para un parámetro con valores de tabla, una aplicación llama a SQLProcedureColumns. Para un parámetro con valores de tabla, SQLProcedureColumns devuelve una sola fila. Dos adicionales [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-se han agregado columnas específicas, SS_TYPE_CATALOG_NAME y SS_TYPE_SCHEMA_NAME, para proporcionar información de esquema y catálogo de tipos de tabla asociados a parámetros con valores de tabla. De acuerdo con la especificación ODBC, SS_TYPE_CATALOG_NAME y SS_TYPE_SCHEMA_NAME aparecen antes de todas las columnas específicas del controlador agregadas en versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y después de todas las columnas asignadas por el propio ODBC.  
  
 En la tabla siguiente se enumeran las columnas que son significativas para los parámetros con valores de tabla.  
  
|Nombre de columna|Tipo de datos|Valor/comentarios|  
|-----------------|---------------|---------------------|  
|DATA_TYPE|Smallint no NULL|SQL_SS_TABLE|  
|TYPE_NAME|WVarchar (128) no NULL|El nombre del tipo del parámetro con valores de tabla.|  
|COLUMN_SIZE|Integer|NULL|  
|BUFFER_LENGTH|Integer|0|  
|DECIMAL_DIGITS|Smallint|NULL|  
|NUM_PREC_RADIX|Smallint|NULL|  
|NULLABLE|Smallint no NULL|SQL_NULLABLE|  
|REMARKS|Varchar|NULL|  
|COLUMN_DEF|WVarchar(4000)|NULL|  
|SQL_DATA_TYPE|Smallint no NULL|SQL_SS_TABLE|  
|SQL_DATETIME_SUB|Smallint|NULL|  
|CHAR_OCTET_LENGTH|Integer|NULL|  
|ORDINAL_POSITION|Integer no NULL|La posición ordinal del parámetro.|  
|IS_NULLABLE|Varchar|"YES"|  
|SS_TYPE_CATALOG_NAME|WVarchar (128) no NULL|El catálogo que contiene la definición del tipo de tabla del parámetro con valores de tabla.|  
|SS_TYPE_SCHEMA_NAME|WVarchar (128) no NULL|El esquema que contiene la definición del tipo de tabla del parámetro con valores de tabla.|  
  
 Las columnas WVarchar se definen como Varchar en la especificación de ODBC, pero realmente se devuelven como WVarchar en todos los controladores ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recientes.  Este cambio se realizó cuando se agregó la compatibilidad con Unicode a la especificación de ODBC 3.5, pero no se declaró de forma explícita.  
  
 Para obtener metadatos adicionales para los parámetros con valores de tabla, una aplicación usa las funciones de catálogo SQLColumns y SQLPrimaryKeys. Antes de llamar a estas funciones para los parámetros con valores de tabla, la aplicación debe establecer el atributo SQL_SOPT_SS_NAME_SCOPE de la instrucción en SQL_SS_NAME_SCOPE_TABLE_TYPE. Este valor indica que la aplicación necesita metadatos para un tipo de tabla en lugar de una tabla real. La aplicación, a continuación, pasa el TYPE_NAME del parámetro con valores de tabla como el *TableName* parámetro. SS_TYPE_CATALOG_NAME y SS_TYPE_SCHEMA_NAME se utilizan con el *CatalogName* y *SchemaName* parámetros, respectivamente, para identificar el catálogo y esquema para el parámetro con valores de tabla. Cuando una aplicación ha terminado de recuperar los metadatos para los parámetros con valores de tabla, debe volver a establecer SQL_SOPT_SS_NAME_SCOPE en su valor predeterminado de SQL_SS_NAME_SCOPE_TABLE.  
  
 Si SQL_SOPT_SS_NAME_SCOPE está establecido en SQL_SS_NAME_SCOPE_TABLE, las consultas a los servidores vinculados producen un error. Se producirá un error en las llamadas a SQLColumns o SQLPrimaryKeys con un catálogo que contiene un componente de servidor.  
  
## <a name="see-also"></a>Vea también  
 [Parámetros con valores de tabla &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
