---
title: Relaciones de dimensión | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- relationships [Analysis Services]
- member groups [Analysis Services]
- regular dimensions [Analysis Services]
- many-to-many relationships [Analysis Services]
- cubes [Analysis Services], relationships
- reference dimensions
- dimensions [Analysis Services], relationships
- fact dimensions [Analysis Services]
- relationships [Analysis Services], dimensions
ms.assetid: de54c059-cb0f-4f66-bd70-8605af05ec4f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec3b57b08460b834868581ac8872ac3c78a38bbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "62727821"
---
# <a name="dimension-relationships"></a>Relaciones de dimensión
  El uso de la dimensión define las relaciones entre una dimensión de cubo y los grupos de medida de un cubo. Una dimensión de cubo es una instancia de una dimensión de base de datos que se utiliza en un cubo específico. Un cubo puede y suele tener dimensiones de cubo que no están directamente relacionadas con un grupo de medida, pero que podrían estar indirectamente relacionadas con el grupo de medida a través de otra dimensión o grupo de medida. Cuando se agrega un grupo de medida o dimensión de base de datos a un cubo, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intenta determinar el uso de dimensiones mediante el examen de las relaciones entre las tablas de dimensiones y tablas de hechos en la vista del origen de datos del cubo y mediante el examen las relaciones entre los atributos de dimensiones. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] establece automáticamente la configuración del uso de la dimensión para las relaciones que puede detectar.  
  
 Una relación entre una dimensión y un grupo de medida consta de las tablas de dimensiones y hechos que participan en la relación y un atributo de granularidad que especifica la granularidad de la dimensión del grupo de medida concreto.  
  
## <a name="regular-dimension-relationships"></a>Relaciones de dimensión normales  
 Hay una relación de dimensión normal entre una dimensión de cubo y un grupo de medida cuando la columna de clave de la dimensión se combina directamente con la tabla de hechos. Esta relación directa se basa en una relación de clave externa para la clave principal en la base de datos relacional subyacente, pero también podría basarse en una relación lógica que se define en la vista del origen de datos. Una relación de dimensión normal representa la relación entre tablas de dimensiones y una tabla de hechos en un diseño de esquema en estrella tradicional. Para obtener más información acerca de las relaciones regulares, vea [definir relaciones normales y propiedades de la relación Regular](../multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).  
  
## <a name="reference-dimension-relationships"></a>Relaciones de dimensión de referencia  
 Hay una relación de dimensión de referencia entre una dimensión de cubo y un grupo de medida cuando la columna de clave de la dimensión se combina indirectamente con la tabla de hechos mediante una clave de otra tabla de dimensiones, como se muestra en la siguiente ilustración.  
  
 ![Diagrama lógico, la relación de dimensión referenciada](../../../2014/analysis-services/dev-guide/media/as-refdimension1.gif "diagrama lógico, la relación de dimensión referenciada")  
  
 Una relación de dimensión de referencia representa la relación entre tablas de dimensiones y una tabla de hechos en un diseño de esquema de copo de nieve. Cuando las tablas de dimensiones se conectan en un esquema de copo de nieve, es posible definir una única dimensión mediante columnas de varias tablas, o bien, definir dimensiones independientes basadas en las tablas de dimensiones independientes y, a continuación, definir un vínculo entre ellas mediante la configuración de la relación de dimensión de referencia. La siguiente ilustración muestra una tabla de hechos denominada **InternetSales**, y dos tablas de dimensiones denominadas **cliente** y **Geography**, en un esquema de copo de nieve.  
  
 ![Esquema lógico, la relación de dimensión referenciada](../../../2014/analysis-services/dev-guide/media/as-refdim-schema1.gif "esquema lógico, la relación de dimensión referenciada")  
  
 Puede crear una dimensión con el **cliente** tabla como la tabla de dimensiones principal y la **Geography** incluida como una tabla relacionada. Entonces se define una relación normal entre la dimensión y el grupo de medida InternetSales.  
  
 Como alternativa, puede crear dos dimensiones relacionadas con el grupo de medida InternetSales: una dimensión basada en la **cliente** tabla y una dimensión basada en la **Geography** tabla. A continuación, puede relacionar la dimensión geográfica con el grupo de medida InternetSales mediante una relación de dimensión de referencia por medio de la dimensión de cliente. En este caso, cuando los hechos del grupo de medida InternetSales están influenciados por la dimensión geográfica, los hechos están influenciados por Customer y Geography. Si el cubo contiene un segundo grupo de medida denominado Reseller Sales, no podrá dimensionar los hechos del grupo de medida Reseller Sales por Geography, dado que no existiría relación entre Reseller Sales y Geography.  
  
 No hay ningún límite con respecto al número de dimensiones de referencia que se pueden encadenar, como se muestra en la siguiente ilustración.  
  
 ![Diagrama lógico, la relación de dimensión referenciada](../../../2014/analysis-services/dev-guide/media/as-refdimension2.gif "diagrama lógico, la relación de dimensión referenciada")  
  
 Para obtener más información acerca de las relaciones que se hace referencia, consulte [definir una relación que se hace referencia y las propiedades de relación que se hace referencia](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md).  
  
## <a name="fact-dimension-relationships"></a>Relaciones de dimensión de hechos  
 Las dimensiones de hechos, más conocidas como dimensiones degeneradas, son dimensiones estándar que se crean a partir de columnas de atributos de tablas de hechos en lugar de columnas de atributos de tablas de dimensiones. Los datos útiles de dimensiones algunas veces se almacenan en una tabla de hechos para reducir la duplicación. Por ejemplo, el siguiente diagrama se muestra el **FactResellerSales** tabla de hechos, desde el [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] base de datos de ejemplo.  
  
 ![Columnas de hecho tabla puede admitir dimensiones](../../../2014/analysis-services/dev-guide/media/as-factdim.gif "columnas en realidad la tabla puede admitir las dimensiones")  
  
 La tabla contiene información sobre atributos no solo para cada línea de un pedido emitido por un distribuidor, sino sobre el propio pedido. Los atributos en un círculo en el diagrama anterior identifican los datos de la **FactResellerSales** tabla que podría utilizarse como atributos de una dimensión. En este caso, dos piezas adicionales de información, el número de seguimiento del transportista y el número de orden de compra emitido por el distribuidor están representados por las columnas de atributo CarrierTrackingNumber y CustomerPONumber. Esta información es interesante-por ejemplo, los usuarios definitivamente estaría interesados en ver la información agregada, como el costo de todos los pedidos que se envían con un número de seguimiento único total del producto. Sin embargo, sin una dimensión no se pueden organizar ni agregar datos para estos dos atributos.  
  
 En teoría, se podría crear una tabla de dimensiones que utilizara la misma información de clave que la tabla FactResellerSales y mover las otras dos columnas de atributos, CarrierTrackingNumber y CustomerPONumber, a esa tabla de dimensiones. Sin embargo, así se duplicaría una parte significativa de los datos y se agregaría una complejidad innecesaria al almacenamiento de datos para poder representar solo dos atributos como una dimensión independiente.  
  
> [!NOTE]  
>  Las dimensiones de hechos se suelen utilizar para permitir acciones de obtención de detalles. Para más información sobre las acciones, vea [Acciones &#40;Analysis Services - Datos multidimensionales&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Las dimensiones de hechos deben actualizarse incrementalmente después de cada actualización al grupo de medida al que hace referencia la relación de hechos. Si la dimensión de hechos es una dimensión ROLAP, el motor de procesamiento de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] elimina todas las cachés y procesa incrementalmente el grupo de medida.  
  
 Para obtener más información acerca de las relaciones de hechos, vea [definir una relación de hechos y propiedades de la relación de hechos](../multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).  
  
## <a name="many-to-many-dimension-relationships"></a>Relaciones de dimensión varios a varios  
 En la mayoría de dimensiones, cada hecho se combina con un solo miembro de la dimensión y un único miembro de la dimensión puede asociarse a varios hechos. En terminología de bases de datos relacionales, esto se conoce como relación de uno a varios. No obstante, suele resultar útil combinar un único hecho con varios miembros de dimensión. Por ejemplo, un cliente de un banco podría tener varias cuentas (cuenta corriente, libreta de ahorro, tarjetas de crédito y cuentas de inversión) y una cuenta también puede tener varios propietarios. La dimensión de cliente creada a partir de estas relaciones tendrá varios miembros relacionados con una única transacción de cuenta.  
  
 ![Relación de dimensión lógica esquema /-to-many](../../../2014/analysis-services/dev-guide/media/as-many-dimension1.gif "lógico esquema /-to-many relación de dimensión")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] le permite definir una relación de varios a varios entre una dimensión y una tabla de hechos.  
  
> [!NOTE]  
>  Para admitir una relación de dimensión de varios a varios, la vista del origen de datos debe haber establecido una relación de clave externa entre todas las tablas implicadas, tal y como se muestra en el diagrama anterior. En caso contrario, no será posible seleccionar el grupo de medida intermedio correcto al establecer la relación en el **uso de dimensiones** ficha del Diseñador de dimensiones.  
  
 Para obtener más información acerca de las relaciones de varios a varios, vea [definir muchos a muchos relación y -to-Many las propiedades de relación](../multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).  
  
## <a name="see-also"></a>Vea también  
 [Dimensiones &#40;Analysis Services - Datos multidimensionales&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
