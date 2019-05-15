---
title: Instalar la búsqueda de texto completo SQL Server en Linux | Microsoft Docs
description: En este artículo se describe cómo instalar la búsqueda de texto completo de SQL Server en Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.openlocfilehash: d16a399ceb6a2c22599d7a95396d49f21e378eef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809743"
---
# <a name="install-sql-server-full-text-search-on-linux"></a>Instalar la búsqueda de texto completo SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Los pasos siguientes instalan [SQL Server Full-Text Search](../relational-databases/search/full-text-search.md) (**mssql-server-fts**) en Linux. Búsqueda de texto completo permite ejecutar consultas de texto completo en datos basados en caracteres en tablas de SQL Server. Para problemas conocidos de esta versión, consulte el [notas de la versión](sql-server-linux-release-notes.md).

> [!NOTE]
> Antes de instalar la búsqueda de texto completo de SQL Server, en primer lugar [instalar SQL Server](sql-server-linux-setup.md#platforms). Esto configura las claves y los repositorios que se utiliza para instalar el **mssql-server-fts** paquete.

Instalar la búsqueda de texto completo de SQL Server para su plataforma:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Instalar en RHEL</a>

Use los siguientes comandos para instalar el **mssql-server-fts** en Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-fts
```

Si ya tiene **mssql-server-fts** instalado, puede actualizar a la versión más reciente con los siguientes comandos:

```bash
sudo yum check-update
sudo yum update mssql-server-fts
```

Si necesita una instalación sin conexión, busque la descarga del paquete de búsqueda de texto completo en el [notas de la versión](sql-server-linux-release-notes.md). A continuación, use los mismos pasos de instalación sin conexión se describe en el artículo [instalar SQL Server](sql-server-linux-setup.md#offline).

## <a name="ubuntu">Instalar en Ubuntu</a>

Use los siguientes comandos para instalar el **mssql-server-fts** en Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts
```

Si ya tiene **mssql-server-fts** instalado, puede actualizar a la versión más reciente con los siguientes comandos:

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts 
```

Si necesita una instalación sin conexión, busque la descarga del paquete de búsqueda de texto completo en el [notas de la versión](sql-server-linux-release-notes.md). A continuación, use los mismos pasos de instalación sin conexión se describe en el artículo [instalar SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Instalar en SLES</a>

Use los siguientes comandos para instalar el **mssql-server-fts** en SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-fts
```

Si ya tiene **mssql-server-fts** instalado, puede actualizar a la versión más reciente con los siguientes comandos:

```bash
sudo zypper refresh
sudo zypper update mssql-server-fts
```

Si necesita una instalación sin conexión, busque la descarga del paquete de búsqueda de texto completo en el [notas de la versión](sql-server-linux-release-notes.md). A continuación, use los mismos pasos de instalación sin conexión se describe en el artículo [instalar SQL Server](sql-server-linux-setup.md#offline).

## <a name="supported-languages"></a>Idiomas compatibles

Búsqueda de texto completo usa [separadores de palabras](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) que determinan cómo se identifican las palabras individuales en función de lenguaje. Puede obtener una lista de separadores de palabras registrados consultando la **sys.fulltext_languages** vista de catálogo. Separadores de palabras para los idiomas siguientes se instalan con SQL Server:

| Idioma | Id. de idioma |
|---|---|
| Neutro | 0 |
| Árabe | 1025 |
| Bengali (India) | 1093 |
| Bokmal | 1044 |
| Portugués (Brasil) | 1046 |
| British English | 2057 |
| Búlgaro | 1026 |
| Catalán | 1027 |
| Chino (RAE de Hong Kong, RPC) | 3076 |
| Chino (RAE de Macao) | 5124 |
| Chino (Singapur) | 4100 |
| Croata | 1050 |
| Checo | 1029 |
| Danish | 1030 |
| Neerlandés | 1043 |
| Inglés | 3082 |
| Francés | 1036 |
| German | 1031 |
| Greek | 1032 |
| Gujarati | 1095 |
| Hebreo | 1037 |
| Hindi | 1081 |
| Islandés | 1039 |
| Indonesio | 1057 |
| Italiano | 1040 |
| Japonés | 1041 |
| Canarés | 1099 |
| Coreano | 1042 |
| Letón | 1062 |
| Lituano | 1063 |
| Malay - Malaysia | 1086 |
| Malayalam | 1100 |
| Maratí | 1102 |
| Polaco | 1045 |
| Portugués | 2070 |
| Punjabí | 1094 |
| Rumano | 1048 |
| Ruso | 1049 |
| Serbio (cirílico) | 3098 |
| Serbio (latino) | 2074 |
| Chino simplificado | 2052 |
| Eslovaco | 1051 |
| Esloveno | 1060 |
| Español | 3082 |
| Sueco | 1053 |
| Tamil | 1097 |
| Telugu | 1098 |
| Tailandés | 1054 |
| Chino tradicional | 1028 |
| Turco | 1055 |
| Ucraniano | 1058 |
| Urdu | 1056 |
| Vietnamita | 1066 |

## <a id="filters"></a> Filtros

Búsqueda de texto completo también funciona con texto almacenado en archivos binarios. Pero en este caso, se requiere un filtro instalado para procesar el archivo. Para obtener más información acerca de los filtros, consulte [configurar y administrar filtros para búsquedas](../relational-databases/search/configure-and-manage-filters-for-search.md).

Puede ver una lista de filtros instalados mediante una llamada a **sp_help_fulltext_system_components 'filter'**. Para SQL Server, se instalan los siguientes filtros:

| Nombre de componente | Id. de clase | Versión |
|---|---|---|
|.a | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ANS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ASC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ascx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asm | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ASP | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.aspx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asx | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|BAS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bat | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.bcp | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.c | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|*.CC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CLS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cmd | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CSA | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CSS | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.csv | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.DBS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.def | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dic | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dos | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.DSP | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.dsw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ext | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|p+f | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.fky | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.h | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hhc | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|HTA | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.HTML | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htt | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htw | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hXX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|i. | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ibq | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ICS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.idl | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.idq | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|Inc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|INI | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.INX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.jav | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|Java | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.js | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.KCI | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.lgn | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.log | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.lst | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|. m3u | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.MAK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.MK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.odc | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.odh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.odl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgdef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgundef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pl | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.PRC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|. RC2 | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.reg | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rgs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rtf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|reglas .rul entre | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.s | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|archivos | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.shtm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.shtml | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|Snippet | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.sol | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.sor | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.srf | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.stm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.TAB | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tdl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tlh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|TLI | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.TRG | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.txt | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|UDF | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.UDT | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|URL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|usr | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vbs | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.viw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|vsixlangpack | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixmanifest | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SCC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vssscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wri | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.WTX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.xml | 41B9BE05-B3AF-460C-BF0B-2CDD44A093B1 | 12.0.9735.0 |

## <a name="semantic-search"></a>Búsqueda semántica
[La búsqueda semántica](../relational-databases/search/semantic-search-sql-server.md) se basa en la característica de búsqueda de texto completo para extraer e indexar relevantes estadísticamente *frases clave*. Esto le permite consultar el significado dentro de documentos en la base de datos. También ayuda a identificar los documentos que son similares.

Para poder usar la búsqueda semántica, primero debe restaurar la base de datos de estadísticas semánticas de lenguaje en el equipo.

1. Usar una herramienta, como [sqlcmd](sql-server-linux-setup-tools.md), para ejecutar el siguiente comando de Transact-SQL en la instancia de Linux con SQL Server. Este comando restaura la base de datos de estadísticas de lenguaje.

   ```sql
   RESTORE DATABASE [semanticsdb] FROM
   DISK = N'/opt/mssql/misc/semanticsdb.bak' WITH FILE = 1,
   MOVE N'semanticsdb' TO N'/var/opt/mssql/data/semanticsDB.mdf',
   MOVE N'semanticsdb_log' TO N'/var/opt/mssql/data/semanticsdb_log.ldf', NOUNLOAD, STATS = 5
   GO
   ```

   > [!NOTE]
   > Si es necesario, actualice las rutas de acceso en el comando de restauración anterior para ajustar la configuración.

1. Ejecute el siguiente comando de Transact-SQL para registrar la base de datos de estadísticas semánticas de lenguaje.

    ```sql
    EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
    GO
    ```

## <a name="next-steps"></a>Pasos siguientes

Para obtener información acerca de la búsqueda de texto completo, vea [búsqueda de texto completo de SQL Server](../relational-databases/search/full-text-search.md). 
