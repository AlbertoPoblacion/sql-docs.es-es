---
title: KPI en los modelos tabulares de Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2f6714d61ce53b251a6511aaf78c803213e19860
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207636"
---
# <a name="kpis"></a>KPI
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Un *KPI* (indicador clave de rendimiento) de un modelo tabular se usa para medir el rendimiento de un valor, definido por una medida *base* , con respecto a un valor de *destino* , que también se define con una medida o un valor absoluto. Este artículo proporciona a los autores de modelos tabulares una descripción básica de los KPI en un modelo tabular.  
  
##  <a name="bkmk_benefits"></a> Ventajas  
 En la terminología empresarial, un indicador clave de rendimiento (KPI) es una medida cuantificable para valorar los objetivos empresariales. Un KPI se evalúa con frecuencia a lo largo del tiempo. Por ejemplo, el departamento de ventas de una organización puede usar un KPI para medir el beneficio bruto mensual frente al beneficio bruto previsto. El departamento de contabilidad puede medir los gastos mensuales frente a los ingresos para evaluar los costos y un departamento de recursos humanos puede medir la rotación trimestral de los empleados. Cada uno de ellos es un ejemplo de KPI. Los profesionales de una empresa suelen usar KPI agrupados en un cuadro de mandos empresarial para obtener un resumen histórico rápido y preciso de los éxitos empresariales o para identificar tendencias.  
  
 Un KPI de un modelo tabular incluye:  
  
 **Valor base**  
 Un valor base está definido por una medida que se resuelve como un valor. Este valor, por ejemplo, puede ser un agregado de las ventas reales o una medida calculada como los beneficios para un período determinado.  
  
 **Valor de destino**  
 Un valor de destino está definido por una medida que se resuelve como un valor o por un valor absoluto. Por ejemplo, un valor de destino podría ser la cantidad en la que los responsables de una organización desean incrementar las ventas o los beneficios.  
  
 **Umbrales de estado**  
 Un umbral de estado se define mediante el intervalo entre un umbral inferior y uno superior o mediante un valor fijo. El umbral de estado muestra un gráfico que ayuda a los usuarios a determinar fácilmente el estado del valor base en comparación con el valor de destino.  
  
##  <a name="bkmk_example"></a> Ejemplo  
 La directora de ventas de Adventure Works desea crear una tabla dinámica que pueda usar para ver rápidamente si los empleados de ventas están cumpliendo o no sus cuotas de ventas durante un periodo determinado (un año). Para cada empleado de ventas, desea que la tabla dinámica para mostrar una presentación gráfica simple que muestra el estado de cada empleado de ventas es si o no a continuación, en o por encima de su cuota de ventas, el importe de cuota de ventas en dólares y el importe de ventas real en dólares. Desea poder segmentar los datos por año.  
  
 Para ello, la directora de ventas se da de alta la Ayuda del programador de soluciones de BI de su organización para agregar un KPI de ventas al modelo Tabular AdventureWorks. La directora de ventas, a continuación, usará Excel para conectar con el modelo Tabular de Adventure Works como origen de datos y crear una tabla dinámica con los campos (medidas y KPI) y segmentaciones de datos para analizar si el equipo de ventas cumple sus cuotas.  
  
 En el modelo, se crea una medida en la columna SalesAmount de la tabla FactResellerSales, que indica el importe de ventas real en dólares para cada empleado de ventas. Esta medida definirá el valor base del KPI.  
  
 La medida Sales se crea con la fórmula siguiente:  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 La columna SalesAmountQuota de la tabla FactSalesQuota tiene definida una cuota de importe de ventas para cada empleado. Los valores de esta columna servirán como medida (valor) de destino del KPI.  
  
 La medida SalesAmountQuota se crea con la fórmula siguiente:  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  Existe una relación entre la columna EmployeeKey de la tabla FactSalesQuota y la columna EmployeeKey de la tabla DimEmployees. Esta relación es necesaria para que cada empleado de ventas de la tabla DimEmployee esté representado en la tabla FactSalesQuota.  
  
 Ahora que se han creado medidas que sirven como valor base y como valor de destino del KPI, se extiende la medida Sales a un nuevo KPI Sales. En el KPI Sales, la medida de destino SalesAmountQuota se define como el valor de destino. El umbral de estado se define como un rango por porcentaje, cuyo destino es el 100%, lo que significa que las ventas reales definidas por la medida Sales cumplen la cuota definida en la medida de destino SalesAmoutnQuota. Los porcentajes Mínimo y Máximo se definen en la barra de estado y se selecciona un tipo de gráfico.  
  
 La directora de ventas ahora puede crear una tabla dinámica agregando valor Base del KPI, valor de destino y estado para el campo de valores. La columna Employees se agrega al campo RowLabel y la columna CalendarYear se agrega como segmentación de datos.  
  
 Ahora, la directora de ventas puede segmentar por año el importe de ventas real, la cuota de ventas y el estado de cada empleado de ventas. Puede analizar las tendencias de ventas a lo largo de los años para determinar si necesita ajustar o no la cuota de ventas para un empleado.  
  
##  <a name="bkmk_create"></a> Create and edit KPIs  
 Para crear KPI, en el diseñador de modelos, usará el cuadro de diálogo Indicador clave de rendimiento. Puesto que los KPI deben asociarse a una medida, para crear un KPI se extiende una medida que se evalúa como un valor base; a continuación, se crea una medida que se evalúa como un valor de destino o especificando un valor absoluto. Después de definir la medida base (valor) y el valor de destino, podrá definir los parámetros del umbral de estado entre el valor base y el valor de destino. El estado se muestra en un formato gráfico mediante iconos, barras, gráficos o colores seleccionables. El valor base y el valor de destino, junto con el estado se pueden agregar a un informe o una tabla dinámica como valores que se pueden segmentar con respecto a otros campos de datos.  
  
 Para ver el cuadro de diálogo Indicador clave de rendimiento, en la cuadrícula de medida de la tabla, haga clic con el botón secundario en la medida que servirá como valor base y, a continuación, haga clic en **Crear KPI**. Después de extender una medida a un KPI como valor base, aparecerá un icono junto al nombre de la medida en la cuadrícula de medidas que identifica la medida como asociada a un KPI.  
  
##  <a name="bkmk_related_tasks"></a> Tareas relacionadas  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Crear y administrar KPI](../../analysis-services/tabular-models/create-and-manage-kpis-ssas-tabular.md)|Describe cómo crear un KPI con una medida base, una medida de destino y umbrales de estado.|  
  
## <a name="see-also"></a>Vea también  
 [medidas](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [Perspectivas](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  
