---
title: KEY_GUID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Key_GUID_TSQL
- Key_GUID
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], GUIDs
- KEY_GUID function
- GUIDs [SQL Server]
ms.assetid: 9246c7b2-7098-42c4-a222-cbf30267c46a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1fbddf97fc08ffe0b200b1affa7258cc2746e0ca
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111940"
---
# <a name="key_guid-transact-sql"></a>KEY_GUID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Devuelve el GUID de una clave simétrica de la base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Key_GUID( 'Key_Name' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumentos
 **'** *Key_Name* **'**  
 El nombre de una clave simétrica en la base de datos.  
  
## <a name="return-types"></a>Tipos de valor devuelto  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Observaciones  
 Si se ha especificado un valor de identidad al crear la clave, su GUID es un hash MD5 de ese valor de identidad. Si no se ha especificado ningún valor de identidad, el GUID es generado por el servidor.  
  
 Si la clave es temporal, su nombre debe comenzar con un signo de número (#).  
  
## <a name="permissions"></a>Permisos  
 No se requieren permisos para el acceso a las claves temporales, dado que éstas solo están disponibles en la sesión en la que se crean. Para obtener acceso a una clave que no es temporal, el autor de la llamada necesita algún permiso en ella. Además no puede tener denegado el permiso VIEW en esa clave.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve el GUID de una clave simétrica denominada `ABerglundKey1`.  
  
```  
SELECT Key_GUID('ABerglundKey1');  
```  
  
## <a name="see-also"></a>Consulte también  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [sys.symmetric_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)  
  
  
