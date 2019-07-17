---
title: Administrar los cambios en las vistas del origen de datos y orígenes de datos | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f8cb72fe4650cd76465207f3e7cd529e2a7b032
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208815"
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>Administrar los cambios de las vistas del origen de datos y los orígenes de datos
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Si se vuelve a ejecutar el Asistente para generar esquemas, éste volverá a utilizar el mismo origen de datos y vista del origen de datos que en la generación original. Si se agrega un origen de datos o una vista de origen de datos, el asistente no los utilizará. Si se elimina el origen de datos o la vista de origen de datos originales tras la generación inicial, debe ejecutarse el asistente desde el principio. También se eliminará la configuración anterior del asistente. Los objetos existentes en una base de datos subyacente enlazados a un origen de datos o vista de origen de datos eliminados se tratarán como objetos creados por el usuario la próxima vez que se ejecute el Asistente para generar esquemas.  
  
 Si la vista del origen de datos no refleja el estado actual de la base de datos subyacente en el momento de la generación, el Asistente para generar esquemas podría experimentar errores al generar el esquema de la base de datos del área de asunto. Por ejemplo, si la vista del origen de datos especifica que el tipo de datos de una columna es **int**, pero el tipo de datos de la columna es en realidad **string**, el Asistente para generar esquemas establecerá el tipo de datos de la clave externa en **INT** para que coincida con la vista del origen de datos, aunque se producirá un error al crear la relación dado que el tipo de datos real es **string**.  
  
 Por otra parte, no se generarán errores si se cambia la cadena de conexión de origen de datos a una base de datos distinta de la generación anterior. Se utilizará la nueva base de datos y no se realizarán cambios en la base de datos anterior.  
  
## <a name="see-also"></a>Vea también  
 [Descripción de la generación incremental](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  
