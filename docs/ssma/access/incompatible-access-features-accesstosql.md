---
title: Características de Access incompatibles (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- Access databases, features incompatible with SQL Azure
- Access databases, features incompatible with SQL Server
- dates
- default expressions
- foreign keys
- hyperlink columns
- incompatible Access features
- indexes
- indexes, length of
- keywords
- primary keys
- reference, incompatible features
- replication columns
- special characters
- unique indexes
- validation rules
ms.assetid: 99d45b9c-e3b9-4d56-8c25-b594b887ace1
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 29b5225f95c6b2cb04f42c0e67c504ac2cb20e53
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62740910"
---
# <a name="incompatible-access-features-accesstosql"></a>Características de Access incompatibles (AccessToSQL)
No todas las características de base de datos de Access son compatibles con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Por ejemplo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y acceso tiene diferentes conjuntos de palabras clave reservadas. Problemas como éstos pueden provocar que una migración correcta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use la tabla siguiente para obtener información acerca de problemas de migración posibles y lo puede hacer con ellos.  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>Configuración de la base de datos o las características que podrían afectar a la migración  
  
|Obtener acceso a la opción de base de datos o característica|Problema de migración|  
|--------------------------------------|-------------------|  
|Acceso a tablas no tienen índices únicos.|Si una tabla que no tiene un índice único se migra a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], no se puede modificar la tabla después de la migración. Esto puede provocar problemas de compatibilidad de aplicaciones.<br /><br />Convertir objetos de base de datos de Access, la ventana de salida mostrará cualquier acceso a tablas que no tienen índices únicos.<br /><br />Puede configurar el acceso para agregar una clave principal en el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabla durante la conversión. Para obtener más información, consulte [configuración del proyecto (conversión)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388).|  
|Acceso a tablas tienen columnas de la replicación.|Si una tabla de Access que incluye las columnas del sistema de replicación se migra a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se interrumpirá la funcionalidad de replicación de Jet después de la migración.<br /><br />Tras la migración, considere el uso de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replicación para mantener copias sincronizadas de las bases de datos.|  
|Acceso a tablas que tienen índices únicos contienen varios valores null.|Acceso a tablas que tienen índices únicos con varios valores null no se puede transferir a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], porque en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], los índices únicos no permitir varios valores NULL. Se producirá un error de migración para estas tablas.<br /><br />SSMA marcará este problema en los informes de evaluación. Para crear un informe de evaluación, consulte [evaluar objetos de base de datos de acceso para la conversión](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Si se produce este problema, debe asegurarse de que la clave principal no tiene valores duplicados de null. O bien, debe quitar la clave principal o índices únicos que contienen varios valores null.|  
|Acceso a tablas contienen los valores de fecha que están fuera de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intervalo.|El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** tipo acepta fechas en el intervalo del 1 de enero de 1753 al 31 de diciembre de 9999 solo. Acceso acepta fechas en el intervalo de 100 1 de enero al 31 de diciembre de 9999.<br /><br />SSMA marcará este problema en los informes de evaluación. Para crear un informe de evaluación, consulte [evaluar objetos de base de datos de acceso para la conversión](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Puede configurar cómo SSMA resuelve las fechas que están fuera de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intervalo. Para obtener más información, consulte [configuración del proyecto (migración)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).|  
|Las longitudes de índice en acceso a superar los 900 bytes.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] los índices tienen un límite de 900 bytes para el tamaño total de columnas de clave de índice. Si las tablas de Access utilizan índices de mayor tamaño, SSMA mostrará una advertencia.<br /><br />Si continúa con la migración de datos, se puede producir un error en la migración.|  
|Los nombres de objeto de acceso son [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] palabras clave, o contienen caracteres especiales.|Acceso y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene diferentes conjuntos de palabras clave reservadas y caracteres especiales. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aceptará los objetos que se denominan utilizando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] palabras clave o que contienen caracteres especiales si utilizar identificadores entre paréntesis o entrecomillados, como "select" o [Active] .p. Para obtener más información, vea "Identificadores delimitados (motor de base de datos)" en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libros en pantalla.<br /><br />**NOTA:** Para usar comillas para delimitar identificadores, SET QUOTED_IDENTIFIER debe ser ON.<br /><br />Por ejemplo, `CREATE TABLE [schema](c1 [FOR])` es una instrucción válida, aunque **esquema** y **para** son palabras clave reservadas. Además, `CREATE TABLE [xxx*yyy](c1 x&y)` es una instrucción válida, aunque el nombre de tabla y columna contienen los caracteres especiales  **\&#42;** y **&amp;** .<br /><br />Todas las consultas que hacen referencia a esos objetos también deben usar los nombres con corchetes o comillas. Por ejemplo, la consulta `SELECT * FROM schema` se producirá un error. La consulta correcta es: `SELECT * FROM [schema]`.<br /><br />Convertir objetos de base de datos de Access, el panel de resultados mostrará cualquier acceso a tablas que usan las palabras clave o caracteres especiales. Puede modificar las tablas de Access y, a continuación, quitar y agregar de nuevo; la base de datos o bien, puede modificar las consultas que hacen referencia a esos objetos para que las consultas utilizan corchetes o comillas para delimitar identificadores. Si no modifica las consultas, las aplicaciones de Access podrían devolver errores o tiene otros problemas.|  
|Tamaño de los campos difieren en relaciones de clave principal/clave externa.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se admite la funcionalidad de Jet de vincular las columnas que tienen tipos de datos diferentes o tamaños con restricciones foreign key.<br /><br />Al convertir los objetos de base de datos de Access, la ventana de salida mostrará cualquier principales/claves restricciones de clave externa que no se convertirá en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede modificar los tipos de datos y los tamaños de las columnas de acceso para que puedan coinciden y, a continuación, quitarán y volver a agregar la base de datos de Access. O bien, puede migrar los datos aunque estas restricciones no se crearán en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Las tablas que se hace referencia en las relaciones de acceso tienen una clave principal ni un índice único.|Acceso acepta la relación entre las tablas donde la tabla que se hace referencia no tiene una clave principal o un índice único. Sin embargo, esto no es compatible con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Convertir objetos de base de datos de Access, la ventana de salida mostrará todas las tablas que no tienen relaciones pero ninguna clave principal o índice único. Puede modificar las tablas para agregar las claves principales o índices únicos y, a continuación, quitar y volver a agregar la base de datos de Access. O bien, puede migrar datos aunque la relación entre las tablas se interrumpirá.|  
|Acceso a tablas tienen columnas de hipervínculo.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no admite **hipervínculo** columnas. En su lugar, las columnas se tratan como acceso de las columnas memorando. De forma predeterminada, estas columnas se convertirá en **nvarchar (max)** columnas en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede personalizar la asignación. Para obtener más información, consulte [tipos de datos de destino y origen de asignación](mapping-source-and-target-data-types-accesstosql.md).|  
|Las expresiones de regla predeterminada o validación contienen funciones de acceso que no se puede convertir a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure.|Las expresiones de acceso predeterminada o las reglas de validación podrían incluir funciones de acceso del sistema o funciones definidas por el usuario que no se asignan a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure. Uso de funciones que no se asignan a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure, no podrá cargar las expresiones de valor predeterminado o las reglas de validación en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure.|  
  
## <a name="see-also"></a>Vea también  
[Preparar las bases de datos de acceso para la migración](preparing-access-databases-for-migration-accesstosql.md)  
[Migrar bases de datos de Access a SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
