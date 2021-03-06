---
title: Dimensiones en modelos multidimensionales | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 6ae68ab8b879656940827bf8ebffb5c1f40cfa0b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="dimensions-in-multidimensional-models"></a>Dimensiones en modelos multidimensionales
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Una dimensión de base de datos es una colección de objetos relacionados, denominados atributos, que se pueden usar para proporcionar información sobre los datos de hechos de uno o varios cubos. Por ejemplo, los atributos típicos de una dimensión de producto pueden ser el nombre, la categoría, la línea, el tamaño y el precio del producto. Estos objetos están enlazados a una o varias columnas de una o varias tablas de una vista del origen de datos. De manera predeterminada, estos atributos están visibles como jerarquías de atributo y se pueden utilizar para comprender los datos de hechos en un cubo. Los atributos se pueden organizar en jerarquías definidas por el usuario que proporcionan rutas de navegación para ayudar a los usuarios al examinar los datos de un cubo.  
  
 Los cubos contienen todas las dimensiones en las que los usuarios basan sus análisis de los datos de hechos. Una instancia de una dimensión de base de datos en un cubo se denomina dimensión de cubo y se relaciona con uno o más grupos de medida en el cubo. Una dimensión de base de datos se puede utilizar varias veces en un cubo. Por ejemplo, una tabla de hechos puede tener varios hechos relacionados con el tiempo y se puede definir una dimensión de cubo independiente que sirva de ayuda para analizar cada uno de ellos. Sin embargo, solo es necesario que haya una dimensión de base de datos relacionada con el tiempo, lo que significa también que solo es necesario que haya una tabla de base de datos relacional relacionada con el tiempo para admitir varias dimensiones de cubo basadas en el tiempo.  
  
> [!NOTE]  
>  Para obtener información sobre los problemas de rendimiento relacionados con el diseño de dimensiones, vea la [Guía de rendimiento de SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=306717).  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>Definir dimensiones, atributos y jerarquías  
 El método más simple para definir dimensiones, atributos y jerarquías de base de datos y de cubo es utilizar el Asistente para cubos para crear las dimensiones a la vez que se define el cubo. El Asistente para cubos creará dimensiones basadas en las tablas de dimensiones en la vista del origen de datos que el asistente identifique o que el usuario especifique para su uso en el cubo. A continuación, el asistente crea las dimensiones de base de datos y las agrega al cubo nuevo, con lo que se crean dimensiones de cubo.  
  
 Cuando se crea un cubo, también se pueden agregar al nuevo cubo las dimensiones que existen en la base de datos. Estas dimensiones pueden haber sido definidas previamente para otro cubo o por el Asistente para dimensiones. Una vez definida una dimensión de base de datos, no puede modificar ni configurar la dimensión de base de datos en el Diseñador de dimensiones. También puede personalizar la dimensión de cubo, de forma limitada, en el Diseñador de cubos  
  
> [!NOTE]  
>  Además puede diseñar y configurar dimensiones, atributos y jerarquías mediante programación utilizando XMLA u Objetos de administración de análisis (AMO). Para más información, vea [Referencia de Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) y [Desarrollar con Objetos de administración de análisis &#40;AMO&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="in-this-section"></a>En esta sección  
 En la tabla siguiente se describen los temas de esta sección.  
  
 [Definir dimensiones de base de datos](../../analysis-services/multidimensional-models/define-database-dimensions.md)  
 Describe cómo modificar y configurar una dimensión de base de datos mediante el Diseñador de dimensiones.  
  
 [Referencia de propiedades de atributos de dimensión](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
 Describe cómo definir, modificar y configurar un atributo de dimensión de base de datos mediante el Diseñador de dimensiones.  
  
 [Definir relaciones de atributo](../../analysis-services/multidimensional-models/attribute-relationships-define.md)  
 Describe cómo definir, modificar y configurar una relación de atributo mediante el Diseñador de dimensiones.  
  
 [Crear jerarquías definidas por el usuario](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
 Describe cómo definir, modificar y configurar una jerarquía definida por el usuario de atributos de dimensión mediante el Diseñador de dimensiones.  
  
 [Usar al Asistente de Business Intelligence para mejorar dimensiones](http://msdn.microsoft.com/library/12d995d1-75ca-4890-bf4b-a2656910b8d0)  
 Describe cómo mejorar una dimensión de base de datos mediante el Asistente de Business Intelligence.  
  
## <a name="see-also"></a>Vea también  
 [Cubos en modelos multidimensionales](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
