---
title: Permisos GRANT T-SQL - almacenamiento de datos paralelos | Microsoft Docs
description: Permisos GRANT de Transact-SQL para las operaciones de base de datos en almacenamiento de datos paralelos.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 15798edc4d6a9b1f00c8dd489dfed76a39e5f340
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960945"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Permisos GRANT de Transact-SQL para el almacenamiento de datos paralelos
Permisos GRANT de Transact-SQL para las operaciones de base de datos en almacenamiento de datos paralelos.

## <a name="grant-permissions-to-submit-database-queries"></a>Conceder permisos para enviar consultas de base de datos
En esta sección se describe cómo conceder permisos a los roles de base de datos y los usuarios para consultar los datos en el dispositivo PDW de SQL Server.  
  
Las instrucciones que se usa para conceder permisos para consultar los datos dependen del ámbito de acceso deseado. Las siguientes instrucciones SQL crean un inicio de sesión denominado KimAbercrombie que puede acceder al dispositivo, cree un usuario de base de datos denominado KimAbercrombie en el **AdventureWorksPDW2012** de base de datos, crear un rol de base de datos denominado PDWQueryData, agrega el uso KimAbercrombie a la función de PDWQueryData y, a continuación, mostrar opciones de concesión de acceso de la consulta, según si se concede el acceso al objeto, o al nivel de base de datos.  
  
```sql  
USE master;  
GO  
  
CREATE LOGIN KimAbercrombie WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
USE AdventureWorksPDW2012;  
GO  
  
CREATE USER KimAbercrombie;  
GO  
  
CREATE ROLE PDWQueryData;  
GO  
  
EXEC sp_addrolemember 'PDWQueryData', 'KimAbercrombie'  
GO  
  
-- If the permission is granted against a table or view only, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO PDWQueryData;  
GO  
  
-- If the permission is granted for the database, use this syntax:  
GRANT SELECT ON DATABASE::AdventureWorksPDW2012 TO PDWQueryData;  
GO  
  
-- If KimAbercrombie is the only user that needs to access a table, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO KimAbercrombie;  
GO  
```  
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Conceder permisos para usar la consola de administración
En esta sección se describe cómo conceder permisos a inicios de sesión para usar la consola de administración.  
  
**Utilice la consola de administración**  
  
Para usar la consola de administración de un inicio de sesión requiere el nivel de servidor **VIEW SERVER STATE** permiso. La siguiente instrucción SQL se concede el **VIEW SERVER STATE** permiso al inicio de sesión `KimAbercrombie` para que Kim puede usar la consola de administración para supervisar el dispositivo PDW de SQL Server.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Terminar sesiones**  
  
Para conceder el permiso para eliminar las sesiones de un inicio de sesión, conceda el **ALTER ANY CONNECTION** permiso como sigue:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Conceder permisos para cargar datos
En esta sección se describe cómo conceder permisos a los usuarios de base de datos y funciones de base de datos para cargar datos en el PDWappliance de SQL Server.  
  
El siguiente script se muestra qué permisos son necesarios para cada opción de carga. Puede modificar esta opción para satisfacer sus necesidades específicas.  
  
```sql  
-- Create server login for the examples that follow.  
USE master;  
CREATE LOGIN BI_ETLUser WITH PASSWORD = '******';  
  
--Grant BULK Load permissions   
GRANT ADMINISTER BULK OPERATIONS TO BI_ETLUser;  
  
--Grant Staging database permissions  
USE stagedb;  
CREATE USER BI_ETLUser for login BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
EXEC sp_addrolemember 'db_ddladmin','BI_ETLUser';  
  
-- The CREATE TABLE permission is required for the database hosting the temporary table.  
-- This may be the staging database (if specified) or destination database.   
-- The CREATE permission is not required if loading in fastappend mode.  
GRANT CREATE TABLE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in append or fastappend mode, the INSERT permission is required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
  
-- If loading in reload mode, the INSERT and DELETE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT DELETE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in upsert mode, the INSERT and UPDATE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT UPDATE ON database::stagedb TO BI_ETLUser;  
  
-- Destination DB  
USE tpch_1gb;  
CREATE USER BI_ETLUser FOR LOGIN BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
```  
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Conceder permisos para copiar los datos fuera del dispositivo
En esta sección se describe cómo conceder permisos a un rol de usuario o la base de datos para copiar los datos fuera del dispositivo PDW de SQL Server.  
  
Para mover datos a otra ubicación requiere **seleccione** permiso en la tabla que contiene los datos que se va a mover.  
  
Si el destino de los datos es otra PDW de SQL Server, el usuario debe tener **CREATE TABLE** permiso en el destino y **ALTER SCHEMA** permiso en el esquema que contiene la tabla.  
  
## <a name="grant-permissions-to-manage-databases"></a>Conceder permisos para administrar bases de datos
En esta sección se describe cómo conceder permisos a un usuario de base de datos para administrar una base de datos en el dispositivo PDW de SQL Server.  
  
En algunas situaciones, una empresa asigna a un administrador de una base de datos. El administrador controla el acceso que tienen otros inicios de sesión en la base de datos, así como los datos y objetos en la base de datos. Para administrar todos los objetos, funciones, y los usuarios de una base de datos conceden al usuario la **CONTROL** permiso en la base de datos. La instrucción siguiente concede la **CONTROL** permiso en el **AdventureWorksPDW2012** base de datos para el usuario `KimAbercrombie`.  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Para conceder a un usuario el permiso para controlar todas las bases de datos en el dispositivo, conceda el **ALTER ANY DATABASE** permiso en la base de datos maestra.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Conceder permisos para administrar inicios de sesión, usuarios y Roles de base de datos
En esta sección se describe cómo conceder permisos para administrar los inicios de sesión, usuarios de base de datos y roles de base de datos.  
  
### <a name="PermsAdminConsole"></a>Conceder permisos para administrar inicios de sesión  
**Agregar o administrar inicios de sesión**  
  
Las siguientes instrucciones SQL crean un inicio de sesión denominado KimAbercrombie que puede crear nuevos inicios de sesión mediante el [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) instrucción y modificar inicios de sesión existentes mediante la [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) instrucción.  
  
El **ALTER ANY LOGIN** permiso otorga la capacidad para crear nuevos inicios de sesión y quitar existente. Una vez que existe un inicio de sesión, el inicio de sesión se puede administrar los inicios de sesión con la **ALTER ANY LOGIN** permiso o el **ALTER** permiso ese inicio de sesión. Un inicio de sesión puede cambiar la base de datos predeterminada y la contraseña para su propio inicio de sesión.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Conceder permisos para administrar sesiones de inicio de sesión  
Para tener la capacidad para ver todas las sesiones en el servidor requiere la **VIEW SERVER STATE** permiso. La capacidad para finalizar las sesiones de otros inicios de sesión requiere el **ALTER ANY CONNECTION** permiso. En el ejemplo siguiente se usa el `KimAbercrombie` inicio de sesión que creó anteriormente.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Conceder permiso para administrar los usuarios de base de datos  
Crear y quitar usuarios de base de datos requieren el **ALTER ANY USER** permiso. Administración de usuarios existentes requiere el **ALTER ANY USER** permiso o el **ALTER** permiso para ese usuario. En el ejemplo siguiente se usa el `KimAbercrombie` inicio de sesión que creó anteriormente.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Conceder permiso para administrar los Roles de base de datos  
Creación y eliminación de roles de base de datos definido por el usuario requiere el **ALTER ANY ROLE** permiso. En el ejemplo siguiente se usa el `KimAbercrombie` inicio de sesión y el uso que creó anteriormente.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Inicio de sesión, usuarios y los gráficos de permiso de rol  
Los siguientes gráficos pueden resultar confusos, pero se muestran los permisos de maneta cómo superiores (por ejemplo, CONTROL) incluyen permisos más granulares que pueden concederse por separado (por ejemplo, ALTER). Es una práctica recomendada siempre conceder la menor cantidad de permisos para un usuario completar sus tareas necesarias. Para ello, conceda permisos más específicos, en lugar de los permisos de nivel superior.  
  
**Permisos de inicio de sesión:**  
  
![Permisos de inicio de sesión de seguridad de APS](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Permisos de usuario:**  
  
![Permisos de usuario de seguridad de APS](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Permisos de rol:**  
  
![Permisos de rol de seguridad de APS](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Conceder permisos para la supervisión del dispositivo
El dispositivo PDW de SQL Server puede supervisarse mediante el uso de vistas del sistema de la consola de administrador o PDW de SQL Server. Los inicios de sesión requieren el nivel de servidor **VIEW SERVER STATE** permiso para supervisar el dispositivo. Inicios de sesión requieren el **ALTER ANY CONNECTION** permiso para terminar las conexiones mediante el uso de la consola de administración o el **KILL** comando. Para obtener información sobre los permisos necesarios para usar la consola de administración, consulte [conceder permisos para usar la consola de administración &#40;PDW de SQL Server&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Conceder permiso para supervisar el dispositivo mediante el uso de vistas del sistema  
Las siguientes instrucciones SQL crean un inicio de sesión denominado `monitor_login` y le concede el **VIEW SERVER STATE** permiso para el `monitor_login` inicio de sesión.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Conceder permiso para supervisar el dispositivo mediante el uso de vistas del sistema y para terminar las conexiones  
Las siguientes instrucciones SQL crean un inicio de sesión denominado `monitor_and_terminate_login` y le concede el **VIEW SERVER STATE** y **ALTER ANY CONNECTION** permisos para el `monitor_and_terminate_login` inicio de sesión.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Para crear los inicios de sesión de administrador, consulte [Roles fijos de servidor](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>Vea también
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[CREAR USUARIO](../t-sql/statements/create-user-transact-sql.md)  
[CREAR ROL](../t-sql/statements/create-role-transact-sql.md)  
[Cargar](load-overview.md)  
