---
title: Compatibilidad con traducción en Analysis Services | Microsoft Docs
ms.date: 01/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd727b56649ce9ffc237575b0311db256ec9b2fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207425"
---
# <a name="translation-support-in-analysis-services"></a>Compatibilidad con traducción en Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  En [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] modelos de datos, puede incrustar varias traducciones de un título o descripción para proporcionar cadenas específicas según el identificador de configuración regional (LCID). En el caso de los modelos multidimensionales, se pueden agregar traducciones del nombre de la base de datos, los objetos del cubo y los objetos de dimensión de la base de datos. En el caso de los modelos tabulares, puede traducir las descripciones y títulos de tabla y columna.  
  
 Al definir una traducción, se crean los metadatos y el título traducido dentro del modelo, pero para que se representen cadenas localizadas en una aplicación cliente, deberá configurar la propiedad **Language** en el objeto o pasar un parámetro **Culture** o **Locale Identifier** en la cadena de conexión (por ejemplo, estableciendo `LocaleIdentifier=1036` para devolver cadenas en francés).  
  
 Utilice **Locale Identifier** si quiere admitir varias traducciones simultáneas del mismo objeto en diferentes idiomas. Si configura la propiedad **Language** , funcionará, pero esto afectará también al procesamiento y a las consultas, lo cual podría tener consecuencias no deseadas. Configurar **Locale Identifier** es la mejor opción, porque solo se utiliza para devolver las cadenas traducidas.  
  
 Una traducción está formada por un identificador de configuración regional (LCID), un título traducido del objeto (por ejemplo, el nombre de la dimensión o el atributo) y, si se quiere, un enlace a una columna que proporciona los valores de los datos en el idioma de destino. Puede tener varias traducciones, pero solo puede utilizar una para cada una de las conexiones. No hay ningún límite teórico en la cantidad de traducciones que puede incrustar en el modelo, pero cada traducción agrega complejidad a las pruebas y todas las traducciones deben compartir la misma intercalación. Por lo tanto, al diseñar la solución, tenga en cuenta estas restricciones naturales.  
  
> [!TIP]  
>  Puede usar las aplicaciones cliente como Excel, SQL Server Management Studio y SQL Server Profiler para devolver las cadenas traducidas. Para más información, vea [Sugerencias de globalización y procedimientos recomendados &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md) .  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Incorporación de metadatos traducidos al modelo de Analysis Services  
 Visite estos vínculos para obtener instrucciones paso a paso:  
  
-   [Traducciones en modelos tabulares](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Traducciones en modelos multidimensionales](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>Vea también  
 [Escenarios de globalización para Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Idiomas e intercalaciones &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)   
 [Establecer o cambiar la intercalación de columnas](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Sugerencias de globalización y procedimientos recomendados &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
