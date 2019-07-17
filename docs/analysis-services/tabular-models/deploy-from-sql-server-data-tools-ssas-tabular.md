---
title: Implementar modelos tabulares de Analysis Services de SQL Server Data Tools | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 09d859cf8b5c372b9588266b9210837012396ea6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162868"
---
# <a name="deploy-from-sql-server-data-tools"></a>Implementar con SQL Server Data Tools
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Use las tareas de este tema para implementar una solución de modelo tabular mediante el comando implementar en SSDT.  
  
##  <a name="bkmk_deploy"></a> Configurar las propiedades Opciones de implementación y Servidor de implementación  
 Antes de implementar la solución de modelo tabular, primero debe especificar las propiedades Opciones de implementación y Servidor de implementación. Para obtener más información acerca de las propiedades de implementación y configuración, consulte [implementación de la solución de modelo Tabular](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
#### <a name="to-configure-options-and-properties"></a>Para configurar las opciones y propiedades  
  
1.  En SSDT, en **el Explorador de soluciones**, haga clic en el nombre del proyecto y, a continuación, haga clic en **propiedades**.  
  
2.  En el  **\<nombre del proyecto > propiedades** cuadro de diálogo, en **opciones de implementación**, especificar valores de propiedades si difiere de la configuración predeterminada.  
  
    > [!NOTE]  
    >  Para los modelos en modo de almacenamiento en caché, el **Modo de consulta** siempre es **In-Memory**.  
  
    > [!NOTE]  
    >  No puede especificar la **Configuración de suplantación** de los modelos que se encuentran en modo DirectQuery.  
  
3.  En **Servidor de implementación**, especifique la configuración de las propiedades **Servidor** (nombre), **Edición**, **Base de datos** (nombre) y **Nombre del cubo** si difiere de la predeterminada y, después, haga clic en **Aceptar**.  
  
> [!NOTE]  
>  También puede especificar el valor de la propiedad Servidor de implementación predeterminado de modo que los proyectos que se creen se implementen automáticamente en el servidor especificado. Para obtener más información, consulte [configurar propiedades de implementación y modelado de datos predeterminada](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
##  <a name="bkmk_deploy_proc"></a> Implementar un modelo tabular  
  
#### <a name="to-deploy-a-tabular-model"></a>Para implementar un modelo tabular
  
-   En SSDT, en el **compilar** menú, haga clic en **implementar \<nombre del proyecto >** .  
  
     Aparecerá el cuadro de diálogo **Implementar** e indicará el estado de la implementación de los metadatos y del procesamiento (a menos que se haya establecido la propiedad Opción de procesamiento en No procesar) de cada tabla incluida en el modelo. Una vez completado el proceso de implementación, utilice SSMS para conectarse a la instancia de Analysis Services y comprobar que se ha creado el nuevo objeto de base de datos de modelo o un aplicación cliente de informes para conectarse al modelo implementado.  
  
##  <a name="bkmk_deploy_status"></a> Estado de la implementación  
 El cuadro de diálogo **Implementar** permite supervisar el progreso de una operación de implementación. Una operación de implementación también se puede detener.  
  
 **Estado**  
 Indica si la operación de implementación se realizó correctamente o no.  
  
 **Detalles**  
 Enumera los elementos de metadatos implementados y el estado de cada uno, y proporciona un mensaje sobre cualquier problema.  
  
 **Detener implementación**  
 Haga clic en esta opción para detener la operación de implementación. Esta opción resulta útil si la operación de implementación tarda demasiado o hay demasiados errores.  
  
## <a name="see-also"></a>Vea también  
 [Implementación de la solución de modelo tabular](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [Configurar las propiedades predeterminadas de modelado de datos y de implementación](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  
