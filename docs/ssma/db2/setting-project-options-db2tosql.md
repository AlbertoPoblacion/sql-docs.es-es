---
title: Establecer las opciones de proyecto (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f325a606-97ac-48bc-b344-b55f5e086a48
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 16bf79c185a23399d48d141b5d773e2e0d41dc3f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "63269985"
---
# <a name="setting-project-options-db2tosql"></a>Establecer las opciones de proyecto (DB2ToSQL)
Puede establecer opciones de nivel de proyecto para cada proyecto SSMA. Estas opciones especifican la conversión de objetos, la carga del objeto, la configuración de migración de datos y la interfaz de usuario. Antes de convertir los objetos a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o migrar los datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], compruebe que las opciones de configuración son adecuadas para el proyecto.  
  
SSMA le permite configurar las opciones predeterminadas para todos los proyectos. Estas opciones se aplican a cualquier nuevo proyecto que cree. A continuación, puede personalizar las opciones para cada proyecto.  
  
## <a name="configuration-options-and-modes"></a>Los modos y opciones de configuración  
SSMA tiene cinco conjuntos de configuración del proyecto:  
  
-   Información del proyecto  
  
-   General (conversión, migración, la carga de objetos)  
  
-   Synchronization  
  
-   GUI  
  
-   Asignación de tipos  
  
También tiene cuatro modos para configurar estas opciones:  
  
-   Default  
  
-   Optimistic  
  
-   Completo  
  
-   Personalizado  
  
Se recomienda el modo predeterminado para la mayoría de los usuarios. El modo optimista mantiene más de la sintaxis de DB2 actual y es más fácil de leer. Sin embargo, mantener la sintaxis actual podría no ser precisa. Si se debe convertir la sintaxis de DB2 a equivalente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sintaxis, el modo completo realiza la conversión más completa, pero el código resultante podría ser más difícil de leer. En el modo personalizado, establezca las opciones.  
  
Para obtener más información sobre la configuración y cómo se aplica la configuración en cada modo, consulte los temas siguientes:  
  
-   [Configuración del proyecto &#40;conversión&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [Configuración del proyecto &#40;migración&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [Configuración del proyecto&#40;sincronización&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [Configuración del proyecto &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [Configuración del proyecto &#40;asignación de tipos de&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
## <a name="setting-project-options"></a>Configuración de opciones de proyecto  
En SSMA, puede configurar la configuración predeterminada para todos los proyectos. Estos valores se guardan en el archivo de configuración de SSMA y se aplican a cualquier nuevo proyecto que cree.  
  
**Para especificar las opciones de proyecto predeterminadas**  
  
1.  En el **herramientas** menú, haga clic en **configuración de proyecto predeterminada**.  
  
2.  En el **configuración de proyecto predeterminada** cuadro de diálogo, use uno de los siguientes procedimientos:  
  
    -   Seleccione el tipo de proyecto de migración para los que es necesaria para ver o cambiar de configuración **versión de destino de migración** desplegable clic **General** en la parte inferior del panel izquierdo y, a continuación, seleccione conversión o Migración.  
  
    -   Para seleccionar un modo predefinido, en el **modo** cuadro de lista desplegable, seleccione **predeterminado**, **Optimistic**, o **completa**.  
  
    -   Para especificar una configuración personalizada, seleccione o escriba la nueva configuración o valores.  
  
3.  Haga clic en **Aceptar** para guardar la configuración.  
  
También puede personalizar la configuración del proyecto actual. Esta configuración se guarda en el archivo de proyecto actual.  
  
**Para personalizar la configuración para el proyecto actual**  
  
1.  En el **herramientas** menú, haga clic en **configuración del proyecto**.  
  
2.  En el **configuración del proyecto** cuadro de diálogo, use uno de los siguientes procedimientos:  
  
    -   Para seleccionar un modo predefinido, en el **modo** cuadro de lista desplegable, seleccione **predeterminado**, **Optimistic**, o **completa**.  
  
    -   Para especificar un modo personalizado, en el **modo** cuadro, seleccione **personalizado**y, a continuación, seleccione la configuración de proyecto adecuada.  
  
3.  Haga clic en **Aceptar** para guardar la configuración.  
  
## <a name="next-steps"></a>Pasos siguientes  
El siguiente paso en la migración depende de las necesidades del proyecto:  
  
-   Para personalizar la asignación de tipos de datos de origen y destino, vea [asignación DB2 y tipos de datos de SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   En caso contrario, puede convertir las definiciones de objeto de base de datos de DB2 en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiciones de objetos. Para obtener más información, consulte [convertir esquemas de DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Vea también  
[Asignación de tipos de datos SQL Server y de DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
