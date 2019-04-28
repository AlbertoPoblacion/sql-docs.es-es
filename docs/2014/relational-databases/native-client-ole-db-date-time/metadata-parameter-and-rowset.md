---
title: Parámetros y metadatos del conjunto de filas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b96876a050f9ba46363792eec22d76640ee6fc2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62655631"
---
# <a name="parameter-and-rowset-metadata"></a>Parámetros y metadatos de conjuntos de filas
  En este tema se proporciona información acerca de los siguientes tipos y miembros de tipo relacionados con las mejoras de fecha y hora de OLE DB.  
  
-   Estructura DBBINDING  
  
-   `ICommandWithParameters::GetParameterInfo`  
  
-   `ICommandWithParameters::SetParameterInfo`  
  
-   `IColumnsRowset::GetColumnsRowset`  
  
-   `IColumnsInfo::GetColumnInfo`  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 La siguiente información se devuelve en la estructura DBPARAMINFO mediante *prgParamInfo*:  
  
|Tipo de parámetro|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Desactivar|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Establecer|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Desactivar|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Desactivar|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19,21..27|0..7|Establecer|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26,28..34|0..7|Establecer|  
  
 Observe que en algunos casos los intervalos de valores no son continuos. Esto se debe a la adición de un separador decimal cuando la precisión fraccionaria es mayor que cero.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE solo es válido cuando se conecta a un servidor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o posteriores). DBPARAMFLAGS_SS_ISVARIABLESCALE no se establece nunca cuando se conecta a servidores de nivel inferior.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo y tipos de parámetro implícitos  
 La información que se proporciona en la estructura DBPARAMBINDINFO debe cumplir lo siguiente:  
  
|*pwszDataSourceType*<br /><br /> (depende del proveedor)|*pwszDataSourceType*<br /><br /> (OLE DB genérico)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Omitido|  
|date|DBTYPE_DBDATE|6|Omitido|  
||DBTYPE_DBTIME|10|Omitido|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Omitido|  
|datetime||16|Omitido|  
|datetime2 o DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 El *bPrecision* parámetro se omite.  
  
 No se tiene en cuenta "DBPARAMFLAGS_SS_ISVARIABLESCALE" al enviar los datos al servidor. Las aplicaciones pueden exigir el uso de tipos heredados de flujo TDS mediante los nombres de tipo específico del proveedor "`datetime`" y "`smalldatetime`". Cuando se conecta a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o posterior) de los servidores, "`datetime2`"se usará el formato e implícita de servidor se producirá una conversión, si es necesario, cuando el nombre de tipo es"`datetime2`" o "DBTYPE_DBTIMESTAMP". *bScale* se omite si los nombres de tipo específico del proveedor "`datetime`"o"`smalldatetime`" se usan. En caso contrario, las aplicaciones deben asegurarse que *bScale* se ha establecido correctamente. Las aplicaciones actualizadas de MDAC y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client desde [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] que usan "DBTYPE_DBTIMESTAMP" se producirá un error si no se establece *bScale* correctamente. Cuando esté conectado a las instancias de servidor anteriores a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], un valor *bScale* que no sea 0 o 3 con "DBTYPE_DBTIMESTAMP" es un error y se devolverá E_FAIL.  
  
 Cuando no se llama a ICommandWithParameters:: SetParameterInfo, el proveedor implica el servidor escriba en el tipo de enlace como se especifica en IAccessor:: CreateAccessor como sigue:  
  
|Tipo de enlace|*pwszDataSourceType*<br /><br /> (depende del proveedor)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|date|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 `IColumnsRowset::GetColumnsRowset` devuelve las columnas siguientes:  
  
|Tipo de columna|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Desactivar|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Establecer|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Desactivar|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Desactivar|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Establecer|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Establecer|  
  
 DBCOLUMN_FLAGS, DBCOLUMNFLAGS_ISFIXEDLENGTH es siempre TRUE para los tipos de fecha y hora, y las marcas siguientes son siempre FALSE:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Se pueden establecer las marcas restantes (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE y DBCOLUMNFLAGS_WRITEUNKNOWN), dependiendo de cómo se defina la columna y la consulta real.  
  
 Se proporciona una nueva marca DBCOLUMNFLAGS_SS_ISVARIABLESCALE en DBCOLUMN_FLAGS para permitir que una aplicación determine el tipo de servidor de columnas, donde DBCOLUMN_TYPE es DBTYPE_DBTIMESTAMP. DBCOLUMN_SCALE o DBCOLUMN_DATETIMEPRECISION también se debe usar para identificar el tipo de servidor.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE solo es válido cuando se conecta a un servidor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o posteriores). DBCOLUMNFLAGS_SS_ISVARIABLESCALE no está definido cuando se conecta a servidores de nivel inferior.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 La estructura DBCOLUMNINFO devuelve la información siguiente:  
  
|Tipo de parámetro|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Desactivar|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Establecer|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Desactivar|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Desactivar|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Establecer|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Establecer|  
  
 En *dwFlags*, DBCOLUMNFLAGS_ISFIXEDLENGTH siempre es TRUE para los tipos de fecha y hora, y las marcas siguientes son siempre FALSE:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 Se pueden establecer las marcas restantes (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE y DBCOLUMNFLAGS_WRITEUNKNOWN).  
  
 Se proporciona una nueva marca DBCOLUMNFLAGS_SS_ISVARIABLESCALE en *dwFlags* para permitir que una aplicación determine el tipo de servidor de columnas, donde *wType* es DBTYPE_DBTIMESTAMP. *bScale* también tiene que usarse para identificar el tipo de servidor.  
  
## <a name="see-also"></a>Vea también  
 [Metadatos &#40;OLE DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
  
  
