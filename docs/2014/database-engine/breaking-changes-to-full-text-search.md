---
title: Cambios de interrupción en la búsqueda de texto completo ? Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- full-text catalogs [SQL Server], breaking changes
- breaking changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: c55a6748-e5d9-4fdb-9a1f-714475a419c5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 45b13c29af6a9c5e82533a4b66213d1cb1b9dd15
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "62787763"
---
# <a name="breaking-changes-to-full-text-search"></a>Cambios principales en la búsqueda de texto completo
  En este tema se describen los principales cambios producidos en la búsqueda de texto completo. Estos cambios pueden provocar errores en las aplicaciones, en los scripts o en las funcionalidades basados en versiones anteriores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Podría encontrar estos problemas al actualizar. Para obtener más información, vea [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-full-text-search-in-sssql14"></a>Cambios importantes en la búsqueda de texto completo de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 La información se proporcionará posteriormente.  
  
## <a name="breaking-changes-in-full-text-search-in-sssql11"></a>Cambios importantes en la búsqueda de texto completo de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="collation-changed-for-name-column-in-sysfulltext_languages"></a>Intercalación modificada para la columna de nombre en sys.fulltext_languages  
 La intercalación de la columna de **nombre** de idioma en la vista de catálogo [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) se ha cambiado y ha pasado de la intercalación fija de la base de datos Resource a la intercalación predeterminada que se haya seleccionado para la instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Este cambio permite comparar los valores en la columna **nombre** cuando se combina la vista de [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) con **sys.fulltext_languages**. Por ejemplo, puede consultar para todas las bases de datos donde el idioma de texto completo predeterminado es distinto del idioma predeterminado de la base de datos.  
  
## <a name="breaking-changes-in-full-text-search-in-sql-server-2008"></a>Cambios recientes en la búsqueda de texto completo de SQL Server 2008  
 Se aplican los siguientes cambios principales a la búsqueda de texto completo entre [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] y [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] y versiones posteriores.  
  
|Característica|Escenario|SQL Server 2005|SQL Server 2008 y versiones posteriores.|  
|-------------|--------------|---------------------|----------------------------------------|  
|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) con tipos definidos por el usuario (UDT)|La clave de texto completo es un tipo definido por el usuario de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], por ejemplo, `MyType = char(1)`.|La clave devuelta es del tipo asignado al tipo definido por el usuario.<br /><br /> En el ejemplo, esto sería **char(1)**.|La clave devuelta es del tipo definido por el usuario. En el ejemplo, se trata de **MyType**.|  
|*top_n_by_rank* parámetro (de las instrucciones CONTAINSTABLE y [FREETEXTTABLE)](/sql/relational-databases/system-functions/freetexttable-transact-sql) [!INCLUDE[tsql](../includes/tsql-md.md)]|*top_n_by_rank* consultas utilizando 0 como parámetro.|Produce un mensaje de error que indica que debe utilizar un valor mayor que cero.|Tiene éxito y devuelve cero filas.|  
|CONTAINSTABLE y **ItemCount**|Eliminar las filas de la tabla base antes de insertar los cambios en MSSearch.|CONTAINSTABLE devuelve el registro fantasma. **ItemCount** no se cambia.|CONTAINSTABLE no devuelve ningún registro fantasma.|  
|**ItemCount**|La tabla contiene documentos nulos o columnas de tipo.|Además de los documentos indizados, los documentos que son null o que tienen tipos nulos se cuentan en el **ItemCount** valor.|Solo los documentos indexados se cuentan en el valor **ItemCount.**|  
|Catalog **ItemCount**|Columna Blob con una extensión NULL.|Se cuenta en **ItemCount** del catálogo|No se cuenta en **ItemCount** de catálogo.|  
|**UniqueKeyCount**|Consultar un recuento de claves únicas de un catálogo, por ejemplo, dos tablas (table1 y table2) cada una con tres palabras: word1, word2 y word3.|**UniqueKeyCount** 9. En la tabla siguiente se resume cómo se alcanza este valor:<br /><br /> table1 = 3<br /><br /> EOF para el índice de texto completo de table1 = 1<br /><br /> table2 = 3<br /><br /> EOF para el índice de texto completo de table2 = 1<br /><br /> catálogo de texto completo = 1|Para cada tabla, **UniqueKeyCount** es el número de palabras clave distintas + 1 (0xFF).  Esto NO trata las mismas palabras en > 1 doc como nueva clave única.<br /><br /> Para un catálogo, **UniqueKeyCount** es la suma de **UniqueKeyCount** de cada una de las tablas del catálogo. Las palabras idénticas de las tablas diferentes se tratan como claves únicas. En este caso, el recuento de claves únicas es 8.|  
|opción de nivel de servidor de **clasificación previa**|Optimización de rendimiento de las consultas FREETEXTTABLE.|Cuando la opción se establece en 1, las consultas FREETEXTTABLE especificadas con *top_n_by_rank* utilizan datos de clasificación precalculados almacenados en los catálogos de texto completo.|No se admite.|  
|[sp_fulltext_pendingchanges](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql) al actualizar la columna de clave|Actualizar la columna de clave de texto completo en una fila de una tabla de 2 filas y ejecutar sp_fulltext_pendingchanges.|Ambas filas aparecen.|Solo aparece una fila.|  
|Funciones insertadas|Funciones insertadas con un operador de texto completo|Devuelve un mensaje de error.|Devuelve las filas pertinentes.|  
|[sp_fulltext_database](/sql/relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql)|Habilitar o deshabilitar la búsqueda de texto completo con sp_fulltext_database.|No se devuelve ningún resultado para las consultas de texto completo. Si el texto completo está deshabilitado para la base de datos, no se permiten operaciones de texto completo.|Devuelve resultados para las consultas de texto completo y las operaciones de texto completo permitidas, aun cuando el texto completo esté deshabilitado para la base de datos.|  
|Palabras irrelevantes específicas de la configuración regional|Consulta las variantes específicas de la configuración regional de un idioma principal, como el francés belga y el francés canadiense.|Las consultas que las variantes específicas de la configuración regional son procesadas por los componentes (interruptores de palabras, lematizadores y palabras de detención) de su idioma principal. Por ejemplo, los componentes de francés (Francia) se utilizan para analizar el francés (Bélgica).|Debe agregar explícitamente las palabras irrelevantes para cada identificador de configuración regional (LCID). Por ejemplo, necesitaría especificar un LCID para Bélgica, Canadá y Francia.|  
|Proceso de lematización de sinónimos|Usar el diccionario de sinónimos y formas no flexionadas (lematización).|Una palabra del diccionario de sinónimos se lematiza automáticamente después de su expansión.|Si desea la forma flexionada en la expansión, tiene que agregarla explícitamente.|  
|Ruta de acceso del catálogo de texto completo y grupo de archivos|Trabajar con catálogos de texto completo.|Cada catálogo de texto completo tiene una ruta de acceso física y pertenece a un grupo de archivos. Se trata como un archivo de base de datos.|Un catálogo de texto completo es un objeto virtual y no pertenece a ningún grupo de archivos. Un catálogo de texto completo es un concepto lógico que hace referencia a un grupo de índices de texto completo.<br /><br /> Nota: [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] Las instrucciones DDL que especifican catálogos de texto completo funcionan correctamente.|  
|[sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)|Utilizar la ruta de acceso, data_space_id y file_id de esta vista de catálogo.|Estas columnas devuelven un valor concreto.|Estas columnas devuelven NULL porque el catálogo de texto completo ya no se encuentra en el sistema de archivos.|  
|[sys.sysfulltextcatalogs](/sql/relational-databases/system-compatibility-views/sys-sysfulltextcatalogs-transact-sql)|Utilizar la columna de ruta de acceso de esta tabla del sistema desusada.|Devuelve la ruta de acceso al sistema de archivos del catálogo de texto completo.|Devuelve NULL porque el catálogo de texto completo ya no se encuentra en el sistema de archivos.|  
|[sp_help_fulltext_catalogs](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql)<br /><br /> [sp_help_fulltext_catalogs_cursor](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql)|Utilizar la columna PATH de estos procedimientos almacenados desusados.|Devuelve la ruta de acceso al sistema de archivos del catálogo de texto completo.|Devuelve NULL porque el catálogo de texto completo ya no se encuentra en el sistema de archivos.|  
|[sp_help_fulltext_catalog_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalog-components-transact-sql)|Utilizar sp_help_fulltext_catalog_components de este procedimiento almacenado.|Devuelve una lista con todos los componentes (filtros, separadores de palabras y controladores de protocolo) que se usan en los catálogos de texto completo de la base de datos actual.|Devuelve filas vacías.|  
|[DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql)|Mediante la propiedad **IsFullTextEnabled.**|El valor **IsFullTextEnabled** indica si la búsqueda de texto completo está habilitada en una base de datos determinada.|El valor de esta columna no tiene ningún efecto. En las bases de datos de usuario siempre está habilitada la búsqueda de texto completo.|  
  
## <a name="see-also"></a>Consulte también  
 [Cambios de comportamiento en la búsqueda de texto completo](../relational-databases/search/full-text-search.md)   
 [Búsqueda de texto completo](../relational-databases/search/full-text-search.md)  
  
  
