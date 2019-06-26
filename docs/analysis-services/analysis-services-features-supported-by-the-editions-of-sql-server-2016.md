---
title: Características compatibles con las ediciones de SQL Server Analysis Services | Microsoft Docs
ms.date: 06/25/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9947b10e01864f66bf26d6599e43814ab37dadc6
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388206"
---
# <a name="analysis-services-features-supported-by-sql-server-edition"></a>Características de Analysis Services compatibles con la edición de SQL Server
[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

En este artículo se describe las características admitidas por las diferentes ediciones de SQL Server 2016, 2017, 2019 Analysis Services. Edición de evaluación es compatible con las características de Enterprise edition.

## <a name="analysis-services-servers"></a>Analysis Services (servidores)
  
|Característica|Enterprise|Estándar|Web|Express con Advanced Services|Express con herramientas|Express|Desarrollador|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Bases de datos compartidas escalables|Sí||||||Sí|  
|Copia de seguridad y restauración, y adjuntar y separar bases de datos|Sí|Sí|||||Sí|  
|Sincronizar bases de datos|Sí||||||Sí|  
|Instancias de clúster de conmutación por error de AlwaysOn|Sí<br /><br /> El número de nodos es el sistema operativo máximo|Sí<br /><br /> Compatibilidad con 2 nodos|||||Sí<br /><br /> El número de nodos es el sistema operativo máximo|  
|Programación (AMO, ADOMD.Net, OLEDB, XML/A, ASSL y TMSL)|Sí|Sí|||||Sí|  
  
## <a name="tabular-models"></a>Modelos tabulares 
  
|Característica|Enterprise|Estándar|Web|Express con Advanced Services|Express con herramientas|Express|Desarrollador|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Jerarquías|Sí|Sí|||||Sí|  
|KPI|Sí|Sí|||||Sí|  
|perspectivas|Sí||||||Sí|  
|Translations|Sí|Sí|||||Sí|  
|Cálculos de DAX, consultas de DAX, consultas MDX|Sí|Sí|||||Sí|  
|Seguridad de nivel de fila|Sí|Sí|||||Sí|  
|Varias particiones|Sí||||||Sí|  
|Grupos de cálculo|Sí (a partir de SQL Server 2019)|Sí (a partir de SQL Server 2019)|||||Sí (a partir de SQL Server 2019)|  
|Modo de almacenamiento en memoria|Sí|Sí|||||Sí|  
|Modo DirectQuery|Sí|Sí (a partir de SQL Server 2019)|||||Sí|  

## <a name="multidimensional-models"></a>Modelos multidimensionales 
  
|Característica|Enterprise|Estándar|Web|Express con Advanced Services|Express con herramientas|Express|Desarrollador|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Medidas de suma parcial|Sí|No <sup>1</sup>|||||Sí|  
|Jerarquías|Sí|Sí|||||Sí|  
|KPI|Sí|Sí|||||Sí|  
|perspectivas|Sí||||||Sí|  
|Acciones|Sí|Sí|||||Sí|  
|Inteligencia de cuentas|Sí|Sí|||||Sí|  
|Inteligencia de tiempo|Sí|Sí|||||Sí|  
|Resúmenes personalizados|Sí|Sí|||||Sí|  
|Reescritura de cubos|Sí|Sí|||||Sí|  
|Reescritura de dimensiones|Sí||||||Sí|  
|Reescritura de celdas|Sí|Sí|||||Sí|  
|Obtención de detalles|Sí|Sí|||||Sí|  
|Tipos de jerarquías avanzadas (jerarquías primarios-secundarios y jerarquías desiguales)|Sí|Sí|||||Sí|  
|Dimensiones avanzadas (dimensiones de referencia, dimensiones de varios a varios)|Sí|Sí|||||Sí|  
|Medidas y dimensiones vinculadas|Sí|Sí  <sup>2</sup> |||||Sí|  
|Translations|Sí|Sí|||||Sí|  
|Agregaciones|Sí|Sí|||||Sí|  
|Varias particiones|Sí|Sí, hasta 3|||||Sí|  
|Almacenamiento en caché automático|Sí||||||Sí|  
|Ensamblados personalizados (procedimientos almacenados)|Sí|Sí|||||Sí|  
|Consultas MDX y scripts|Sí|Sí|||||Sí|  
|Consultas DAX|Sí|Sí|||||Sí|  
|Modelo de seguridad basada en roles|Sí|Sí|||||Sí|  
|Seguridad de dimensión y de nivel de celda|Sí|Sí|||||Sí|  
|Almacenamiento escalable de cadena|Sí|Sí|||||Sí|  
|Modelos de almacenamiento MOLAP, ROLAP y HOLAP|Sí|Sí|||||Sí|  
|Transporte XML comprimido y binario|Sí|Sí|||||Sí|  
|Procesamiento de modo de inserción|Sí||||||Sí|  
|Expresiones de medida|Sí||||||Sí|  
  
 <sup>1</sup> La medida de suma parcial LastChild se admite en una edición estándar, a diferencia de otras medidas de suma parcial, como None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren y ByAccount. En todas las ediciones se admiten medidas de suma, como Sum, Count, Min y Max, y medidas de no suma (DistinctCount).  
  <sup>2</sup> La edición estándar admite la vinculación de medidas y dimensiones dentro de la misma base de datos, pero no de otras bases de datos o instancias.
  
## <a name="power-pivot-for-sharepoint"></a>PowerPivot para SharePoint  
  
|Característica|Enterprise|Estándar|Web|Express con Advanced Services|Express con herramientas|Express|Desarrollador|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Integración de la granja de servidores de SharePoint según la arquitectura del servicio|Sí||||||Sí|  
|Informes de uso|Sí||||||Sí|  
|Reglas de seguimiento de estado|Sí||||||Sí|  
|Galería de PowerPivot|Sí||||||Sí|  
|Actualización de datos de PowerPivot|Sí||||||Sí|  
|Fuentes de distribución de datos de PowerPivot|Sí||||||Sí|  
  
## <a name="data-mining"></a>Minería de datos  
  
|Nombre de la característica|Enterprise|Estándar|Web|Express con Advanced Services|Express con herramientas|Express|Desarrollador|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Algoritmos estándar|Sí|Sí|||||Sí|  
|Herramientas de minería de datos (asistentes, editores y generadores de consultas)|Sí|Sí|||||Sí|  
|Validación cruzada|Sí||||||Sí|  
|Modelos de subconjuntos filtrados de datos de estructura de minería de datos|Sí||||||Sí|  
|Series temporales: Mezcla personalizada entre métodos ARTXP y ARIMA|Sí||||||Sí|  
|Series temporales: Predicción con nuevos datos|Sí||||||Sí|  
|Consultas de minería de datos simultáneas ilimitadas|Sí||||||Sí|  
|Configuración avanzada y opciones de optimización de algoritmos de minería de datos|Sí||||||Sí|  
|Compatibilidad con algoritmos de complemento|Sí||||||Sí|  
|Procesamiento de modelos en paralelo|Sí||||||Sí|  
|Series temporales: predicción de series cruzadas|Sí||||||Sí|  
|Atributos ilimitados para reglas de asociación|Sí||||||Sí|  
|Predicción de secuencias|Sí||||||Sí|  
|Varios destinos de predicción para Bayes naive, red neuronal y regresión logística|Sí||||||Sí|  
  


