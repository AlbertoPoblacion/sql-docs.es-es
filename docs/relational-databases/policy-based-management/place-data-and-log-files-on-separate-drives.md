---
title: Colocación de los datos y los archivos de registro en unidades independientes | Microsoft Docs
description: Coloque los datos y los archivos de registro en unidades lógicas independientes. Las ubicaciones independientes permiten que la actividad de cada una de ellas se produzca al mismo tiempo, lo que mejora el rendimiento de SQL.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7c0ed515a8fe166d4b53fec5750fa3b09a48a06a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716854"
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Colocar los datos y los archivos de registro en unidades independientes
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Esta regla comprueba si los datos y archivos de registro se colocan en unidades lógicas independientes. Al colocar tanto los archivos de registro como los datos en el mismo dispositivo, se puede ocasionar la contención para ese dispositivo y provocar un rendimiento escaso. Colocar los archivos en unidades de disco independientes permite que la actividad de E/S tenga lugar al mismo tiempo para los archivos de registro y los datos.  
  
## <a name="recommendations"></a>Recomendaciones  
 Al crear una base de datos nueva, especifique unidades independientes para los datos y el registro. Para mover los archivos una vez creada la base de datos, esta debe ponerse sin conexión. Mueva los archivos utilizando alguno de los siguientes métodos:  
  
> [!NOTE]  
>  Esta directiva no puede detectar dispositivos físicos independientes mediante puntos de montaje  
  
-   Restaure la base de datos a partir de la copia de seguridad utilizando la instrucción RESTORE DATABASE con la opción WITH MOVE.  
  
-   Desasocie y, a continuación, asocie la base de datos especificando ubicaciones independientes para los datos y los dispositivos de registro.  
  
-   Especifique una ubicación nueva ejecutando la instrucción ALTER DATABASE con la opción MODIFY FILE y reiniciando a continuación la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="for-more-information"></a>Para obtener más información  
 [Mover archivos de base de datos](../../relational-databases/databases/move-database-files.md)  
  
 [Mover bases de datos de usuario](../../relational-databases/databases/move-user-databases.md)  
  
 [Adjuntar y separar bases de datos &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>Consulte también  
 [Supervisar y aplicar las prácticas recomendadas usando la administración basada en directivas](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
