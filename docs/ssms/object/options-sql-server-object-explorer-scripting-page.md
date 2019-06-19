---
title: Opciones (Explorador de objetos de SQL Server - página Script) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bd09972eaebba893ac92198c9b953392e383f9e4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095725"
---
# <a name="options-sql-server-object-explorer---scripting-page"></a>Opciones (Explorador de objetos de SQL Server - página Script)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Use esta página para establecer las opciones de scripting que se aplican a los siguientes comandos en los menús contextuales de objetos del **Explorador de objetos**:  
  
-   Comandos **Editar** para las tablas y vistas del usuario.  
  
-   Comandos **Script <object> como** para los objetos creados por el usuario.  
  
-   Comando **Modificar** para los objetos creados por el usuario.  
  
-   Esta página también establece los valores predeterminados de las opciones de scripting del **Asistente para generar scripts de SQL Server**.  
  
## <a name="remarks"></a>Notas  
Los comandos **Editar** y **Modificar** pueden generar resultados distintos a los del comando **Script <object> como** para el mismo valor de opción. Los comandos **Editar** y **Modificar** están diseñados para modificar objetos en la base de datos actual durante una sesión del Editor de consultas. El comando **Script<object> como** está diseñado para generar un script que se pueda usar posteriormente para crear objetos.  
  
## <a name="options"></a>Opciones  
Para especificar las opciones de scripts, seleccione las opciones de configuración disponibles en la lista situada a la derecha de cada opción.  
  
### <a name="general-scripting-options"></a>Opciones generales de scripting  
**Delimitar instrucciones individuales**  
Separa instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] individuales mediante un separador de lotes. Para cambiar el separador de lotes predeterminado del **Editor de consultas**, seleccione **Herramientas**/**Opciones**/**Ejecución de la consulta**/**SQL Server**/**General**/**Separador de lotes**. El valor predeterminado es False. Para más información, consulte [GO (Transact-SQL)](https://msdn.microsoft.com/b2ca6791-3a07-4209-ba8e-2248a92dd738).  
  
**Incluir encabezados descriptivos**  
Agrega comentarios descriptivos al script dividiéndolo en secciones para cada objeto. El valor predeterminado es True. Para más información, consulte [/ *...* / (Comment) (Transact-SQL)](https://msdn.microsoft.com/4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c).  
  
**Incluir la habilitación de la compresión vardecimal**  
Incluye las opciones de almacenamiento vardecimal. El valor predeterminado es False. Para obtener más información, consulte [sp_db_vardecimal_storage_format (Transact-SQL)](https://msdn.microsoft.com/9920b2f7-b802-4003-913c-978c17ae4542).  
  
**Crear scripts para el historial de cambios**  
Incluye información del historial de cambios en el script.  
  
**Generar script de catálogos de texto completo**  
Incluye un script para catálogos de texto completo. El valor predeterminado es False. Para más información, consulte [CREATE FULLTEXT CATALOG (Transact-SQL)](https://msdn.microsoft.com/d7a8bd93-e2d7-4a40-82ef-39069e65523b).  
  
**Incluir USE <database>**  
Agrega la instrucción USE DATABASE al script para crear objetos de base de datos en el contexto de la base de datos actual del **Explorador de objetos** . Cuando necesite usar el script en otra base de datos, seleccione False para omitir. El valor predeterminado es True. Para más información, consulte [USE (Transact-SQL)](https://msdn.microsoft.com/c05acac8-c063-4770-8e36-d7f71d500b10).  
  
### <a name="object-scripting-options"></a>Opciones de scripting de objetos  

**Comprobar la existencia de objetos** Compruebe que existe un objeto con el nombre indicado antes de quitarlo o modificarlo, o bien que no existe un objeto con el nombre indicado antes de crearlo. Para más información, consulte [IF...ELSE (Transact-SQL)](https://msdn.microsoft.com/676c881f-dee1-417a-bc51-55da62398e81) y [EXISTS (Transact-SQL)](https://msdn.microsoft.com/b6510a65-ac38-4296-a3d5-640db0c27631).

**Generar script para objetos dependientes**  
Genera un script para objetos adicionales que son necesarios cuando se ejecuta el script para el objeto seleccionado. El valor predeterminado es False.  
  
**Nombres de objeto de certificación de esquema**  
Califica nombres de objeto con el esquema de objetos. El valor predeterminado es False. Para más información, consulte [Crear un esquema de base de datos](../../relational-databases/security/authentication-access/create-a-database-schema.md).  

**Incluir opciones de compresión de datos en el script** Incluye las opciones de compresión de datos en el script. El valor predeterminado es False.

**Generar script de propiedades extendidas**  
Incluye propiedades extendidas en el script si el objeto tiene propiedades extendidas. El valor predeterminado es False. Para más información, consulte [sp_addextendedproperty (Transact-SQL)](https://msdn.microsoft.com/565483ea-875b-4133-b327-d0006d2d7b4c).  
  
**Incluir propietario**  
Incluye el propietario en el script generado. El valor predeterminado es False.  
  
**Generar script de permisos**  
Incluye permisos sobre los objetos de la base de datos en el script. El valor predeterminado es True. Para más información, consulte [Permisos](../../relational-databases/security/permissions-database-engine.md).  
  
### <a name="tableview-options"></a>Opciones de tabla o vista  
Las siguientes opciones solo se aplican a scripts para tablas o vistas.  
  
**Convertir tipos de datos definidos por el usuario en tipos base**  
Convierte los tipos de datos definidos por el usuario en los tipos base a partir de los cuales se crearon. Utilice el valor True cuando los tipos de datos definidos por el usuario de la base de datos de origen no existan en la base de datos en la que se va a ejecutar el script. Utilice el valor False para mantener los tipos de datos definidos por el usuario. El valor predeterminado es False. Para más información, consulte [CREATE TYPE (Transact-SQL)](https://msdn.microsoft.com/2202236b-e09f-40a1-bbc7-b8cff7488905).  
  
**Generar comandos SET ANSI PADDING**  
Agrega la instrucción SET ANSI_PADDING antes y después de cada instrucción CREATE TABLE. El valor predeterminado es True. Para más información, consulte [SET ANSI_PADDING (Transact-SQL)](https://msdn.microsoft.com/92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0).  
  
**Incluir intercalación**  
Incluye una intercalación en la definición de columna. El valor predeterminado es True. Para más información, consulte [Compatibilidad con la intercalación y Unicode](../../relational-databases/collations/collation-and-unicode-support.md).  
  
**Incluir propiedad IDENTITY**  
Incluye definiciones para el valor de inicialización IDENTITY y el incremento IDENTITY. El valor predeterminado es True. Para más información, consulte [IDENTITY (propiedad) (Transact-SQL)](https://msdn.microsoft.com/8429134f-c821-4033-a07c-f782a48d501c).  
  
**Referencias de claves externas de certificación de esquema**  
Agrega el nombre de esquema a las referencias de tabla para las restricciones FOREIGN KEY. El valor predeterminado es True.  
  
**Generar script de reglas y valores predeterminados enlazados**  
Incluye las llamadas a los procedimientos almacenados enlazados **sp_bindefault** y **sp_bindrule** . El valor predeterminado es True. Para más información, consulte [sp_bindefault (Transact-SQL)](https://msdn.microsoft.com/3da70c10-68d0-4c16-94a5-9e84c4a520f6) y [sp_bindrule (Transact-SQL)](https://msdn.microsoft.com/2606073e-c52f-498d-a923-5026b9d97e67).  
  
**Generar script de restricciones CHECK**  
Agrega [restricciones CHECK](../../relational-databases/tables/unique-constraints-and-check-constraints.md) al script. El valor predeterminado es True.  
  
**Incluir valores predeterminados**  
Incluye valores predeterminados de columna en el script. El valor predeterminado es False. Para más información, consulte [CREATE DEFAULT (Transact-SQL)](https://msdn.microsoft.com/08475db4-7d90-486a-814c-01a99d783d41).  
  
**Generar script de grupos de archivos**  
Especifica el grupo de archivos en la cláusula ON para definiciones de tabla. El valor predeterminado es False. Para más información, consulte [CREATE TABLE (Transact-SQL)](https://msdn.microsoft.com/1e068443-b9ea-486a-804f-ce7b6e048e8b).  
  
**Incluir claves externas en el script**  
Incluye [restricciones FOREIGN KEY](../../relational-databases/tables/primary-and-foreign-key-constraints.md) en el script. El valor predeterminado es False.  
  
**Incluir índices de texto completo**  
Incluye índices de texto completo en el script. El valor predeterminado es False. Para más información, consulte [CREATE FULLTEXT INDEX (Transact-SQL)](https://msdn.microsoft.com/8b80390f-5f8b-4e66-9bcc-cabd653c19fd).  
  
**Incluir índices en el script**  
Incluye índices clúster, no clúster y XML en el script. El valor predeterminado es True. Para más información, consulte [CREATE INDEX (Transact-SQL)](https://msdn.microsoft.com/d2297805-412b-47b5-aeeb-53388349a5b9).  
  
**Generar script de esquemas de partición**  
Incluye esquemas de particiones de tabla en el script. El valor predeterminado es False. Para más información, consulte [CREATE PARTITION SCHEME (Transact-SQL)](https://msdn.microsoft.com/5b21c53a-b4f4-4988-89a2-801f512126e4).  
  
**Incluir claves principales en el script**  
Incluye [Restricciones entre claves principales y claves externas](../../relational-databases/tables/primary-and-foreign-key-constraints.md) en el script. El valor predeterminado es True.  
  
**Incluir estadísticas en el script**  
Incluye estadísticas definidas por el usuario en el script. El valor predeterminado es False. Para más información, consulte [CREATE STATISTICS (Transact-SQL)](https://msdn.microsoft.com/b23e2f6b-076c-4e6d-9281-764bdb616ad2).  
  
**Incluir desencadenadores**  
Incluye desencadenadores en el script. El valor predeterminado es False. Para más información, consulte [CREATE TRIGGER (Transact-SQL)](https://msdn.microsoft.com/edeced03-decd-44c3-8c74-2c02f801d3e7).  
  
**Incluir claves únicas en el script**  
Incluye [Restricciones UNIQUE y restricciones CHECK](../../relational-databases/tables/unique-constraints-and-check-constraints.md) en el script. El valor predeterminado es False.  
  
**Generar script de columnas de vista**  
Declara columnas de vista en encabezados de vista. El valor predeterminado es False. Para más información, consulte [CREATE VIEW (Transact-SQL)](https://msdn.microsoft.com/aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9).  
  
**Incluir nombres de sistema de DRI**  
Incluye nombres de restricción generados por el sistema para aplicar la integridad referencial declarativa. El valor predeterminado es False. Para más información, consulte [REFERENTIAL_CONSTRAINTS (Transact-SQL)](https://msdn.microsoft.com/5d358f18-0a85-4b55-af4b-98d5f4cd1020).  
  
### <a name="version-options"></a>Opciones de versión

**Coincidir configuración del script con origen** Si está habilitada, la versión de destino, la edición del motor y el tipo de motor de los scripts generados se establecerán en los valores del servidor del objeto que se va a incluir en el script. Esta acción deshabilitará (y omitirá) las otras opciones de versión. 

**Script para la edición del motor de base de datos** Los scripts generados se dirigirán a la [Edición del motor](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.edition.aspx) especificada.

**Script para tipo de motor de base de datos** Los scripts generados se dirigirán al [Tipo de motor de base de datos](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.databaseenginetype.aspx) especificado.

**Script para versión de servidor**  
Los scripts generados se dirigirán a la versión especificada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Las características nuevas de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] no se pueden incluir en scripts para versiones anteriores. Algunos scripts creados para [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] no pueden ejecutarse en servidores que ejecutan una versión anterior de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o en una base de datos con un [valor de nivel de compatibilidad de base de datos](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)anterior.  

## <a name="see-also"></a>Vea también  
[Generar scripts (SQL Server Management Studio)](https://msdn.microsoft.com/9711c617-3c68-4e5a-aea3-befc64d51524)  
  
