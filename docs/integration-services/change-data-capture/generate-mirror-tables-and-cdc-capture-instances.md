---
description: Generar tablas reflejadas e instancias de captura CDC
title: Generar tablas reflejadas e instancias de captura CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8340ef153f815d3073edaf4f9a13e99e1e9f67
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2020
ms.locfileid: "88394811"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>Generar tablas reflejadas e instancias de captura CDC

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Use la página Generar tablas reflejadas para generar las tablas reflejadas para las tablas que se incluyeron en la instancia CDC.  
  
 Haga clic en **Ejecutar** para crear las tablas reflejadas. Se mostrará el progreso de la creación de cada tabla y aparecerá un mensaje para que sepa si cada tabla reflejada se completó correctamente o con errores. Si se produce algún error, haga clic en **Detalles** para ver un cuadro de diálogo con una explicación del error.  
  
 Si alguna de las tablas no se puede crear, puede elegir entre continuar o eliminar las tablas que produjeron errores antes de continuar. Cuando termine de ejecutar el asistente, puede decidir si desea corregir la tabla de la base de datos de origen de Oracle o no usarla en la instancia CDC. Si corrige la tabla, puede agregarla al [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
 Haga clic en **Siguiente** para abrir la página [Finish](../../integration-services/change-data-capture/finish.md) .  
  
## <a name="see-also"></a>Vea también  
 [Cómo crear la instancia de base de datos de cambios de SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
