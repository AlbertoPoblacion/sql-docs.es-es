---
title: Tipos definidos por el usuario CLR grandes | Microsoft Docs
description: Tipos definidos por el usuario CLR grandes en OLE DB controlador para SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: pmasl
ms.author: pelopes
ms.openlocfilehash: acbdd170808ed9f6d7f67265a4e0d18f3b9e8eb0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989073"
---
# <a name="large-clr-user-defined-types"></a>Tipos definidos por el usuario de CLR grandes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  En SQL Server 2005, los tipos definidos por el usuario (UDT) en Common Language Runtime (CLR) estaban restringidos a un tamaño de 8.000 bytes. Esta restricción se soluciona en [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] y versiones posteriores. Los UDT CLR se tratan ahora de una manera similar a los tipos de objeto grandes (LOB). Es decir, los UDT con un tamaño menor o igual que 8.000 bytes se comportan de la misma manera que en SQL Server 2005, pero se admiten UDT de mayor tamaño y notifican su tamaño como "ilimitado".  
  
 Para obtener más información, vea [ &#40;tipos CLR grandes definidos por el&#41;usuario OLE DB](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md).  
  
## <a name="use-cases"></a>Casos de uso   
  
 Para OLE DB, la compatibilidad con UDT grandes incluye la capacidad de transmitir en secuencias los valores del UDT a y desde el servidor mediante el enlace ISequentialStream.  
  
 Los UDT con un tamaño menor o igual que 8.000 se comportarán como lo hacían en SQL Server 2005. Por OLE DB, puede seguir transmisiones de UDT pequeños mediante el enlace ISequentialStream.  
  
 A veces el código nativo tendrá que entender el contenido de los UDT CLR, pero no tendrá que crear instancias de los objetos administrados. Si éste es el caso, puede utilizar la serialización personalizada para convertir los valores de UDT en el servidor en un formato bien conocido para los clientes.  
  
 Para las aplicaciones que tienen código de acceso a datos existente, puede aprovechar el comportamiento de los UDT CLR en el cliente recuperando los UDT a través de API nativas y creando instancias de ellos utilizando la interoperabilidad de C++ CLI en aplicaciones de modo mixto.  
  
## <a name="see-also"></a>Consulte también  
 [Controlador OLE DB para las características de SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
