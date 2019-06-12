---
title: Cambios de copia masiva para tipos de fecha y hora mejorados (OLE DB) | Microsoft Docs
description: Cambios de copia masiva para tipos de fecha y hora mejorados (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, bulk copy operations
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 2e4291d32de1b18edb65560e21d16c76eb692f3d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66769553"
---
# <a name="bulk-copy-changes-for-enhanced-date-and-time-types-ole-db"></a>Cambios de copia masiva para tipos de fecha y hora mejorados (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  En este artículo se describe las mejoras de fecha y hora para admitir la funcionalidad de copia masiva en el controlador de OLE DB para SQL Server.  
  
## <a name="format-files"></a>Archivos de formato  
 En la tabla siguiente se describe la entrada que se usa para especificar los tipos de fecha y hora, así como los nombres de tipo de datos de archivo host correspondientes, a la hora de generar archivos de formato de forma interactiva.  
  
|tipo de almacenamiento en archivo|Tipo de datos del archivo host|Respuesta al mensaje "Especifique el tipo del campo de almacenamiento de archivo <nombre_de_campo> [\<predeterminado>]:"|  
|-----------------------|-------------------------|-----------------------------------------------------------------------------------------------------|  
|DATETIME|SQLDATETIME|d|  
|Smalldatetime|SQLDATETIM4|D|  
|date|SQLDATE|de|  
|Time|SQLTIME|te|  
|Datetime2|SQLDATETIME2|d2|  
|Datetimeoffset|SQLDATETIMEOFFSET|do|  
  
 El archivo XSD con formato XML tendrá las siguientes adiciones:  
  
```  
<xs:complexType name="SQLDATETIME2">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATETIMEOFFSET">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATE">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLTIME">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
```  
  
## <a name="character-data-files"></a>Archivos de datos de caracteres  
 En los archivos de datos de caracteres, los valores de fecha y hora se representan como se describe en la sección "Formatos de datos: cadenas y literales" de [compatibilidad con tipos de datos para OLE DB mejoras de fecha y hora](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md) para OLE DB.  
  
 En archivos de datos nativos, los valores de fecha y hora para los cuatro nuevos tipos se representan como sus representaciones TDS con una escala de 7 (porque este es el máximo admitido por [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y los archivos de datos bcp no almacenan la escala de estas columnas). No se ha realizado ningún cambio en el almacenamiento de los tipos **datetime** y **smalldatetime** existentes, ni en sus representaciones de flujo TDS.  
  
 Los tamaños de almacenamiento para los distintos tipos de almacenamiento son los siguientes para OLE DB:  
  
|tipo de almacenamiento en archivo|Tamaño de almacenamiento en bytes|  
|-----------------------|---------------------------|  
|DATETIME|8|  
|smalldatetime|4|  
|Date|3|  
|time|6|  
|datetime2|9|  
|datetimeoffset|11|  
 
  
## <a name="bcp-types-in-msoledbsqlh"></a>Tipos BCP en msoledbsql.h  
 Los tipos siguientes se definen en msoledbsql.h. Estos tipos se pasan con el *eUserDataType* parámetro de ibcpsession:: BCPColFmt en OLE DB.  
  
|tipo de almacenamiento en archivo|Tipo de datos del archivo host|Escriba en msoledbsql.h para su uso con ibcpsession:: BCPColFmt|Valor|  
|-----------------------|-------------------------|-----------------------------------------------------------|-----------|  
|DATETIME|SQLDATETIME|BCP_TYPE_SQLDATETIME|0x3d|  
|Smalldatetime|SQLDATETIM4|BCP_TYPE_SQLDATETIM4|0x3a|  
|date|SQLDATE|BCP_TYPE_SQLDATE|0x28|  
|Time|SQLTIME|BCP_TYPE_SQLTIME|0x29|  
|Datetime2|SQLDATETIME2|BCP_TYPE_SQLDATETIME2|0x2a|  
|Datetimeoffset|SQLDATETIMEOFFSET|BCP_TYPE_SQLDATETIMEOFFSET|0x2b|  
  
## <a name="bcp-data-type-conversions"></a>Conversiones de tipos de datos BCP  
 En las tablas siguientes se proporciona información de conversión.  
  
 **Nota de OLE DB** Las conversiones siguientes se realizan con IBCPSession. IRowsetFastLoad usa conversiones OLE DB, tal como se define en [conversiones realizadas de cliente a servidor](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md). Tenga en cuenta que los valores datetime se redondean a la fracción 1/300 de segundo y los valores smalldatetime tienen los segundos establecidos en cero después de que se hayan realizado las conversiones de cliente que se describen a continuación. El redondeo de datetime se propaga a las horas y minutos, pero no a la fecha.  
  
|A --><br /><br /> De|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|char|wchar|  
|------------------------|----------|----------|-------------------|--------------|---------------|--------------------|----------|-----------|  
|date|1|-|1, 6|1, 6|1, 6|1, 5, 6|1, 3|1, 3|  
|Time|N/D|1, 10|1, 7, 10|1, 7, 10|1, 7, 10|1, 5, 7, 10|1, 3|1, 3|  
|Smalldatetime|1, 2|1, 4, 10|1|1|1, 10|1, 5, 10|1, 11|1, 11|  
|DATETIME|1, 2|1, 4, 10|1, 12|1|1, 10|1, 5, 10|1, 11|1, 11|  
|Datetime2|1, 2|1, 4, 10|1, 12|1, 10|1, 10|1, 5, 10|1, 3|1, 3|  
|Datetimeoffset|1, 2, 8|1, 4, 8, 10|1, 8, 10|1, 8, 10|1, 8, 10|1, 10|1, 3|1, 3|  
|Char/wchar (date)|9|-|9, 6, 12|9, 6, 12|9, 6|9, 5, 6|N/D|N/D|  
|Char/wchar (time)|-|9, 10|9, 7, 10, 12|9, 7, 10, 12|9, 7, 10|9, 5, 7, 10|N/D|N/D|  
|Char/wchar (datetime)|9, 2|9, 4, 10|9, 10, 12|9, 10, 12|9, 10|9, 5, 10|N/D|N/D|  
|Char/wchar (datetimeoffset)|9, 2, 8|9, 4, 8, 10|9, 8, 10, 12|9, 8, 10, 12|9, 8, 10|9, 10|N/D|N/D|  
  
#### <a name="key-to-symbols"></a>Clave de los símbolos  
  
|Símbolo|Significado|  
|------------|-------------|  
|-|No se admite la conversión.<br />|  
|1|Si los datos proporcionados no son válidos, se registra un error. Para los valores datetimeoffset, el espacio de tiempo debe estar comprendido dentro del intervalo después de la conversión a UTC, aunque no se haya solicitado ninguna conversión a UTC. Esto se debe a que la secuencia de datos tabulares (TDS) y el servidor siempre normalizan el tiempo en valores datetimeoffset para UTC. Por lo tanto, el cliente debe comprobar que los componentes de tiempo se encuentran dentro del intervalo admitido después de la conversión a UTC.|  
|2|Se omite el componente de hora.|  
|3|Si se produce un truncamiento con pérdida de datos, se publica un error. Para datetime2, el número de dígitos de las fracciones de segundo (la escala) se determina en función del tamaño de la columna de destino, según la tabla siguiente. Si el tamaño de las columnas es mayor que el intervalo de la tabla, se presupone una escala de 9. Esta conversión debería permitir hasta nueve dígitos en las fracciones de segundo, que es el máximo permitido por OLE DB.<br /><br /> **Tipo:** DBTIME2<br /><br /> **Escala supuesta 0** 8<br /><br /> **Escala supuesta 1..9** 1..9<br /><br /> <br /><br /> **Tipo:** DBTIMESTAMP<br /><br /> **Escala supuesta 0:** 19<br /><br /> **Escala supuesta 1..9:** 21..29<br /><br /> <br /><br /> **Tipo:** DBTIMESTAMPOFFSET<br /><br /> **Escala supuesta 0:** 26<br /><br /> **Escala supuesta 1..9:** 28..36|  
|4|Se omite el componente de fecha.|  
|5|Timezone se establece en UTC (por ejemplo, 00:00).|  
|6|La hora se establece en cero.|  
|7|La fecha se establece en 1900-01-01.|  
|8|Se omite el desplazamiento de zona horaria.|  
|9|La cadena se analiza y se convierte en un valor date, datetime, datetimeoffset o time, en función del primer carácter de puntuación encontrado y de la presencia de otros componentes. Después, la cadena se convierte en el tipo de destino, siguiendo las reglas de la tabla al final de este artículo para el tipo de origen detectado por este proceso. Si los datos proporcionados no pueden analizarse sin errores, o si cualquier parte del componente está fuera del intervalo permitido, o si no hay ninguna conversión del tipo literal al tipo de destino, se registra un error. Para los parámetros datetime y smalldatetime, si el año está fuera del intervalo que se admiten estos tipos, se registra un error.<br /><br /> Para datetimeoffset, el valor debe estar comprendido dentro del intervalo después de la conversión a UTC, aunque no se haya solicitado ninguna conversión a UTC. Esto se debe a que la secuencia de datos tabulares (TDS) y el servidor siempre normalizan la hora en valores datetimeoffset para UTC, de modo que el cliente tenga que comprobar que los componentes de hora están dentro del intervalo admitido después de la conversión a UTC. Si el valor no está dentro del intervalo UTC admitido, se registra un error.|  
|10|Para el cliente para las conversiones de servidor, si se produce un truncamiento con pérdida de datos se registra un error. Este error también se produce si el valor está fuera del intervalo que puede representarse mediante el intervalo UTC utilizado por el servidor. Si se produce un truncamiento de segundos o fracciones de segundo en una conversión de servidor a cliente, solo se emite una advertencia.|  
|11|Para el cliente para las conversiones de servidor, si se produce un truncamiento con pérdida de datos se registra un error.|
|12|Los segundos se establecen en cero y las fracciones de segundo se descartan. No es posible ningún error de truncamiento.|  
|N/D|Se mantiene el comportamiento de las versiones actuales y anteriores de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].|  
  
## <a name="see-also"></a>Consulte también     
 [Mejoras de fecha y hora &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
