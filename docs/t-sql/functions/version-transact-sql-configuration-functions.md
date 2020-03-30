---
title: '@@VERSION (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/20/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1894f0e4aa31e8b80255fb49f30c7cfe1c1a146b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "67927533"
---
# <a name="x40x40version---transact-sql-configuration-functions"></a>&#x40;&#x40;Version - Funciones de configuración Transact SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve información del sistema y la compilación para la instalación actual de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
@@VERSION  
```  
  
## <a name="return-types"></a>Tipos de valor devuelto  
 **nvarchar**  
  
## <a name="remarks"></a>Observaciones  
 Los resultados de @@VERSION se presentan como una cadena nvarchar. Puede usar la función [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md) para recuperar los valores de propiedad individuales.  
  
 En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se devuelve la siguiente información.  
  
-   Versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Arquitectura del procesador  
  
-   Fecha de compilación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Instrucción de copyright  
  
-   Edición de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Versión del sistema operativo  
  
 En [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], se devuelve la siguiente información.  
  
-   Edición: "Microsoft SQL Azure"  
  
-   Nivel de producto: "(RTM)"  
  
-   Versión del producto  
  
-   Fecha de compilación  
  
-   Instrucción de copyright  

> [!NOTE]  
> Somos conscientes de que hay un problema con el número de versión de producto en Azure SQL Database del que nos ha informado @@VERSION. La versión del motor de base de datos de SQL Server que ejecuta Azure SQL Database va siempre por delante de la versión local de SQL Server e incluye las correcciones de seguridad más recientes. Esto significa que el nivel de revisión siempre va a la par de la versión local de SQL Server, o incluso por delante, y que las características más recientes disponibles en SQL Server están disponibles en Azure SQL Database.
>
> Para determinar mediante programación la edición del motor, use SELECT SERVERPROPERTY('EngineEdition'). Esta consulta devolverá "5" para los grupos elásticos y bases de datos únicas y "8" para las instancias administradas en Azure SQL Database. 
>
> Una vez que se resuelva este problema, se actualizará la documentación.

  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-return-the-current-version-of-ssnoversion"></a>A. Devolver la versión actual de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 En el ejemplo siguiente se muestra cómo devolver la información de versión de la instalación actual.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Ejemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] y [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-ssdw"></a>B. Devolver la versión actual de [!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>Consulte también  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

