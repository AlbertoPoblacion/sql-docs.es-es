---
title: '@@SERVERNAME (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: ''
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 40f441998f2f5055bdacb0ac6d796a6d3ad56f68
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2018
---
# <a name="x40x40servername-transact-sql"></a>&#x40;&#x40;SERVERNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el nombre del servidor local en el que se ejecuta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Icono de vínculo de artículo](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 **nvarchar**  
  
## <a name="remarks"></a>Notas  
 El programa de instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] establece durante la instalación el nombre del equipo como nombre de servidor. Para cambiar el nombre del servidor, use **sp_addserver** y después reinicie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si tiene instaladas varias instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], @@SERVERNAME devuelve la siguiente información del nombre del servidor local, siempre que el nombre no se haya cambiado desde la instalación.  
  
|Instancia|Información de servidor|  
|--------------|------------------------|  
|Instancia predeterminada|'*servername*'|  
|Instancia con nombre|'*servername*\\*instancename*'|  
|instancia en clúster de conmutación por error: instancia predeterminada|'*virtualservername*'|  
|instancia en clúster de conmutación por error: instancia con nombre|'*virtualservername*\\*instancename*'|  
  
 Aunque la función @@SERVERNAME y la propiedad SERVERNAME de la función SERVERPROPERTY puedan devolver cadenas con formatos similares, la información puede ser distinta. La propiedad SERVERNAME informa automáticamente de los cambios en el nombre de red del equipo.  
  
 Por el contrario, @@SERVERNAME no informa de estos cambios. @@SERVERNAME informa de los cambios realizados en el nombre del servidor local utilizando el procedimiento almacenado **sp_addserver** o **sp_dropserver**.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se muestra la forma de utilizar `@@SERVERNAME`.  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 A continuación se muestra un conjunto de resultados de ejemplo.  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>Ver también  
 [Funciones de configuración &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  
