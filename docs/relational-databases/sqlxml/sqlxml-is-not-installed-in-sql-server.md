---
title: SQLXML no está instalado en SQL Server | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2adac1703facccda712db1e3f5826f784c0be141
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135323"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML no se instala en SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Antes de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 se comercializó junto con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y formó parte de la instalación predeterminada de todas las versiones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], salvo [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. A partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la última versión de SQLXML (SQLXML 4.0 SP1) ya no está incluida en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para instalar SQLXML 4.0 SP1, descárguelo desde [ubicación de instalación para SQLXML 4.0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).  
  
 Si una aplicación se ejecuta en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y requiere SQLXML 4.0, tendrá que descargar e instalar SQLXML 4.0 SP1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Comportamiento de SQLXML 4.0 SP1 con nuevos tipos de datos que usan el proveedor OLE DB de SQLOLEDB y SQL Server Native Client  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] presenta a los siguientes tipos de datos, es posible que desee utilizar que los desarrolladores de SQLXML:  
  
-   **Date**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 Cuando se usa SQLXML 4.0 SP1 con SQLOLEDB o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB de Native Client desde [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], estos tipos aparecen como cadenas a un desarrollador. SQLXML 4.0 SP1 habilitará estos cuatro nuevos tipos de datos como tipos escalares integrados cuando se usa con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de cliente nativo 11.0 o versiones posterior. Hasta que descargue SQLXML 4.0 SP1, la asignación de estos tipos a tipos que no sean de cadena puede producir el truncamiento de algunos datos. Por ejemplo, la asignación **DateTime2** a **xsd: Date** hará que los datos se trunquen a la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** precisión de 3,33 milisegundos.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos de programación en SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
