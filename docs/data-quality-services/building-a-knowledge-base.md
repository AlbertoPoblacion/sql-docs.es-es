---
description: Crear una base de conocimiento
title: Crear una base de conocimiento
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: swinarko
ms.author: sawinark
ms.openlocfilehash: e5914d97a8110f9b50ecfd20da7130c564aac840
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450003"
---
# <a name="building-a-knowledge-base"></a>Crear una base de conocimiento

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Una base de conocimiento de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) es un repositorio de conocimiento sobre los datos que le permite comprenderlos y mantener su integridad. Una base de conocimiento consta de dominios, cada uno de los cuales representa los datos de un campo de datos. DQS utiliza la base de conocimiento para realizar la limpieza de datos y la eliminación de datos duplicados en una base de datos. Para preparar la base de conocimiento para la limpieza de datos, puede ejecutar un análisis asistido por PC de una muestra de los datos, así como administrar de forma interactiva los valores de los dominios. DQS le permite importar conocimiento, crear reglas y relaciones, cambiar los valores de los datos directamente y utilizar una base de datos predeterminada.  
  
## <a name="in-this-section"></a>En esta sección  
 En una base de conocimiento puede realizar las operaciones siguientes:  
  
|Descripción de la operación|Tema|  
|-|-|  
|Crear una nueva base de conocimiento desde cero, a partir de una base de conocimiento existente o a partir de un archivo de datos .dqs.|[Crear una base de conocimiento](../data-quality-services/create-a-knowledge-base.md)|  
|Abrir una base de conocimiento existente para realizar la detección de conocimiento, la administración de dominios o para agregar una directiva de coincidencia.|[Abrir una base de conocimiento](../data-quality-services/open-a-knowledge-base.md)|  
|Realizar acciones de administración en una base de conocimiento, como abrirla, desbloquearla, descartar los cambios realizados en ella, cambiarla de nombre, eliminarla o ver sus propiedades.|[Administrar una base de conocimiento](../data-quality-services/manage-a-knowledge-base.md)|  
|Agregar conocimiento a una base de conocimiento mediante la detección de conocimiento; la administración de los valores del dominio; la adición de una directiva de coincidencia; la importación de un conocimiento, un dominio o determinados valores; o el uso de la base de conocimiento predeterminada, Datos de DQS.|[Agregar conocimiento a una base de conocimiento](../data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|Analizar una muestra de datos para los criterios de calidad de los datos.|[Realizar la detección de conocimiento](../data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Importar conocimiento en una base de conocimiento o exportarlo desde esta.|[Importar y exportar conocimiento](../data-quality-services/importing-and-exporting-knowledge.md)|  
|Crear un dominio individual y agregarle conocimiento.|[Administrar un dominio](../data-quality-services/managing-a-domain.md)|  
|Crear un dominio compuesto y agregarle conocimiento.|[Administrar un dominio compuesto](../data-quality-services/managing-a-composite-domain.md)|  
  
  
