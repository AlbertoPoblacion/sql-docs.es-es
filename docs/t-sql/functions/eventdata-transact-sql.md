---
title: EVENTDATA (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EVENTDATA
- fn_event_data
- EVENTDATA_TSQL
- fn_event_data_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server instance event data [SQL Server]
- event notifications [SQL Server], event status
- events [SQL Server], status information
- EVENTDATA function
- status information [SQL Server], events
- DDL triggers, returning event data
ms.assetid: 03a80e63-6f37-4b49-bf13-dc35cfe46c44
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aed9a65000724b1b3ac7750fde45dddebbe3682d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "65946113"
---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Esta función devuelve información acerca de los eventos de base de datos o servidor. `EVENTDATA` se llama cuando se activa una notificación de eventos y el resultado se devuelve al Service Broker especificado. Un desencadenador DDL o LOGON también admite el uso interno de `EVENTDATA`.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>Notas  
`EVENTDATA` devuelve datos solo cuando se hace referencia al mismo directamente dentro de un desencadenador DDL o LOGON. `EVENTDATA` devuelve NULL si otras rutinas lo llaman, incluso si un desencadenador DDL o LOGON llama a esas rutinas.
  
Los datos que `EVENTDATA` devuelve no son válidos después de una transacción que

+ llamó a `EVENTDATA` de manera explícita
+ llamó a `EVENTDATA` de manera implícita
+ se confirma
+ se revierte  
  
> [!CAUTION]  
>  `EVENTDATA` devuelve datos de XML, enviados al cliente como Unicode que usa 2 bytes para cada carácter. `EVENTDATA` devuelve XML que puede representar estos puntos de código de Unicode:  
>   
>  `0x0009`  
>   
>  `0x000A`  
>   
>  `0x000D`  
>   
>  `>= 0x0020 && <= 0xD7FF`  
>   
>  `>= 0xE000 && <= 0xFFFD`  
>   
>  XML no puede expresar, ni permitirá, algunos caracteres que pueden aparecer en los datos e identificadores de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Los caracteres o datos que tienen puntos de código que no se muestran en la lista anterior se asignan a un signo de interrogación (?).  
  
Las contraseñas no se muestran cuando se ejecutan las instrucciones `CREATE LOGIN` o `ALTER LOGIN`. Esto protege la seguridad del inicio de sesión.  
  
## <a name="schemas-returned"></a>Esquemas devueltos  
EVENTDATA devuelve un valor de tipo de datos **xml**. De forma predeterminada, la definición del esquema para todos los eventos se instala en este directorio: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.  
  
La página web [Esquemas XML de Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkID=31850) también tiene el esquema de eventos.  
  
Para extraer el esquema de un evento concreto, busque el esquema del tipo complejo `EVENT_INSTANCE_<event_type>`. Por ejemplo, para extraer el esquema del evento `DROP_TABLE`, busque el esquema de `EVENT_INSTANCE_DROP_TABLE`.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. Consultar datos de evento en un desencadenador DDL  
En este ejemplo se crea un desencadenador DDL que impide la creación de nuevas tablas de bases de datos. El uso de XQuery con los datos XML generados por `EVENTDATA` captura la instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] que activa el desencadenador. Consulte [Referencia del lenguaje XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md) para más información.  
  
> [!NOTE]  
>  Cuando se usa **Resultados a cuadrícula** en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para consultar el elemento `<TSQLCommand>`, no se muestran los saltos de línea en el texto del comando. Es preferible usar **Resultados a texto**.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value  
        ('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
GO  
--Test the trigger.  
CREATE TABLE NewTable (Column1 int);  
GO  
--Drop the trigger.  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
> [!NOTE]  
>  Para devolver datos de evento, use el método XQuery **value()** en lugar del método **query()** . El método **query()** devuelve XML e instancias de retorno de carro y avance de línea (CR/LF) con el carácter de escape “y” comercial en el resultado, mientras que el método **value()** representa instancias de CR/LF invisibles en el resultado.  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>B. Crear una tabla de registro con datos de evento en un desencadenador DDL  
En este ejemplo se crea una tabla para almacenar información sobre todos los eventos de nivel de base de datos y rellena esa tabla con un desencadenador DDL. El uso de XQuery con los datos XML generados por `EVENTDATA` captura el tipo de evento y la instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger.  
CREATE TABLE TestTable (a int);  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
--Drop the trigger.  
DROP TRIGGER log  
ON DATABASE;  
GO  
--Drop table ddl_log.  
DROP TABLE ddl_log;  
GO  
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar la función EVENTDATA](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [Desencadenadores DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [Notificaciones de eventos](../../relational-databases/service-broker/event-notifications.md)   
 [Desencadenadores logon](../../relational-databases/triggers/logon-triggers.md)  
  
  
