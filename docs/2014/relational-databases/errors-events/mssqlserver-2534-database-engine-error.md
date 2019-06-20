---
title: MSSQLSERVER_2534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ed3a5a48a4c327decc75e37142c77d7d4ee52f1d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914674"
---
# <a name="mssqlserver2534"></a>MSSQLSERVER_2534
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|2534|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT|  
|Texto del mensaje|Error de tabla: Page P_ID, cuyo encabezado indica ya está asignada a un objeto ID O_ID, ID. de partición PN_ID, índice de unidad de asignación ID A_ID (tipo TYPE), está asignada mediante otro objeto.|  
  
## <a name="explanation"></a>Explicación  
 El encabezado de la página contiene el Id. de unidad de asignación, *A_ID*, pero ninguna de las páginas IAM (Mapa de asignación de índices) de esa unidad de asignación asigna la página. Por tanto, el encabezado de la página contiene un Id. de unidad de asignación incorrecto y la página tendrá un error de coincidencia MSSQLServer_2533 que corresponde al Id. de unidad de asignación al que la página está realmente asignada.  
  
## <a name="user-action"></a>Acción del usuario  
  
### <a name="look-for-hardware-failure"></a>Busque un error de hardware  
 Ejecute un diagnóstico de hardware y corrija cualquier problema. Examine también los registros del sistema y de aplicación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows así como el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ver si el error se produjo como resultado de un error de hardware. Arregle cualquier problema relacionado con el hardware que encuentre en estos registros.  
  
 Si sigue teniendo problemas de datos dañados, intente intercambiar diferentes componentes de hardware para aislar el problema. Asegúrese de que el sistema no tiene habilitada la memoria caché de escritura en el controlador de disco. Si cree que el problema se debe a la caché de escritura, póngase en contacto con su proveedor de hardware.  
  
 Finalmente, puede resultarle útil cambiar a un nuevo sistema de hardware. Este cambio puede incluir volver a formatear las unidades de disco y volver a instalar el sistema operativo.  
  
### <a name="restore-from-backup"></a>Restaure mediante la copia de seguridad  
 Si el problema no está relacionado con el hardware y tiene una copia de seguridad limpia disponible, úsela para restaurar la base de datos.  
  
### <a name="run-dbcc-checkdb"></a>Ejecute DBCC CHECKDB  
 Si no tiene disponible una copia de seguridad limpia, ejecute DBCC CHECKDB sin una cláusula REPAIR para determinar el alcance de los daños. DBCC CHECKDB recomendará el uso de una cláusula REPAIR. A continuación, ejecute DBCC CHECKDB con la cláusula REPAIR apropiada para reparar el problema.  
  
> [!CAUTION]  
>  Si no está seguro del efecto que tendrá DBCC CHECKDB con una cláusula REPAIR en los datos, póngase en contacto con su proveedor principal de soporte antes de ejecutar esta instrucción.  
  
 Si ejecuta DBCC CHECKDB con una de las cláusulas REPAIR y no se soluciona el problema, póngase en contacto con su proveedor principal de soporte.  
  
### <a name="results-of-running-repair-options"></a>Resultados de ejecutar opciones REPAIR  
 REPAIR vuelve a generar el índice (si existe).  
  
> [!CAUTION]  
>  Al ejecutar REPAIR para el error de coincidencia [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md), se cancela la asignación de la página antes de la reconstrucción.  
  
> [!CAUTION]  
>  Esta reparación puede causar la pérdida de datos.  
  
  
