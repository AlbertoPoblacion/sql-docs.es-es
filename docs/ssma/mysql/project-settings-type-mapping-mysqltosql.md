---
title: Configuración del proyecto (asignación de tipo) (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: beb82f2fd894af71bb6f291dcc6f86a995f8dd85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138327"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Configuración del proyecto (asignación de tipo) (MySQLToSQL)
La configuración del proyecto de asignación de tipos le permite establecer asignaciones de tipos predeterminadas para el proyecto SSMA.  

Asignación de tipos está disponible en los cuadros de diálogo Configuración del proyecto y la configuración predeterminada del proyecto:  
  
-   Utilice el cuadro de diálogo de configuración del proyecto para establecer las opciones de configuración para el proyecto actual. Para obtener acceso a la configuración de asignación de tipo, en el menú Herramientas, seleccione la configuración del proyecto y, a continuación, haga clic en asignación de tipos en el panel izquierdo.  
  
-   Utilice el cuadro de diálogo Configuración de proyecto predeterminada para establecer las opciones de configuración para todos los proyectos. Para tener acceso a la asignación de tipo configuración, en el menú Herramientas, seleccione la configuración predeterminada del proyecto, tipo de proyecto de migración select para los que es necesaria para ver o cambiar de configuración **versión de destino de migración** lista desplegable y, a continuación, haga clic en el tipo Asignación en el panel izquierdo.  
  
## <a name="options"></a>Opciones  
  
##### <a name="source-type"></a>Tipo de origen  
Es el tipo de datos MySQL, que debe asignarse al tipo de datos de la base de datos de destino.  
  
##### <a name="target-type"></a>Tipo de destino  
Escriba los datos de la base de datos de destino para el tipo de datos de MySQL especificado.  
  
##### <a name="add"></a>Agregar  
Haga clic para agregar un tipo de datos a la lista de asignación.  
  
##### <a name="edit"></a>Editar  
Haga clic para editar el tipo de datos seleccionado en la lista de asignación.  
  
##### <a name="remove"></a>Quitar  
Haga clic para quitar la asignación de tipos de datos seleccionados de la lista de asignación.  
  
##### <a name="reset-to-default"></a>Valores predeterminados  
Haga clic para restablecer la lista de asignación de tipo para los valores predeterminados SSMA.  
  
## <a name="type-mappings"></a>Asignaciones de tipos  
La siguiente tabla muestra las asignaciones predeterminadas entre tipos de datos de origen y destino  
  
|||  
|-|-|  
|**Tipo de datos de MySQL**|**Tipo de datos SQL Server**|  
|bigint|bigint|  
|bigint [*.. 255]|bigint|  
|binary|binario [1]|  
|archivo binario [de 0.. 1]|binario [1]|  
|binario [2..255]|binario [*]|  
|bit|binario [1]|  
|bit[0..8]|binario [1]|  
|bit[17..24]|binario [3]|  
|bit[25..32]|binario [4]|  
|bit[33..40]|binario [5]|  
|bit[41..48]|binario [6]|  
|bit[49..56]|binario [7]|  
|bit[57..64]|binario [8]|  
|bit[9..16]|binario [2]|  
|blob|varbinary(max)|  
|BLOB [de 0.. 1]|varbinary [1]|  
|blob[2..8000]|varbinary [*]|  
|blob[8001..*]|varbinary(max)|  
|booleano|bit|  
|booleano|bit|  
|char|nchar [1]|  
|bytes de char|binario [1]|  
|bytes del carácter [de 0.. 1]|binario [1]|  
|bytes de Char [2..255]|binario [*]|  
|char [de 0.. 1]|nchar [1]|  
|Char [2..255]|nchar [*]|  
|character|nchar [1]|  
|caracteres distintos de [0.. 1]|nvarchar [1]|  
|carácter variable [2..255]|nvarchar|  
|carácter [de 0.. 1]|nchar [1]|  
|caracteres [2..255]|nchar [*]|  
|date|date|  
|datetime|datetime2 [0]|  
|dec|decimal|  
|DEC [*.. 65]|decimal[*][0]|  
|DEC [*.. 65] [\*... 30]|decimal [*] [\*]|  
|decimal|decimal|  
|decimal [*.. 65]|decimal[*][0]|  
|decimal [*.. 65] [\*... 30]|decimal [*] [\*]|  
|Doble|float[53]|  
|double precision|float[53]|  
|doble precisión [*.. 255] [\*... 30]|numérico [*] [\*]|  
|Double [*.. 255] [\*... 30]|numérico [*] [\*]|  
|se ha corregido|numeric|  
|se ha corregido [*.. 65] [\*... 30]|numérico [*] [\*]|  
|float|float[24]|  
|float [*.. 255] [\*... 30]|numérico [*] [\*]|  
|float [*.. 53]|float[53]|  
|int|int|  
|int [*.. 255]|int|  
|integer|int|  
|entero [*.. 255]|int|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|int|  
|mediumint [*.. 255]|int|  
|mediumtext|nvarchar(max)|  
|carácter nacional|nchar [1]|  
|carácter nacional [de 0.. 1]|nchar [1]|  
|carácter nacional [2..255]|nchar [*]|  
|carácter nacional|nchar [1]|  
|national character varying de|nvarchar [1]|  
|carácter nacional distintos [de 0.. 1]|nvarchar [1]|  
|carácter nacional varying [2..4000]|nvarchar [*]|  
|national character varying de [4001.. *]|nvarchar(max)|  
|carácter nacional [de 0.. 1]|nchar [1]|  
|carácter nacional [2..255]|nchar [*]|  
|varchar nacional|nvarchar [1]|  
|varchar nacional [de 0.. 1]|nvarchar [1]|  
|National varchar [2..4000]|nvarchar [*]|  
|National varchar [4001.. *]|nvarchar(max)|  
|nchar|nchar [1]|  
|nchar varchar|nvarchar [1]|  
|nchar varchar [de 0.. 1]|nvarchar [1]|  
|nchar varchar [2..4000]|nvarchar [*]|  
|nchar varchar [4001.. *]|nvarchar(max)|  
|nchar [de 0.. 1]|nchar [1]|  
|nchar [2..255]|nchar [*]|  
|numeric|numeric|  
|numérico [*.. 65]|numérico [*] [0]|  
|numérico [*.. 65] [\*... 30]|numérico [*] [\*]|  
|nvarchar|nvarchar [1]|  
|nvarchar [de 0.. 1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|real|float[53]|  
|real [*.. 255] [\*... 30]|numérico [*] [\*]|  
|serial|bigint|  
|smallint|smallint|  
|smallint [*.. 255]|smallint|  
|text|nvarchar(max)|  
|text[0..1]|nvarchar [1]|  
|texto [2..4000]|nvarchar [*]|  
|text[4001..*]|nvarchar(max)|  
|time|time|  
|timestamp|datetime|  
|tinyblob|varbinary [255]|  
|tinyint|smallint|  
|tinyint [*.. 255]|smallint|  
|tinytext|nvarchar [255]|  
|bigint sin signo|bigint|  
|bigint sin signo [*.. 255]|bigint|  
|dec sin signo|decimal|  
|dec sin signo [*.. 65]|decimal[*][0]|  
|dec sin signo [*.. 65] [\*... 30]|decimal [*] [\*]|  
|decimal sin signo|decimal|  
|decimal sin signo [*.. 65]|decimal[*][0]|  
|decimal sin signo [*.. 65] [\*... 30]|decimal [*] [\*]|  
|doble sin signo|float[53]|  
|sin signo de precisión doble|float[53]|  
|sin signo de precisión doble [*.. 255] [\*... 30]|numérico [*] [\*]|  
|unsigned double [*.. 255] [\*... 30]|numérico [*] [\*]|  
|unsigned fijo|numeric|  
|unsigned fijo [*.. 65] [\*... 30]|numérico [*] [\*]|  
|float sin signo|float[24]|  
|float sin signo [*.. 255] [\*... 30]|numérico [*] [\*]|  
|float sin signo [*.. 53]|float[53]|  
|unsigned int|bigint|  
|int sin signo [*.. 255]|bigint|  
|entero sin signo|bigint|  
|entero sin signo [*.. 255]|bigint|  
|mediumint sin signo|int|  
|mediumint sin signo [*.. 255]|int|  
|numérico sin signo|numeric|  
|numérico sin signo [*.. 65]|numérico [*] [0]|  
|numérico sin signo [*.. 65] [\*... 30]|numérico [*] [\*]|  
|real sin signo|float[53]|  
|unsigned real [*.. 255 [[\*... 30]|numérico [*] [\*]|  
|smallint sin signo|int|  
|smallint sin signo [*.. 255]|int|  
|tinyint sin signo|tinyint|  
|tinyint sin signo [*.. 255]|tinyint|  
|varbinary [de 0.. 1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [de 0.. 1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar[4001..*]|nvarchar(max)|  
|year|smallint|  
|año [2..2]|smallint|  
|año [4..4]|smallint|  
  
##### <a name="add"></a>Agregar  
Haga clic para agregar un tipo de datos a la lista de asignación.  
  
##### <a name="edit"></a>Editar  
Haga clic para editar un tipo de datos en la lista de asignación.  
  
##### <a name="remove"></a>Quitar  
Haga clic para quitar la asignación de tipos de datos seleccionados de la lista de asignación.  
  
##### <a name="reset-to-default"></a>Valores predeterminados  
Haga clic para restablecer todas las asignaciones de tipo de datos a los valores predeterminados SSMA.  
  
